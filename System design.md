# MyLibrary – Comprehensive System Design

> A personal digital library system for cataloging books, tracking borrowers, managing metadata, and writing notes or reviews — with support for regional languages like Kannada (ಕನ್ನಡ).

---

## Overview

**Purpose**  
To create a lightweight, extensible personal library app that allows users to:

- Add, view, and manage books
- Track borrowing activity
- Maintain a repository of authors and genres
- Add notes and reviews to individual books
- Support multilingual input, especially Kannada
- Provide a responsive, user-friendly interface

---

## Key Features

- Add/Edit/Delete Books
- Book detail view with notes/reviews
- Search, filter, sort functionality
- Borrower tracking (who borrowed what and when)
- Metadata management (Authors, Genres)
- Notes/Review system per book
- Full Kannada support (UTF-8 input, rendering, optional UI)
- Responsive web design
- Modular, extensible codebase
- LocalStorage (Phase 1) with optional backend (later phase)

---

## System Architecture

A frontend-centric app (initially) with optional cloud backend support in later phases.

### Stack

| Layer        | Tech                                  |
|--------------|---------------------------------------|
| Frontend     | React + TypeScript + Tailwind CSS     |
| State Mgmt   | Zustand / React Context + LocalStorage|
| UI Framework | HTML5 + Tailwind                      |
| i18n         | Manual labels / optional i18next      |
| Fonts        | Noto Sans Kannada (for Kannada text)  |
| Hosting      | Vercel (GitHub-connected)             |
| Backend (opt)| Supabase / Firebase (future phase)    |

---

## Data Model

### Book
```
- id: UUID
- title: String
- authorId: UUID
- genreId: UUID
- year: Number
- description: String
- coverImage: URL
- notes: BookNote[]
- borrowHistory: BorrowHistory[]
```

### Author
```
- id: UUID
- name: String
- bio: String
```

### Genre
```
- id: UUID
- name: String
- description: String
```

### Borrower
```
- id: UUID
- name: String
- email: String
- phone: String
```
### BookNote
```
- id: UUID
- bookId: UUID
- content: String
- createdAt: Date
```
### BorrowHistory
```
- id: UUID
- bookId: UUID
- borrowerId: UUID
- borrowDate: Date
- returnDate: Date
```

---

## Entity Relationship Diagram (ERD)

![Entity Relationship Diagram (ERD)](https://github.com/sujaybn/personal_library/blob/main/UML%20diagrams/ERD.drawio.png)

---

## UML Class Diagram

![UML Class disgram](https://github.com/sujaybn/personal_library/blob/main/UML%20diagrams/library%20app%20class%20diagram.drawio.png)

---

## Use Case Diagram

![Use case diagram](https://github.com/sujaybn/personal_library/blob/main/use-case-diagram.drawio.png)

---

## Activity Diagram – Add Book

![Activity diagram](https://github.com/sujaybn/personal_library/blob/main/UML%20diagrams/Activity%20diagram.drawio.png)

---

## UI & Navigation Structure

### Main Routes
| Route           | Description                     |
|------------------|----------------------------------|
| `/`              | Dashboard / Book list            |
| `/books/:id`     | Book detail (with notes/borrow)  |
| `/books/add`     | Add new book                     |
| `/metadata`      | Manage authors & genres          |
| `/borrowers`     | View/edit borrower profiles      |

---

### UI Components
- **Header** – App name, search, add button
- **BookCard** – Display for each book
- **BookForm** – Modal/page to add/edit book
- **BookDetail** – Detailed view with notes/borrow history
- **MetadataManager** – Author/genre management
- **BorrowerManager** – View/edit borrowers
- **NoteComponent** – Add/edit/delete notes per book

---

## Kannada & Multilingual Support

- All input fields support UTF-8 and Kannada (e.g., "ಮಾಲ್ಗುಡಿ ಡೇಸ್")
- Optional font: `Noto Sans Kannada` (loaded via Google Fonts)
- Notes and reviews can be written in any language
- Future expansion: `react-i18next` for full UI translation
- `lang="kn"` can be added for screen reader semantics

---

## UX Flows

### Book Management Flow
1. Open app → Book grid/list
2. Click "Add Book"
3. Enter title, author, genre, etc.
4. Click Save → New book appears in list

### Borrower Flow
1. Open Book Detail
2. Click "Mark as Borrowed"
3. Select existing or add new borrower
4. Save → Borrow history updated

### Review/Note Flow
1. Open Book Detail
2. Add review/note in free-form text area
3. Saved as timestamped log under that book

---

## State Design & Persistence

- React state + Zustand or Context for reactive updates
- `localStorage` for persistence
- IndexedDB (optional) for larger datasets
- Optional future backend (Supabase)

---

---

## Deployment

- Deploy via **Vercel**
- Connect with GitHub
- Auto CI/CD on push
- Environment configurable for Supabase if used later

---

## Summary

| Area                | Status |
|---------------------|--------|
| Feature Design      | [DONE] |
| Data Models         | [DONE] |
| UML/ERD Diagrams    | [DONE] |
| Tech Stack          | [DONE] |
| Kannada Support     | [DONE] |
| Architecture Plan   | [DONE] |
| UI Navigation Flow  | [DONE] |

---

## Next Step: Development Breakdown

Move on to:
- Phased development plan
- MVP definition
- Task allocation per milestone

_See `DEVELOPMENT_PLAN.md` for implementation roadmap._

