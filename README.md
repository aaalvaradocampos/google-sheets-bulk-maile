# 📧 Google Sheets Secure Bulk Mailer

A robust Google Apps Script designed to send bulk emails safely from Google Sheets. It bypasses Gmail's BCC limits by chunking recipients into mini-batches, includes an "Anti-Error Shield" for invalid emails, and updates your sheet in real-time to prevent duplicate sending.

## ✨ Features

* 🚀 **BCC Mini-Batching:** Sends emails in concealed batches of 50 (BCC) to avoid Gmail's "Limit Exceeded: Email Recipients Per Message" errors.
* 🛡️ **Anti-Duplicate Lock:** Uses `PropertiesService` and real-time row-by-row saving to ensure no recipient gets the same email twice, even if the script is interrupted.
* ✅ **Auto-Validation:** Scans for malformed email addresses before sending. Invalid emails are skipped and tagged as `Error: Invalid Email` in your sheet without stopping the script.
* 🖼️ **Inline Image Embedding:** Injects images directly into the HTML email body (using CID) so recipients don't need Google Drive permissions to view them.
* 🕒 **Time-based Execution:** Built-in logic to allow execution only during specific authorized hours.

## 📋 Prerequisites

1. A **Google Account** (Workspace or personal).
2. A **Google Sheet** containing your email list.
3. An image hosted on **Google Drive** (if you want to include inline images).

## 🚀 Installation & Setup

1. Open your Google Sheet.
2. Navigate to **Extensions > Apps Script** in the top menu.
3. Delete any code in the editor and paste the contents of `bulk_mailer.js`.
4. Update the Configuration Variables (see below).
5. Click the **Save** (floppy disk) icon.
6. Go to the **Triggers** menu (clock icon on the left) and create a new Time-driven trigger to run this function automatically (e.g., Every hour).

## ⚙️ Configuration

Before running the script, make sure to update the following variables at the top of the code to match your environment:

```javascript
var sheetName = "YOUR_SHEET_NAME_HERE"; // The exact name of your tab
var DRIVE_IMAGE_ID = "YOUR_DRIVE_IMAGE_ID_HERE"; // The ID of your image on Google Drive
var visibleRecipient = "visible_email@yourdomain.com"; // The email shown in the "To:" field
var subject = "Your Email Subject Here";
