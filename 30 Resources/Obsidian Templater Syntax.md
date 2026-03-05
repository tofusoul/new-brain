# Obsidian Templater Syntax

The Templater plugin for Obsidian is a powerful tool for creating dynamic notes. It uses a specific syntax to insert variables, functions, and even execute JavaScript code.

## Basic Syntax

- **Expressions:** Templater commands are enclosed in `<%` and `%>`.
- **Date and Time:** The `tp.date.now()` function is used to insert the current date and time.
  - **Format:** You can specify the format using tokens. For example, `<% tp.date.now("YYYY-MM-DD") %>` will insert the date in ISO format.
  - **Offsets:** You can add or subtract time. For example, `<% tp.date.now("YYYY-MM-DD", 1) %>` will insert tomorrow's date.
- **File Title as Reference:** You can use the file title as a reference date for calculations.
  - `tp.file.title`:  This variable holds the title of the current file.
  - Example: `<% tp.date.now("YYYY-MM-DD", 1, tp.file.title, "YYYY-MM-DD") %>` will insert the day after the date in the file title.

## Advanced Usage

- **Variables and Functions:** Templater allows you to define and use variables and functions within your templates.
- **JavaScript Execution:** For complex scenarios, you can execute arbitrary JavaScript code within your templates. This allows for interaction with other plugins and advanced file manipulation.

## Common Date Format Tokens

| Token | Output |
| --- | --- |
| `YYYY` | 4-digit year (e.g., 2025) |
| `MM` | 2-digit month (e.g., 07) |
| `DD` | 2-digit day (e.g., 06) |
| `dddd` | Full day name (e.g., Sunday) |
| `MMMM` | Full month name (e.g., July) |
| `Do` | Day of the month with ordinal (e.g., 6th) |
