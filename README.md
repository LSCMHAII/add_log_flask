# add_log_flask

This is a simple Flask application that provides an API endpoint to add log entries to a specified file. The application is designed to run in a Docker container and can be easily integrated into existing workflows for logging purposes.

## Features
- Add log entries to a specified file in a specified directory.
- Configurable base path for log storage via environment variables.

## API Endpoint

### POST /run
This endpoint accepts a JSON payload to specify the directory name, file name, and content to be added to the log file.
Content will be divided into lines by the newline character `\n` and each line will be added to the log file.

#### Request Body
```json
{
    "dir_name": "logs",
    "file_name": "log_20260228.txt",
    "content": "[20260228][INFO] Validate job complete without error."
}

{
    "dir_name": "logs",
    "file_name": "log_20260228.txt",
    "content": "[20260228][INFO] Validate job complete without error.\n[20260228][ERROR] Validate job failed with error code 123."
}
```