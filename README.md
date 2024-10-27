# Zip and Upload Automation Script

This script creates a symbolic link to a specified directory, compresses it into a zip file, and uploads the zip file to a target server for processing. This automation is useful for quickly zipping files and performing file upload operations on specific target servers.

### Prerequisites

- `curl`: This script uses `curl` to upload and retrieve data from the target server.
- `zip`: This script uses `zip` to package files.

### Usage

To run the script:

```bash
./script.sh [DIRECTORY_PATH]
```

- **[DIRECTORY_PATH]**: The directory you want to create a symbolic link to, which will be added to a zip file for uploading.

### Script Workflow

1. **Target Configuration**: The script sets the target server to `zipping.htb`.
2. **Directory Parameter**: Accepts a directory path as an argument for the symbolic link.
3. **Cleanup**: Removes any existing `test.pdf` and `test.zip` files to prevent conflicts.
4. **Symbolic Link and Zip Creation**:
   - Creates a symbolic link (`test.pdf`) to the specified directory.
   - Compresses the symbolic link into `test.zip`.
5. **File Upload**:
   - Uploads `test.zip` to the target server (`zipping.htb`) via a POST request using `curl`.
   - Uses a specific PHP session ID for authentication or session persistence.
6. **Extract and Display Result**:
   - Parses the server’s response to obtain the file URL for the uploaded file.
   - Uses `curl` again to retrieve and display the file contents.

### Example

```bash
./script.sh /path/to/directory
```

This command will create `test.pdf` as a symbolic link to `/path/to/directory`, zip it into `test.zip`, and upload it to `http://zipping.htb/upload.php`.

### Notes

- Update the `PHPSESSID` in the script to a valid session ID for access.
- Ensure permissions and access rights are granted for the specified directory and the target server.
- Test in a controlled environment, as this script performs file uploads which may have security implications.

### Troubleshooting

- **Permission Denied**: Ensure the directory specified in `[DIRECTORY_PATH]` is accessible.
- **Session Expiry**: If receiving `403 Forbidden` or similar errors, check if the `PHPSESSID` is still valid.
