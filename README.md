# JOIN

## Overview

**Join** is a web-based Kanban task management application developed as part of a Front-End Development training project. It is built as a **multi-page application with Vanilla JavaScript, HTML, and CSS** and focuses on structuring team workflows through a clear board system, task management features, contact handling, and dashboard-style summaries.

The technical value of the project lies in the fact that it was implemented **without a frontend framework**. Core application concerns such as rendering, state handling, overlays, form workflows, navigation, and data synchronization are solved directly in the browser. This makes Join a strong demonstration of fundamental frontend engineering, architectural thinking, and maintainable JavaScript organization.

### Live Demo

- **Link:** [View Live Project](https://stefanstraeter.github.io/join/)

---

## Technical Architecture: Multi-Page Vanilla JavaScript Application

A central strength of this project is the way application logic is structured across multiple pages while still maintaining consistent behavior, shared layout sections, and reusable logic.

### Key Architectural Highlights:

- **Framework-Free State Handling:** Tasks, contacts, and user-related data are loaded, cached, updated, and rendered without React, Vue, or any other UI abstraction.
- **Shared Layout Composition:** Header and sidebar are injected as reusable HTML templates, allowing the application to maintain a unified layout across multiple pages.
- **Pragmatic Data Layer:** Firebase Realtime Database is combined with `sessionStorage` caching to reduce redundant requests and improve perceived responsiveness.
- **Modular Responsibility Split:** Board logic, authentication, task overlays, templates, contact management, and utility logic are separated into focused script files.

### Project Structure

- **`index.html`**: Entry point for authentication, including login, signup, and guest access.
- **`html/`**: Main feature pages such as Summary, Board, Add Task, Contacts, Help, Legal Notice, and Privacy Policy.
- **`scripts/`**: Application logic split by domain, including authentication, board behavior, task creation, task detail overlays, contacts, and shared utilities.
- **`assets/templates/`**: Reusable layout fragments such as the header and sidebar.
- **`styles/`**: Base styles, layout components, feature-specific styles, and responsive adjustments.

---

## Key Features & Implementation

### Structured Task Management

Join covers the full lifecycle of task organization, from creation to completion. Users can create tasks with categories, due dates, priorities, assigned contacts, and subtasks, then manage them through detailed overlays and editing workflows.

### Interactive Kanban Board

- **Status-Based Workflow:** Tasks are organized across the board columns To do, In progress, Await feedback, and Done.
- **Drag-and-Drop Interaction:** Cards can be moved between columns to reflect changing progress.
- **Search and Filtering:** The board supports live search to quickly find relevant tasks.
- **Visual Progress Tracking:** Subtask completion is reflected through progress indicators directly in the task cards.

### Contact-Centered Collaboration

The application includes a dedicated contacts area, allowing users to manage people separately from tasks and then assign them through the task workflow. This adds an extra layer of realism compared to simpler single-entity CRUD projects.

### Dashboard and Summary Logic

The summary page provides a compact overview of workload distribution, urgent items, and upcoming deadlines. This extends the project beyond a simple board UI and adds a reporting perspective to the application.

### Responsive UX Without Framework Tooling

- **Desktop and Mobile Support:** The layout adapts to different screen sizes across the board, forms, contacts, and overlay views.
- **Mobile-Specific Logic:** Parts of the contact handling and interaction behavior are adapted specifically for smaller devices.
- **Custom Form Handling:** Validation and interaction feedback are implemented manually instead of relying on default browser behavior.

---

## Technical Challenges

### State Management Across Multiple Pages

Because Join is not a single-page application, state and behavior have to remain coherent across separate HTML documents. This requires careful initialization logic and a clean split between shared and page-specific functionality.

### Synchronizing Firebase with Client-Side Cache

The combination of Firebase as the remote data source and `sessionStorage` as a local cache introduces real synchronization concerns. Changes must be reflected reliably in the current session without causing stale or inconsistent UI output.

### Maintaining Reusable Logic in a Framework-Free Setup

Without component systems or central state libraries, reusable behavior has to be designed manually. The project addresses this by separating templates, utility functions, and domain logic into dedicated files that remain understandable and maintainable.

### Building an Interactive Board UI from Scratch

The board involves more than visual layout. Tasks must be grouped correctly, moved between states, re-rendered on change, and displayed differently depending on assignments, progress, and search results. Implementing that behavior directly with DOM logic is one of the more demanding parts of the project.

---

## Getting Started

1. **Clone the repository:** `git clone <repository-url>`
2. **Open the project folder:** `cd join`
3. **Run the project through a local server:** for example with VS Code Live Server or another static development server.
4. **Ensure Firebase is reachable:** the application depends on a configured Firebase Realtime Database connection.

---

## Tech Stack

- **HTML5** for page structure
- **CSS3** for layout, components, and responsive behavior
- **Vanilla JavaScript** for application logic and interaction handling
- **Firebase Realtime Database** for persistent data storage
- **Session Storage** for client-side caching

---

## Author

**Stefan Straeter**

GitHub: [@stefanstraeter](https://github.com/stefanstraeter/)
