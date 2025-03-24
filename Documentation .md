### Setup Guide

#### 1. Credentials Configuration
- **Gmail**: OAuth2 API credentials https://docs.n8n.io/integrations/builtin/credentials/google/oauth-generic/
- **Google Drive**: OAuth2 API credentials with access to:
  - Create folders
  - Upload files
- **Google Sheets**: OAuth2 API for spreadsheet logging
- **Telegram**: Bot token with message sending permissions https://docs.n8n.io/integrations/builtin/credentials/telegram/

#### 2. Key Nodes Configuration

**A. Company Name Setup**
- `SetCompanyName` node: 
  - Replace "YourCompany" with your actual company name
  - ![image](https://github.com/user-attachments/assets/799a217c-0b30-4082-aa0b-9527fec6fe95) ![image](https://github.com/user-attachments/assets/e4ad416b-07ae-4b42-a4ee-6b63d3d9ee6d)

  - This becomes the root folder name in Google Drive
  - ![image](https://github.com/user-attachments/assets/2d770fa9-fb1c-4d61-bd4a-5e6ac4af1303)


**B. Folder Structure**
Workflow creates this automatic structure:
```
Company Name/
└── Invoices/
    └── YYYY/
        └── MM/
            └── Sender Name/
                └── Attached PDFs
```

**C. Notifications**
- Two Telegram nodes:
  1. For successful PDF processing
 
  ![image](https://github.com/user-attachments/assets/c8b55fec-372a-4bba-88a2-3efe03af3816) ![image](https://github.com/user-attachments/assets/141bd116-0704-4ad7-b878-dcfc15f37bca)

  3. For emails without PDF attachments
     
  ![image](https://github.com/user-attachments/assets/465767ec-eeda-48c0-a5f7-ae69bd476607) ![image](https://github.com/user-attachments/assets/11ec9b69-56ea-4f71-bf8f-d486db996cc5)

  - Set chat ID in both nodes

**D. Google Sheets Logging**
- Pre-configured spreadsheet:
  - Logs: Company, Sender, Email text, Date/Time
  
  ![image](https://github.com/user-attachments/assets/77afe9dd-6f97-44ab-bc8d-c95d5c993140)
  

#### 3. Execution Flow
1. Trigger: Checks for new "invoice" emails every minute

![image](https://github.com/user-attachments/assets/b91a60f3-43c2-4802-8b75-1212c1a97a88) ![image](https://github.com/user-attachments/assets/79b70a61-e688-4b94-859d-1959d5d113ba)


3. Validation: Confirms PDF attachment exists

![image](https://github.com/user-attachments/assets/cb77b824-5871-4002-91ad-df53cf38d801) ![image](https://github.com/user-attachments/assets/7451a0f6-eb50-4c1f-bf06-4216d3920464)

5. Processing:
   - Creates missing folders (if needed)
     
       1. Check if the folder exists

        ![image](https://github.com/user-attachments/assets/ee084543-8451-4562-bdd2-349ae52e4a37) ![image](https://github.com/user-attachments/assets/652d4f44-7ea1-482a-9d59-1f0026a2d30f)

       2. Creates a folder if it does not exist
    
       ![image](https://github.com/user-attachments/assets/9bbb5ed8-3911-4c3e-a38b-3fb8675368cb) ![image](https://github.com/user-attachments/assets/0a83d435-c8ab-4d09-a956-d45d9665b326)

   - Uploads PDF to correct location

      ![image](https://github.com/user-attachments/assets/8eb6358f-e337-4b33-a7cd-05dc3b3cb830)

   - Logs details to Sheets
  
      ![image](https://github.com/user-attachments/assets/e533a0d8-5c0a-4738-b69b-7c21d5c74642)

   - Sends Telegram notification
   - Marks email as read

#### 4. Error Handling
- Non-PDF emails: Sends Telegram alert and skips processing
  
![image](https://github.com/user-attachments/assets/3bfa3175-0042-4a02-a34e-b3a3a06d789b) ![image](https://github.com/user-attachments/assets/e86d06f8-0935-4860-aef6-b3494b8a4771)

#### 5. Customization Options
- Change folder hierarchy by modifying Drive nodes
- Adjust email search filters in Gmail trigger
- Modify notification messages in Telegram nodes
- Add additional processing steps after PDF upload

Workflow is ready after:
1. Credentials setup
2. Company name configuration
3. Telegram chat ID update
4. Google Sheet ID verification (if using custom sheet)
