# 类图 4：交易评价与举报

对应图：[4.jpeg](4.jpeg)。

## 设计主体思路

将交易后的评价与平台举报作为两条独立流程：评价围绕订单和交易双方展开，举报则针对商品或订单。两者各自用抽象父类保存通用信息，再通过互斥的子类表达具体类型。

## 对应的用户用例

| 用例 | 类图覆盖内容 |
| --- | --- |
| `UC-1102` 查看个人交易记录 | `TransactionReview` 及其子类记录用户撰写或收到的评价；个人其他交易记录由类图 1、2 补充。 |
| `UC-1501` 举报商品或交易 | `ItemReport` 和 `TransactionReport` 分别记录商品举报与交易举报及其提交者。 |
| `UC-4501` 评价交易对方 | `TransactionReview`、`BuyerReview`、`SellerReview` 和 `TransactionOrder` 表达订单双方及评价记录；完成订单后的资格和每方向最多一条评价仍需校验。 |
| `UC-5501` 处理举报与违规内容 | `Report` 的处理状态和两种举报目标支持记录审核对象及处理进度；管理员权限由类图 1 的 `UserRole` 提供基础，具体处置流程不在本类图中规定。 |

## 包含的实体

| 实体 | 作用 |
| --- | --- |
| `User` | 评价的撰写者与接收者，以及举报的提交者。 |
| `TransactionOrder` | 评价对应的交易，也是交易举报的目标。 |
| `SecondhandItem` | 商品举报的目标。 |
| `TransactionReview`（抽象类） | 保存评价 ID、日期、评分、评论与状态。 |
| `BuyerReview`、`SellerReview` | 分别表示针对买家和针对卖家的评价。 |
| `Report`（抽象类） | 保存举报 ID、原因、描述、日期与处理状态。 |
| `ItemReport`、`TransactionReport` | 分别表示商品举报和交易举报。 |

## 主要关系

- 每条 `TransactionReview` 由 1 名 `User` 撰写、由 1 名用户接收；用户可撰写或收到 0 到多条评价。
- 每笔 `TransactionOrder` 最多关联 1 条 `BuyerReview` 和 1 条 `SellerReview`；每条具体评价关联 1 笔订单。
- 每条 `Report` 由 1 名用户提交；用户可提交 0 到多条举报。
- 每条 `ItemReport` 针对 1 件 `SecondhandItem`，每条 `TransactionReport` 针对 1 笔 `TransactionOrder`；一件商品或一笔订单可分别收到 0 到多条相应举报。

## 特殊考量

- 两组继承均标注 `{complete, disjoint}`：每条评价必须且只能属于买家评价或卖家评价；每条举报必须且只能属于商品举报或交易举报。
- 图中的评价角色是**被评价者**的身份：`BuyerReview` 评价买家，`SellerReview` 评价卖家。写入时应校验撰写者与接收者是订单的相应交易双方，不能仅凭评价类型推断身份。
- 单笔订单每种评价最多一条；应在实现中约束重复评价，并明确取消或未完成订单是否允许评价。
- 举报与评价各有状态，便于审核和处理；处理结果不应直接改写原始举报内容或历史评价。
