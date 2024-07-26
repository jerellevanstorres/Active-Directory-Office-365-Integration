# Active-Directory-Office-365-Integration# Detailed Setup Guide for Active Directory and Office 365 Integration Lab

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
2. Run the installer and follow the on-screen instructions to complete the installation.

## Step 2: Create Virtual Machines
### Windows Server 2019 VM
1. Open VirtualBox and click **New**.
2. Name your VM (e.g., WinServer2019), select Microsoft Windows as the type, and Windows 2019 (64-bit) as the version.
3. Allocate memory (RAM) (e.g., 4 GB).
4. Create a virtual hard disk now, choose VDI, dynamically allocated, and allocate at least 40 GB.
5. Follow the prompts to complete the VM creation.

### Windows 10 VM (Optional)
1. Follow the previous steps to create another VM named Win10, with Microsoft Windows as the type and Windows 10 (64-bit) as the version.
2. Allocate memory (e.g., 2 GB) and a virtual hard disk (e.g., 30 GB).

## Step 3: Install Operating Systems
### Windows Server 2019
1. Download Windows Server 2019 ISO from the [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2019).
2. In VirtualBox, select your WinServer2019 VM, click **Start**, and select the Windows Server 2019 ISO.
3. Follow the installation prompts, including setting up the administrator account.

### Windows 10 (Optional)
1. Download Windows 10 ISO from the [Microsoft website](https://www.microsoft.com/en-us/software-download/windows10ISO).
2. In VirtualBox, select your Win10 VM, click **Start**, and select the Windows 10 ISO.
3. Follow the installation prompts.

## Step 4: Configure Active Directory
### Promote Windows Server to Domain Controller
1. Open **Server Manager**.
2. Click **Add roles and features**.
3. Select **Role-based or feature-based installation**, choose your server, and click **Next**.
4. Select **Active Directory Domain Services** and add features if prompted. Continue clicking **Next** until you reach **Install**.
5. After installation, click on the **Notifications** flag in Server Manager, then click **Promote this server to a domain controller**.
6. Select **Add a new forest** and enter a root domain name (e.g., domain.com).
7. Follow the prompts to configure the domain controller, including setting a Directory Services Restore Mode (DSRM) password.
8. Complete the wizard and the server will restart.

## Step 5: Add and Manage Users in Active Directory
### Add a User in Active Directory
1. In Server Manager, click **Tools** > **Active Directory Users and Computers**.
2. Navigate to your domain, right-click the **Users** container, and select **New** > **User**.
3. Enter the user details (e.g., First name: John, Last name: Doe, User logon name: jdoe).
4. Set a password and configure account options as needed.
5. Click **Next** and **Finish**.

### Elevate User to Admin
1. In **Active Directory Users and Computers**, navigate to the **Users** container.
2. Find and right-click the user you created and select **Add to a group**.
3. Type `Domain Admins` and click **Check Names** to verify, then click **OK**.

## Step 6: Set Up Office 365 Integration
### Sign Up for Office 365 Developer Account
1. Visit the [Office 365 Developer Program](https://developer.microsoft.com/en-us/office/dev-program) and sign up for a free developer account.
2. Follow the prompts to set up your Office 365 environment.

### Install and Configure Azure AD Connect
#### Download Azure AD Connect
1. Download Azure AD Connect from the [Azure AD Connect download page](https://www.microsoft.com/en-us/download/details.aspx?id=47594).

#### Install Azure AD Connect
1. On your Windows Server 2019 VM, run the Azure AD Connect installer.
2. Choose **Express Settings** if you want a quick setup or **Customize** for more control.
3. Enter your Office 365 global admin credentials and your on-premises AD admin credentials.
4. Follow the prompts to configure synchronization settings.

## Step 7: Verify Integration
### Check Synchronization Status
#### Azure AD Connect Tool
1. On the Windows Server, open the **Azure AD Connect** tool.
2. Ensure synchronization is enabled and running correctly.

#### Azure Portal
1. Go to the [Azure portal](https://portal.azure.com) and log in with your Office 365 admin credentials.
2. Navigate to **Azure Active Directory** > **Users** and verify that your on-premises AD users are listed.

