# Invoice Processing from Email

## Who is this for?
This workflow is for **business owners** and **accounting teams** who receive invoices via email and need to organize them systematically in Google Drive.

## What it does
- Scans Gmail for unread emails containing "Invoice" or "invoice"
- ![image](https://github.com/user-attachments/assets/c231e5b4-4265-4d89-8e6e-ea56809b3d24)

- The workflow processes attachments only if they are in PDF format, otherwise it sends a notification to Telegram and marks the email as read
- ![image](https://github.com/user-attachments/assets/00dd91a5-1f1c-4ede-a574-04b4e4bf8cf9)

- Organizes invoices in Google Drive by: Company Name → Invoices → Year → Month → Sender Name
- ![image](https://github.com/user-attachments/assets/cdaa90a6-46cc-495a-b51e-a0317b6854d3)

- Logs invoice details in Google Sheets and sends Telegram notifications
- ![image](https://github.com/user-attachments/assets/3948c6d4-e05d-4cf7-a55e-1c67cc922db9)
  
- Marks processed emails as read

## Setup
1. Set up credentials for:
   - Gmail
   - ![image](https://github.com/user-attachments/assets/d3f5cb5e-584a-46ed-8572-6a1d800f6493)
   - Google Drive
   - ![image](https://github.com/user-attachments/assets/df8c03b2-0e6b-46f6-987d-1474c20761ef)
   - Google Sheets
   - ![image](https://github.com/user-attachments/assets/9e1547dc-d6db-4fa1-9784-3a233c2914fd)
   - Telegram
   - ![image](https://github.com/user-attachments/assets/90035d42-ca18-42a3-8ea7-727c9a3e7b90)
     
2. Configure company name in "SetCompanyName" node

   ![image](https://github.com/user-attachments/assets/bf2a783b-61ca-4b31-904d-0b735d595417)
   
4. Set Telegram chat ID in notification nodes

   ![image](https://github.com/user-attachments/assets/f9cc106f-7505-4ef1-bcc3-b5931faa4e78)

6. Activate workflow

    ![image](https://github.com/user-attachments/assets/d1fcf0f1-de39-479c-a530-85adab6e4ad8)

## Customization
- Change folder structure by modifying the Google Drive nodes
- Adjust email search criteria in Gmail trigger
- Modify notification message in Telegram nodes
- Update Google Sheet logging format as needed
