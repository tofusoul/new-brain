
# Using rclone with Google Drive

This note summarizes the correct way to use `rclone` to interact with your Google Drive, specifically how to differentiate between "My Drive" and "Shared Drives".

## Key Concepts

*   **Remote Configuration is Key:** The most important concept is that the distinction between "My Drive" and a "Shared Drive" is made during the `rclone config` process when you set up a new remote.
*   **"My Drive" Remote:** To create a remote for your personal "My Drive", you answer "n" (No) when asked "Configure this as a Shared Drive (Team Drive)?".
*   **"Shared Drive" Remote:** To create a remote for a specific "Shared Drive", you answer "y" (Yes) to the same question and then select the desired drive from a list. You must create a separate remote for each Shared Drive you want to access.

## Listing Files

Once the remotes are configured, the commands to list files are the same. The output will depend on how the remote was configured.

*   **List contents of a remote:**
    ```bash
    rclone lsd <remote_name>:
    ```
*   **List contents of a specific folder:**
    ```bash
    rclone lsd <remote_name>:/path/to/folder
    ```

## Accessing Files "Shared with me"

To access files that have been shared with you but are not in your "My Drive" or a "Shared Drive", you use the `--drive-shared-with-me` flag with a remote configured for your "My Drive".

*   **List items shared with you:**
    ```bash
    rclone lsd <my_drive_remote_name>: --drive-shared-with-me
    ```
