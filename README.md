# Join

Join is a web-based Kanban tool for structured task management. The application covers a complete workflow from authentication to task creation, editing, and status changes, combining board management, contact handling, task creation, and a dashboard view within a consistent multi-page architecture.

What makes the project technically interesting is the deliberate decision to build it without a frontend framework. State handling, rendering, form logic, overlays, navigation, and data persistence are implemented with HTML, CSS, and Vanilla JavaScript. That makes the architectural work behind the application much more visible and shows how much structure even a relatively compact frontend needs when no framework abstracts the hard parts away.

## Project Overview

Join is designed for teams or individual users who want to manage work in a clear Kanban workflow. The application includes:

- login and signup flows with guest access
- a summary page with key metrics and upcoming deadlines
- a Kanban board with the statuses To do, In progress, Await feedback, and Done
- task creation with priority, category, due date, assignments, and subtasks
- detailed task views and editing capabilities
- contact management as the basis for task assignments
- responsive behavior for desktop and mobile usage

## Strengths of the Project

### 1. Strong functional scope

Join is more than a static task board. The project covers the core areas expected from a usable task management product: authentication, persistence, board interaction, contact management, task details, subtasks, and overview metrics. That gives it the character of a coherent product rather than an isolated UI exercise.

### 2. Consistent implementation with Vanilla JavaScript

The application does not rely on framework abstractions. Page logic, DOM updates, form validation, drag and drop behavior, and template composition are handled directly in the browser. This makes the codebase easier to evaluate from an engineering perspective and demonstrates solid understanding of browser APIs, client-side state handling, and reusable UI patterns without React, Vue, or Angular.

### 3. Clear separation of responsibilities

For a learning and portfolio project, the structure is notably clean. Board logic, task overlays, templates, contacts, authentication, summary logic, and shared utilities are separated into dedicated files. Header and sidebar are also extracted into reusable HTML templates. This reduces duplication and provides a maintainable foundation for a multi-page frontend.

### 4. Pragmatic data strategy

Data is loaded from Firebase and additionally cached in session storage. This combination reduces unnecessary network requests and keeps the interface responsive. For a project of this size, it is a practical balance between simplicity and performance.

### 5. Good coverage of real UX requirements

Join includes several details that are often missing from smaller training projects:

- live board search
- visual progress tracking through subtasks
- direct task creation from the board
- detail and edit overlays
- custom form validation instead of default browser behavior
- separate mobile interaction paths for contacts and board usage

These aspects show that the project was not only designed visually, but also thought through in terms of real usage scenarios.

## Technical Challenges

The real value of the project lies not only in the feature set, but in the problems that had to be solved to make those features work together.

### 1. State management without a framework

Because no central UI framework is used, application state has to be managed manually. Tasks, contacts, and user information are loaded, cached locally, updated, and rendered again when the state changes. This is especially relevant for board filtering, task movement, detail views, subtask progress, and the integration of the currently logged-in user into the contact logic.

### 2. Data consistency between Firebase and session storage

Join works with a combination of an external data source and a local cache. That is practical, but it also increases complexity: changes need to be reflected in the active client state without leaving stale data in the interface. Even in a compact application, that kind of synchronization is a real architectural concern.

### 3. Multi-page architecture with shared UI building blocks

The project is not a single-page application. Its functionality is distributed across multiple HTML pages while navigation, layout, and shared behavior still need to remain consistent. The use of shared templates and initialization logic is therefore a central technical part of the implementation.

### 4. Interactive board behavior

A Kanban board may look straightforward, but the interaction model is not trivial. Tasks need to be grouped by status, filtered, moved via drag and drop, and re-rendered correctly afterwards. On top of that, the board has to account for empty columns, search results, priorities, assigned contacts, and progress derived from subtasks.

### 5. Responsive behavior across different usage patterns

The application is not only meant to scale visually, but to remain usable across device types. Board views, overlays, and contact screens require different interaction patterns on mobile than on desktop. The presence of dedicated CSS files and mobile-specific scripts shows that responsiveness was treated as a functional concern, not just a visual one.

## Technology Stack

- HTML5
- CSS3
- Vanilla JavaScript
- Firebase Realtime Database
- Session Storage for client-side caching
- modular HTML templates for shared layout sections

## Architecture Summary

The application is structured as a multi-page frontend.

- index.html is the entry point for login and signup
- the html directory contains the main feature pages for summary, board, add task, contacts, and static content pages
- shared layout sections are injected through assets/templates/header.html and assets/templates/sidebar.html
- business logic is organized into topic-specific JavaScript files inside the scripts directory
- data handling is centralized in scripts/dataStore.js, while Firebase communication is handled in scripts/firebase.js

## Local Setup

Because this is a classic frontend project with multiple HTML pages and relative asset paths, Join should be started through a local web server rather than by opening the HTML files directly via file access.

A typical setup looks like this:

```bash
git clone <repository-url>
cd join
```

After that, the project can be started with a local server extension or any simple static server.

Important: the application connects directly to Firebase. For full functionality, the configured database needs to be reachable and set up correctly.

## Assessment

Join stands out as a practical project because it is not just a collection of individual screens, but a connected application system. The combination of multi-page structure, reusable templates, board interaction, form logic, contact management, and external data persistence makes it significantly more demanding than a basic CRUD demo.

The decision to solve many of these problems without a framework is a clear strength. It makes the architecture more visible, requires cleaner structure, and shows that the core mechanisms behind modern frontend applications are understood and implemented directly rather than delegated to a library.
