---
aliases:
  - Obsidian Base
---
# Obsidian Bases

Obsidian Bases is a core plugin that brings database-like functionality to your Obsidian vault. It allows you to organize, view, and manage your notes by treating them as items in a database, complete with editable properties and different layouts.

## Key Features

*   **Database Views:** Create views of your notes as tables or cards.
*   **Properties as Fields:** Bases uses your notes' YAML frontmatter (properties) as the fields for the database.
*   **Filtering and Sorting:** You can filter and sort your notes based on their properties.
*   **In-place Editing:** Edit note properties directly from the base view.
*   **Local Data:** All data is stored in your local Markdown files, so you're not locked into a proprietary format.
*   **Embeddable:** You can embed your bases into other notes.

## How to Use Obsidian Bases

1.  **Enable the Plugin:** Go to `Settings` > `Core Plugins` and enable "Bases".
2.  **Create a Base:** Open the command palette (`Ctrl/Cmd + P`) and run the command "Bases: Create new base".
3.  **Configure the Base:** You can then configure the base by choosing which notes to include (e.g., by folder or tag), which properties to display, and how to sort and filter them.

## Bases vs. Dataview

Bases is similar to the popular `Dataview` community plugin, but with a few key differences:

*   **No Code Required:** Bases provides a graphical interface for creating your views, whereas Dataview relies on a query language.
*   **Focus on Properties:** Bases primarily works with the properties in your notes' frontmatter. Dataview can query both frontmatter and the content of your notes.
*   **Performance:** Bases is generally faster than Dataview because it doesn't need to parse the full content of your notes.

Bases is a great option if you want a simple, user-friendly way to create database-like views of your notes without writing any code. Dataview is more powerful and flexible if you need to create complex queries that involve the content of your notes.

## Functions in Bases

Bases includes functions that can be used within filters and formulas to manipulate your data. This allows for more advanced and dynamic views.

Some examples of functions include:

*   `list()`: Treats a property value as a list of items.
*   `format()`: Formats dates and other data.
*   **Formulas:** You can create calculated fields that update dynamically based on other properties.

## Popular Use Cases

People are using Obsidian Bases for a wide variety of organizational tasks, including:

*   **Project Management:** Tracking tasks, projects, and their statuses.
*   **Content Creation:** Managing a content calendar, tracking ideas, and monitoring progress.
*   **Reading Lists:** Organizing books, articles, and other materials you want to read.
*   **Meeting Notes:** Keeping track of meetings, attendees, and action items.
*   **Personal Knowledge Management (PKM):** Structuring and connecting ideas and information.
*   **Academic Research:** Managing literature reviews, research notes, and citations.
