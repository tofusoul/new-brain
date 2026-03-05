# Plugin Usage Guide for Vault Organization

This guide documents the decision-making process and usage patterns for the plugins involved in the vault organization project.

## 1. Tool Selection

Two plugins were considered for programmatically moving notes: `obsidian-local-rest-api` and `obsidian-advanced-uri`.

-   **`obsidian-advanced-uri`**: Excellent for user-facing automation and simple, one-off commands via URI. However, it lacks a direct, reliable feedback mechanism for scripts, making it difficult to validate if an operation succeeded.
-   **`obsidian-local-rest-api`**: Provides a full REST API, which is perfect for scripting. It offers clear success/error codes and allows for robust validation. It can move notes and, critically, **updates backlinks automatically** as part of its move operation.

**Conclusion:** `obsidian-local-rest-api` is the selected tool for this migration due to its reliability, script-friendliness, and backlink-updating capabilities.

## 2. `obsidian-local-rest-api` Usage

-   **Authentication**: Requires a Bearer token in the `Authorization` header.
-   **Key Endpoint**: `PUT /vault/{path}`
    -   This endpoint is used to move a note.
    -   The `{path}` in the URL is the current, URL-encoded path of the note.
    -   The request body is a JSON object containing the `new_path` key.
    -   **Example `curl` command:**
        ```bash
        curl -X PUT "http://127.0.0.1:27123/vault/MyOldNote.md" \
          -H "Authorization: Bearer <API_KEY>" \
          -H "Content-Type: application/json" \
          -d '{"new_path": "20 Areas/MyNewNote.md"}'
        ```
-   **Success Condition**: A `204 No Content` status code indicates a successful move. Any other code indicates an error.
