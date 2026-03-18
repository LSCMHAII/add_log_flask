# add_log_flask

This is a simple Flask application that provides an API endpoint to add log entries to a specified file. The application is designed to run in a Docker container and can be easily integrated into existing workflows for logging purposes.

## Features
- Add log entries to a specified file in a specified directory.
- Configurable base path for log storage via environment variables.

## Simple setup locally
1. Install dependency:
```bash
pip install -r requirements.txt
```
2. Run the Flask application:
```bash
python app.py
```

## API Endpoint

### POST /run
This endpoint accepts a JSON payload to specify the `dir_name`, `file_name`, and `content` to be added to the log file.
- `dir_name`(string): The directory where the log file is located (e.g., "logs/").
- `file_name`(string) (required): The name of the log file (e.g., "log_20260228.txt").
- `content`(string) (required): The log content to be added. It can contain multiple lines separated by the newline character `\n`. Each line will be treated as a separate log entry.
- Content will be divided into lines by the newline character `\n` and each line will be added to the log file.
- Timestamps will be added to each log entry in the format `[YYYY-MM-DD HH:MM:SS]`.

#### Request Body
```json
{
    "dir_name": "logs/",
    "file_name": "log_20260228.txt",
    "content": "[INFO] Validate job complete without error."
}

or

{
    "dir_name": "logs/",
    "file_name": "log_20260228.txt",
    "content": "[INFO] Validate job complete without error.\n[ERROR] Validate job failed with error code 123."
}
```

#### Response
```json
[
  {
    "message": "Workflow was started"
  }
]
```

### Example output in log file
```
[2026-03-11 11:29:15][INFO] Validate job complete without error.
[2026-03-11 11:29:15][ERROR] Validate job failed with error code 123.
```