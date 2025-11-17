# Day 10 - Automated Document Processing with Google Drive and AI

Created a workflow that monitors a Google Drive folder for new documents, processes them using AI, and stores the generated output back in Google Drive.

## Features

- Monitors a specific Google Drive folder for new document uploads
- Extracts text from various document formats (PDF, DOCX, etc.)
- Uses Google Gemini to analyze and process document content
- Saves generated images back to Google Drive
- Sends Slack notifications for successful processing
- Handles errors and retries failed operations

## Prerequisites

- Google Cloud Platform service account with Drive API access
- Google Gemini API key
- Slack webhook URL (optional, for notifications)

## Setup Instructions

1. Set up credentials.json for Google Drive API access
2. Configure the following environment variables:
   - `GOOGLE_APPLICATION_CREDENTIALS`: Path to your service account key file
   - `GEMINI_API_KEY`: Your Google Gemini API key
   - `GOOGLE_DRIVE_OUTPUT_FOLDER_ID`: ID of the folder to store generated images
   - `SLACK_WEBHOOK_URL`: (Optional) Your Slack incoming webhook URL for notifications

## Workflow Overview

![Day 10 Workflow](./workflow.png)

1. **Schedule Trigger**: Runs on a schedule to check for new documents
2. **Google Drive Node**: Lists files in the specified folder
3. **Filter Node**: Identifies new, unprocessed documents
4. **Google Drive Node**: Downloads the document content
5. **Text Extractor Node**: Extracts text from various document formats
6. **Google Gemini Node**: Processes the content and generates output
7. **Google Drive Node**: Saves the generated output back to Drive
8. **Slack Node**: (Optional) Sends a notification with processing results

## Example Output

![Example Output](./2025-11-16.png)

## Troubleshooting

- Ensure all API keys and credentials are correctly configured
- Check execution logs for detailed error messages
- Verify that the Google Drive folders have the correct sharing settings
- Make sure the service account has read/write access to the necessary folders

## Next Steps

- Add support for more document formats
- Implement more advanced content processing
- Add email notifications in addition to Slack
- Create a dashboard to track processing metrics

## Video Demo

<video src="./demo.mp4" controls width="100%"></video>
