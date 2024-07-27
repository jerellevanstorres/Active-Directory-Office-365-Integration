# Active-Directory-Office-365-Integration
## Detailed Setup Guide for Active Directory and Office 365 Integration Lab

## Introduction
This guide provides a step-by-step walkthrough for setting up and integrating Active Directory with Office 365 using Windows Server 2019 and Azure AD Connect. It includes detailed instructions, screenshots, and configuration examples to ensure a smooth setup process.

## Prerequisites
Before starting, ensure you have the following:
- VirtualBox installed on your machine
- Windows Server 2019 ISO
- Windows 10 ISO (optional)
- Office 365 Developer Account
- Azure AD Connect installer

## Step 1: Install VirtualBox
1. Download VirtualBox from the [VirtualBox download page](https://www.virtualbox.org/wiki/Downloads).
![VBPage](https://github.com/user-attachments/assets/226da852-f49c-4ba1-a8c0-687294a7c216)
2. Run the installer and follow the on-screen instructions to complete the installation.

## Step 2: Install Operating Systems
### Windows Server 2019
1. Download Windows Server 2019 ISO from the [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2019).
![Server2019](https://github.com/user-attachments/assets/6298934a-9962-4912-ae24-c9a264bb5744)

### Windows 10 (Optional)
1. Download Windows 10 ISO from the [Microsoft website](https://www.microsoft.com/en-us/software-download/windows10ISO).
![Windows10](https://github.com/user-attachments/assets/95d05052-1ffe-4027-9ea5-c405e31eb83c)

## Step 3: Create Virtual Machines
### Windows Server 2019 VM
1. Open VirtualBox and click **New**.
2. Name your VM (e.g., WinServer2019) and select the Windows Server 2019 ISO.
![VBDC](https://github.com/user-attachments/assets/9c58296c-9d0d-49ff-a090-6d49a8f4e558)
3. Allocate memory (RAM) (e.g., 4 GB).
4. Create a virtual hard disk now, choose VDI, dynamically allocated, and allocate at least 40 GB.
5. Follow the prompts to complete the VM creation.

### Windows 10 VM (Optional)
1. Follow the previous steps to create another VM named Win10, with Microsoft Windows as the type and Windows 10 (64-bit) as the version.
![windows 10 VB](https://github.com/user-attachments/assets/9be3e495-a588-499f-8fa8-c5efba3c9d39)
2. Allocate memory (e.g., 2 GB) and a virtual hard disk (e.g., 30 GB).

## Step 4: Configure Active Directory
### Promote Windows Server to Domain Controller
1. Open **Server Manager**.
![DC Dashboard](https://github.com/user-attachments/assets/b8eee0e2-eb9d-4136-a2c2-c8386df409e4)
2. Click **Add roles and features**.
3. Select **Role-based or feature-based installation**, choose your server, and click **Next**.
4. Select **Active Directory Domain Services** and add features if prompted. Continue clicking **Next** until you reach **Install**.
![AD Domain Services](https://github.com/user-attachments/assets/22f317fa-4c7a-45f4-a015-8aec82fc9216)
5. After installation, click on the **Notifications** flag in Server Manager, then click **Promote this server to a domain controller**.
![promote server](https://github.com/user-attachments/assets/8f5605ba-2f55-41c3-9a0b-5e50adacd4a9)
6. Select **Add a new forest** and enter a root domain name (e.g., domain.com).
7. Follow the prompts to configure the domain controller
8. Complete the wizard and the server will restart.
![domain admin](https://github.com/user-attachments/assets/3c0d548e-8c4b-4e5a-a573-6d503bd37553)

## Step 5: Add and Manage Users in Active Directory
### Add a User in Active Directory
1. In Server Manager, click **Tools** > **Active Directory Users and Computers**.
![add user](https://github.com/user-attachments/assets/68fc67b1-5412-4ad4-bf06-543a630cb1fa)
2. Navigate to your domain, right-click the **Users** container, and select **New** > **User**.
![new user AD](https://github.com/user-attachments/assets/d11d18c3-e5e6-45f8-9bd1-df9e7f01f128)
3. Enter the user details (e.g., First name: John, Last name: Doe, User logon name: jdoe).
![New user details](https://github.com/user-attachments/assets/3d1425bb-93f1-494d-a59a-277ae38997bf)
4. Set a password and configure account options as needed.
5. Click **Next** and **Finish**.

### Elevate User to Admin
1. In **Active Directory Users and Computers**, navigate to the **Users** container.
2. Find and right-click the user you created and select **Add to a group**.
![AD add to group](https://github.com/user-attachments/assets/e5679136-3363-4fc0-807b-77878e1d711e)
3. Type Domain Admins and click **Check Names** to verify, then click **OK**.
![AD domain admin](https://github.com/user-attachments/assets/1424f672-4ba3-4696-b90f-eff1cebd8ca1)

## Step 6: Set Up Office 365 Integration
### Sign Up for Office 365 Developer Account
1. Visit the [Office 365 Developer Program](https://developer.microsoft.com/en-us/office/dev-program) and sign up for a free developer account.
![365 free](https://github.com/user-attachments/assets/09a66d9f-ea4b-4713-8f67-14cd52cc7eca)
2. Follow the prompts to set up your Office 365 environment.

### Install and Configure Azure AD Connect
#### Download Azure AD Connect
1. Download Azure AD Connect from the [Azure AD Connect download page](https://www.microsoft.com/en-us/download/details.aspx?id=47594).
![azure download](https://github.com/user-attachments/assets/5ae76f67-738c-45ad-a050-7b278a1c0ff0)

#### Install Azure AD Connect
1. On your Windows Server 2019 VM, run the Azure AD Connect installer.
![welcome az](https://github.com/user-attachments/assets/3e1b0a59-4bdb-49c8-9b08-fa311e8cda67)
2. Choose **Express Settings** if you want a quick setup or **Customize** for more control.
3. Enter your Office 365 global admin credentials and your on-premises AD admin credentials.
4. Follow the prompts to configure synchronization settings.
![az configuration](https://github.com/user-attachments/assets/06ae68fb-37c7-459c-b564-cfd71b451080)

## Step 7: Verify Integration
### Check Synchronization Status
#### Azure Portal
1. Go to the [Azure portal](https://portal.azure.com) and log in with your Office 365 admin credentials.
2. Ensure synchronization is enabled and running correctly.
![azure synced](https://github.com/user-attachments/assets/70bdbf5f-77b9-4bd5-b089-cf7fb749a5ec)
3. Navigate to **Azure Active Directory** > **Users** and verify that your on-premises AD users are listed.
![Azure Active Users](https://github.com/user-attachments/assets/80416679-b814-44cf-88f3-c1c946d43854)


