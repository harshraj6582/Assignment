Here's an updated version of the `README.md` file that includes the technology stack and Gmail details:

```md
# EachInbox-Assignment

This project is an email automation tool that parses and checks emails from Google and Outlook email IDs, responds to emails based on the context using AI, and manages tasks with BullMQ.

## Features
- Parse and check emails from both Google and Outlook.
- Respond to emails based on context using OpenAI's text generation.
- Use BullMQ to handle tasks efficiently.

## Technology Stack

- **Node.js**: Server-side JavaScript runtime for handling requests and tasks.
- **Express.js**: Web framework used for building the API endpoints.
- **BullMQ**: Task management queue for handling email responses in the background.
- **OpenAI API**: For generating AI-based responses to emails.
- **OAuth2**: For authenticating and accessing Google and Outlook email accounts.
- **Nodemailer**: For sending emails via Gmail and Outlook.

## Installation

1. Clone the repository:

```bash
git clone https://github.com/harshraj6582/Assignment.git
```

2. Navigate to the project directory:

```bash
cd eachinbox-assignment
```

3. Install the dependencies:

```bash
npm install
```

4. Create a `.env` file with the following environment variables:

```bash
OPENAI_API_KEY=your-openai-api-key
OUTLOOK_CLIENT_ID=your-outlook-client-id
OUTLOOK_CLIENT_SECRET=your-outlook-client-secret
OUTLOOK_REDIRECT_URI=your-outlook-redirect-uri
OUTLOOK_REFRESH_TOKEN=your-outlook-refresh-token
GMAIL_CLIENT_ID=your-gmail-client-id
GMAIL_CLIENT_SECRET=your-gmail-client-secret
GMAIL_REDIRECT_URI=your-gmail-redirect-uri
GMAIL_REFRESH_TOKEN=your-gmail-refresh-token
```

5. Start the server:

```bash
npm start
```

The application will run on `http://localhost:3000`.

## Endpoints

### Outlook Endpoints

#### 1. GET - Read Outlook Mail

##### Request:
```http
GET /outlook/{:email}/read-Msg/{:messageid}
```
- This endpoint retrieves the details of a specific message in the Outlook mailbox.

##### Example:
```bash
curl --location -g 'http://localhost:3000/outlook/harshraj211430@gmail.com/read-Msg/{:messageid}'
```

##### Response:
```json
{
  "id": "",
  "createdDateTime": "",
  "receivedDateTime": "",
  "subject": "",
  "bodyPreview": "",
  "importance": "",
  "sender": {
    "emailAddress": {
      "name": "",
      "address": ""
    }
  },
  "toRecipients": [
    {
      "emailAddress": {
        "name": "",
        "address": ""
      }
    }
  ]
}
```

#### 2. POST - Send Mail Using Outlook

##### Request:
```http
POST /outlook/{email}/send-Mail/
```
- Sends an email via Outlook.

##### Example:
```bash
curl --location 'http://localhost:3000/outlook/harshraj211430@gmail.com/send-Mail/' \
--data-raw '{
    "from": "harshraj211430@gmail.com",
    "to": "recipient@example.com",
    "label": "Follow Up"
}'
```

##### Response:
```json
{
  "message": "Success",
  "result": "Email sent successfully"
}
```

#### 3. POST - Send Mail via BullMQ

##### Request:
```http
POST /outlook/sendone/{recipientEmail}/{messageId}
```
- Sends an email response using BullMQ based on the content of the specified message ID.

##### Example:
```bash
curl --location 'http://localhost:3000/outlook/sendone/recipient@example.com/{messageId}' \
--data-raw '{
    "from": "harshraj211430@gmail.com",
    "to": "recipient@example.com"
}'
```

##### Response:
```json
{
  "message": "Email sent via BullMQ"
}
```

### Gmail Endpoints

#### 1. GET - Read Gmail Mail

##### Request:
```http
GET /gmail/{:email}/read-Msg/{:messageid}
```
- This endpoint retrieves the details of a specific message in the Gmail mailbox.

##### Example:
```bash
curl --location -g 'http://localhost:3000/gmail/harshraj211430@gmail.com/read-Msg/{:messageid}'
```

##### Response:
```json
{
  "id": "",
  "createdDateTime": "",
  "receivedDateTime": "",
  "subject": "",
  "bodyPreview": "",
  "importance": "",
  "sender": {
    "emailAddress": {
      "name": "",
      "address": ""
    }
  },
  "toRecipients": [
    {
      "emailAddress": {
        "name": "",
        "address": ""
      }
    }
  ]
}
```

#### 2. POST - Send Mail Using Gmail

##### Request:
```http
POST /gmail/{email}/send-Mail/
```
- Sends an email via Gmail.

##### Example:
```bash
curl --location 'http://localhost:3000/gmail/harshraj211430@gmail.com/send-Mail/' \
--data-raw '{
    "from": "harshraj211430@gmail.com",
    "to": "recipient@example.com",
    "label": "Urgent Follow Up"
}'
```

##### Response:
```json
{
  "message": "Success",
  "result": "Email sent successfully"
}
```

### Automated Response

For both Outlook and Gmail, the API can automatically generate and send replies based on the email's content using AI.

### 3. POST - Send AI Response via BullMQ (Gmail)

##### Request:
```http
POST /gmail/sendone/{recipientEmail}/{messageId}
```
- Sends an AI-generated email response using BullMQ based on the content of the specified Gmail message.

##### Example:
```bash
curl --location 'http://localhost:3000/gmail/sendone/recipient@example.com/{messageId}' \
--data-raw '{
    "from": "harshraj211430@gmail.com",
    "to": "recipient@example.com"
}'
```

##### Response:
```json
{
  "message": "AI-generated response sent via BullMQ"
}
```

## Usage

1. **Reading Emails**: Use the `GET /outlook/{email}/read-Msg/{messageid}` or `GET /gmail/{email}/read-Msg/{messageid}` endpoint to retrieve email details.
2. **Sending Emails**: Use the `POST /outlook/{email}/send-Mail/` or `POST /gmail/{email}/send-Mail/` endpoint to send an email.
3. **Automated AI Responses**: Use the BullMQ-powered endpoints to automatically respond to emails based on their content using AI.

## Contact

For any issues or questions, feel free to contact me via email at [harshraj211430@gmail.com](mailto:harshraj211430@gmail.com).

---

**Note:** This project uses OpenAI for AI-based email responses, BullMQ for managing background tasks, and OAuth2 for authentication with both Google and Outlook. Make sure to configure your API keys and credentials properly in the `.env` file.
```

### Updates Made:
1. **Technology Stack** section added to explain the tech used in the project.
2. **Gmail Endpoints** section added for reading and sending emails via Gmail.
3. Instructions on configuring `.env` variables updated with Gmail credentials.
4. Contact email added consistently as requested.
