# ReachInbox - AI Email Automation Tool 🤖

ReachInbox is an intelligent email automation tool that seamlessly integrates with Google and Outlook accounts to provide AI-powered email responses and task management. Built with Node.js and powered by OpenAI, it helps streamline your email communication workflow.

## ✨ Key Features

- 📧 Unified email management for Google and Outlook accounts
- 🤖 AI-powered contextual email responses using OpenAI
- 🔄 Efficient background task processing with BullMQ
- 🔐 Secure authentication via OAuth2
- ✉️ Reliable email delivery through Nodemailer

## 🛠️ Tech Stack

- **Backend**: Node.js, Express.js
- **Task Queue**: BullMQ
- **AI Integration**: OpenAI API
- **Authentication**: OAuth2
- **Email Service**: Nodemailer
- **Email Providers**: Gmail and Outlook APIs

## 🚀 Getting Started

### Prerequisites

- Node.js installed on your system
- Gmail and/or Outlook account
- OpenAI API key
- OAuth2 credentials for Gmail and Outlook

### Installation

1. Clone the repository
```bash
git clone https://github.com/harshraj6582/Assignment.git
```

2. Navigate to the project directory
```bash
cd reachinbox-assignment
```

3. Install dependencies
```bash
npm install
```

4. Create a `.env` file in the root directory with the following variables:
```env
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

5. Start the server
```bash
npm start
```

The application will be available at `http://localhost:3000`.

## 📚 API Documentation

### Outlook Endpoints

#### Read Email
```http
GET /outlook/{email}/read-Msg/{messageid}
```
Retrieves details of a specific message from Outlook.

#### Send Email
```http
POST /outlook/{email}/send-Mail/
```
Sends an email through Outlook.

#### Send AI Response
```http
POST /outlook/sendone/{recipientEmail}/{messageId}
```
Generates and sends an AI-powered response using BullMQ.

### Gmail Endpoints

#### Read Email
```http
GET /gmail/{email}/read-Msg/{messageid}
```
Retrieves details of a specific message from Gmail.

#### Send Email
```http
POST /gmail/{email}/send-Mail/
```
Sends an email through Gmail.

#### Send AI Response
```http
POST /gmail/sendone/{recipientEmail}/{messageId}
```
Generates and sends an AI-powered response using BullMQ.

## 💡 Usage Examples

### Reading Emails
```bash
curl --location -g 'http://localhost:3000/outlook/user@example.com/read-Msg/{messageid}'
```

### Sending Emails
```bash
curl --location 'http://localhost:3000/gmail/user@example.com/send-Mail/' \
--data-raw '{
    "from": "user@example.com",
    "to": "recipient@example.com",
    "label": "Urgent Follow Up"
}'
```

### Automated AI Responses
```bash
curl --location 'http://localhost:3000/gmail/sendone/recipient@example.com/{messageId}' \
--data-raw '{
    "from": "user@example.com",
    "to": "recipient@example.com"
}'
```

## 🔐 Security

- All sensitive credentials are stored in environment variables
- OAuth2 implementation ensures secure access to email accounts
- API endpoints are protected against unauthorized access

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📬 Contact

For questions or support, reach out to:
- Email: [harshraj211430@gmail.com](mailto:harshraj211430@gmail.com)

## 📝 License

This project is open source and available under the MIT License.

---

⭐ Don't forget to star this repo if you find it helpful!
