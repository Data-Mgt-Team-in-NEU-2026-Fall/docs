# Seattle Neighborhood Book-Sharing System

## 1. ER Entity List

| Entity | Description | Example |
| --- | --- | --- |
| User | A local resident or university student. | Ballard resident Lisa Park and UW student Leo Wang. |
| Book Category | A classification dictionary for browsing shared books. | Fiction, science, history, children's books. |
| Book | Details for a shared circulating book. | *The Three-Body Problem*, *Sapiens*, or *Operating System Concepts*. |
| Shared Bookshelf | A neighborhood location for storing and exchanging books. | Ballard Community Library or a Capitol Hill apartment lobby. |
| Borrowing Record | A record covering the borrowing request through return. | Leo borrows *The Three-Body Problem* for 30 days. |
| Donation Record | A record of a user's donated book. | Lisa donates *Sapiens* to the Ballard bookshelf. |
| Book Tag | An attribute used for precise search and recommendations. | Like new, English original, commuter-friendly. |
| Reservation | A waitlist record for an unavailable book. | Lily is second in line for *Operating System Concepts*. |
| Book Review | A user's reading reflection and rating. | Leo posts a five-star review of *The Three-Body Problem*. |
| Site Administrator | A volunteer responsible for a shared bookshelf. | Emma organizes books and verifies lending activity. |

## 2. Core Business Scenarios

### Residents

- Search books by category and tags and submit borrowing requests.
- Donate books and review personal borrowing and donation history.
- Join waitlists and post reviews after returning books.

### Site Administrators

- Maintain bookshelves, shelve books, and update book status.
- Verify borrowing and returns and manage waitlists.
- Review circulation rates and borrowing volume.
