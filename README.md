# Warehouse Workstation Deployment & Domain Migration – ~20 PCs

A real-world on-site IT support deployment completed during my IT Support internship, involving the configuration and migration of approximately **20 Windows workstations** across a warehouse and office environment.

The deployment included **DNS configuration, Active Directory domain joining, user profile migration, endpoint management agent installation, Microsoft 365 deployment, user application configuration, troubleshooting, and final validation**.

> **Privacy Notice:** Client-identifying information, internal IP addresses, domain names, usernames, email addresses, server paths, credentials, and other sensitive information have been removed or redacted.

---

## Project Overview

I worked alongside a senior technician to configure and migrate approximately **20 Windows workstations** across a warehouse and its associated office areas.

The deployment was completed over **two days**, which required us to work efficiently while maintaining a consistent configuration across each workstation.

During the deployment, several unexpected issues also occurred, requiring troubleshooting while continuing to work within the deployment timeframe.

### My Responsibilities

My hands-on tasks included:

- Configuring DNS settings
- Flushing the Windows DNS resolver cache
- Renaming Windows workstations
- Joining computers to the Active Directory domain
- Restarting and verifying domain membership
- Migrating existing Windows user profiles using ForensiT User Profile Wizard
- Installing the ConnectWise Automate endpoint agent
- Verifying the remote management installation
- Deploying Microsoft 365 Apps
- Configuring Outlook
- Completing Microsoft Authenticator verification
- Configuring Microsoft Teams
- Configuring OneDrive
- Troubleshooting a Microsoft Teams synchronisation issue
- Performing final user and application checks
- Repeating the deployment process across approximately 20 workstations

<p align="center">
  <img width="332" height="371" alt="image" src="https://github.com/user-attachments/assets/c82e68bf-4067-4ff8-ad2f-ec4cfd27465f" />
  <img width="393" height="393" alt="image" src="https://github.com/user-attachments/assets/5e80e99a-2308-4147-8c76-6639bafc328e" />


</p>

<p align="center">
  <i>On-site workstation configuration during the warehouse deployment.</i>
</p>

---

# Deployment Workflow

The general deployment process for each workstation was:

**DNS Configuration → PC Rename → Domain Join → Restart → Profile Migration → User Login → Endpoint Agent Installation → Microsoft 365 Deployment → Outlook / Teams / OneDrive Configuration → Final Testing**

---

# 1. Network & DNS Configuration

Before joining each workstation to the organisation's Active Directory domain, I first configured the required DNS settings.

## Why DNS Configuration Was Important

Active Directory relies heavily on DNS.

A workstation needs to communicate with the organisation's DNS infrastructure so that it can locate domain resources and communicate correctly with the Active Directory environment.

An incorrect DNS configuration can result in problems such as:

- Domain controllers not being located
- Domain join failures
- Authentication problems
- Internal resources failing to resolve correctly

## Configuration Process

I navigated to:

**Settings → Network & Internet → Ethernet → DNS Server Assignment**

I then changed the DNS configuration according to the organisation's network requirements.

> Internal DNS addresses have been redacted from this public project.

<p align="center">
  <img width="615" height="626" alt="image" src="https://github.com/user-attachments/assets/82377d9a-19b1-4f1c-8d01-421995244e83" />
  <img width="391" height="455" alt="image" src="https://github.com/user-attachments/assets/5751ed40-75ea-4451-a2fd-45e55526239c" />

</p>

<p align="center">
  <i>Reviewing and configuring the required DNS settings before joining the workstation to the domain.</i>
</p>

---

## Flushing the DNS Resolver Cache

After changing the DNS configuration, I opened **Command Prompt** and ran:

```cmd
ipconfig /flushdns
```

This cleared previously cached DNS records from the workstation.

The purpose of this step was to ensure that Windows performed fresh DNS lookups using the newly configured DNS settings rather than relying on previously cached information.

A successful result returned:

```text
Successfully flushed the DNS Resolver Cache.
```

<p align="center">
  <img width="623" height="372" alt="image" src="https://github.com/user-attachments/assets/7c2c9eb9-5f95-4aae-9e63-c5bff132dfb5" />
</p>

<p align="center">
  <i>Flushing the Windows DNS resolver cache after updating the DNS configuration.</i>
</p>

The workstation was then restarted before continuing with the domain configuration.

---

# 2. Workstation Rename & Active Directory Domain Join

The next stage was to rename the workstation according to the organisation's computer naming convention and join it to the **Active Directory domain**.

I navigated to:

**This PC → Properties → Domain or Workgroup**

<p align="center">
  <img width="390" height="401" alt="image" src="https://github.com/user-attachments/assets/75b68eda-3aab-4f91-a4df-21ad2be8154a" />
  <img width="427" height="486" alt="image" src="https://github.com/user-attachments/assets/c0517f2f-8020-4d46-90f4-78ea405b9644" />

</p>

---

## Computer Naming

Each workstation needed to follow the organisation's existing computer naming convention.

Using a consistent naming convention makes endpoints easier for IT administrators to identify, support, and manage across the environment.

I changed the computer name to the assigned workstation name before proceeding with the domain join.

---

## Joining the Active Directory Domain

Under **Computer Name / Domain Changes**, I selected:

**Member of → Domain**

and entered the organisation's Active Directory domain.

<p align="center">
  <img width="617" height="647" alt="image" src="https://github.com/user-attachments/assets/9dbf97e0-f03c-4618-8ba7-17c34a4776dc" />

  <img width="592" height="510" alt="image" src="https://github.com/user-attachments/assets/e188d6c9-d66b-4388-9c0f-0739b5e53723" />


</p>

<p align="center">
  <i>Configuring the workstation name and Active Directory domain membership. Client information has been redacted.</i>
</p>

Windows then requested credentials from an account authorised to join computers to the domain.

After successful authentication, Windows confirmed that the workstation had successfully joined the domain.

<p align="center">
  <img width="427" height="247" alt="image" src="https://github.com/user-attachments/assets/b70b5512-6656-456c-b1d5-4febbf5124b0" />
  <img width="431" height="280" alt="image" src="https://github.com/user-attachments/assets/c1fb9e84-2e3a-4996-96c9-47b0fadb3d7b" />

</p>

<p align="center">
  <i>Authorising and confirming the Active Directory domain join.</i>
</p>

The workstation then required a restart for the changes to take effect.

### Result

After restarting, the computer was successfully operating as a member of the organisation's Active Directory environment.

This allowed domain users to authenticate to the workstation and access organisational resources according to the environment's configuration.

---

# 3. Domain Administrator Login

After the workstation restarted, I logged in using an authorised domain administrative account so that the remaining configuration and migration tasks could be completed.

<p align="center">
  <img width="512" height="602" alt="image" src="https://github.com/user-attachments/assets/30e61d19-9a23-443d-9485-96742b8455a2" />

</p>

<p align="center">
  <i>Signing into the newly domain-joined workstation using an authorised administrative account. Credentials have been redacted.</i>
</p>

This provided the required administrative permissions for the next stage of the deployment — migrating the existing user's Windows profile.

---

# 4. User Profile Migration

One of the most important parts of the deployment was migrating the existing Windows user profile to the new domain account.

Simply joining a computer to a domain does not automatically associate the user's existing local Windows profile with their domain account.

Without profile migration, the user could sign into the domain and receive a new Windows profile rather than continuing to use their existing working environment.

This could separate the user from their existing:

- Desktop configuration
- User-specific settings
- Existing profile data
- Application preferences

To address this, we used **ForensiT User Profile Wizard (ProfWiz)**.

---

## Using ForensiT User Profile Wizard

I launched **User Profile Wizard** and selected the existing Windows user profile that needed to be associated with the user's domain account.

<p align="center">
  <img width="568" height="526" alt="image" src="https://github.com/user-attachments/assets/f4829f0d-27d9-447d-9d8b-c56ad29ae66d" />

  <img width="577" height="583" alt="image" src="https://github.com/user-attachments/assets/9ff83682-f231-4eb6-9292-3ac34edfcb4e" />

</p>

<p align="center">
  <i>Launching ForensiT User Profile Wizard to begin the profile migration process.</i>
</p>

The migration process updated the profile association so that the user's domain account could use the existing Windows profile.

During the migration, User Profile Wizard performed the required profile and permission changes.

<p align="center">
  <img width="717" height="660" alt="image" src="https://github.com/user-attachments/assets/da808a4d-d449-40e6-a4e9-91b64addb9df" />

</p>

<p align="center">
  <i>User Profile Wizard successfully completing the profile migration.</i>
</p>

Once the migration completed, the workstation was restarted.

---

## Verifying the Migrated Profile

After restarting, the user could sign into Windows using their **domain account**.

I then verified that the user could access their existing Windows environment through the migrated profile.

### Result

Instead of starting with a completely new Windows profile, the domain user could continue using their existing profile environment after the domain migration.

This helped reduce disruption to the user during the migration process.

---

# 5. ConnectWise Automate Agent Installation

After completing the domain and profile migration, I installed the organisation's endpoint management agent.

The installation files were provided through the company's deployment USB.

<p align="center">
  <img width="671" height="433" alt="image" src="https://github.com/user-attachments/assets/8b892064-d8c3-4e27-8ad0-95b4e2e87ab3" />

</p>

I located the appropriate installation package and ran the installer with administrative privileges:

**Right-click → Run as administrator**

<p align="center">
  <img width="400" height="367" alt="image" src="https://github.com/user-attachments/assets/a1bd94eb-0cd7-40cb-b056-29c564fb9301" />
 
Running the installer as administrator ensured that the installation had the required permissions to install the management components on the workstation.

---

## ConnectWise Automate

The endpoint was configured with the **ConnectWise Automate Remote Agent**.

<p align="center">
   <img width="467" height="377" alt="image" src="https://github.com/user-attachments/assets/2a217f07-443f-48d4-922e-6675f9f64276" />

</p>

</p>

<p align="center">
  <i>ConnectWise Automate Remote Agent installation completed successfully.</i>
</p>

An RMM (**Remote Monitoring and Management**) agent allows an IT support provider to centrally manage and support endpoints.

Depending on the organisation's configuration, an RMM platform can assist IT teams with:

- Endpoint monitoring
- Remote support
- Software management
- Maintenance
- Troubleshooting
- Device visibility

My responsibility during this deployment was to install the provided agent package on the workstations.

---

## Verifying the Agent Installation

After installation, I opened:

**Control Panel → Programs and Features**

to confirm that the required remote management component had been successfully installed.

<p align="center">
  <img width="503" height="516" alt="image" src="https://github.com/user-attachments/assets/175fdb31-b9a0-4e46-864e-906c64445aee" />

</p>

<p align="center">
  <i>Verifying that the required remote management component was present after installation.</i>
</p>

This verification step ensured that the required software component was present before moving on to the next stage of the deployment.

---

# 6. Microsoft 365 Apps Deployment

The next stage was installing the Microsoft 365 applications required by the users.

Instead of manually downloading and installing individual Office applications on every workstation, the organisation provided a standardised deployment method using a network-hosted Microsoft 365 installation package and configuration file.

I opened **Command Prompt as Administrator** and ran the organisation-provided deployment command.

For privacy, the actual internal server and configuration paths have been removed from this public project.

Example:

```cmd
\\<INTERNAL-SERVER>\<M365-PATH>\setup.exe /configure \\<INTERNAL-SERVER>\<M365-PATH>\<CONFIGURATION-FILE>.xml
```

The configuration file allowed the required Microsoft 365 applications to be installed using the organisation's predefined deployment configuration.

<p align="center">
  <img width="675" height="477" alt="image" src="https://github.com/user-attachments/assets/5135fd2d-01f1-4f7c-b289-0d5451f56277" />

</p>

<p align="center">
  <i>Deploying Microsoft 365 Apps using the organisation's network-based deployment configuration.</i>
</p>

After the installation completed successfully, I proceeded with configuring the applications required by each user.

---

# 7. Outlook Configuration & Authentication

The first user application I configured was **Microsoft Outlook**.

I signed into Outlook using the user's organisational Microsoft account.

The sign-in process required **Microsoft Authenticator** verification.

<p align="center">
  <img width="386" height="531" alt="image" src="https://github.com/user-attachments/assets/b53df5b9-2294-4088-8424-1904d2203ab5" />
</p>

<p align="center">
  <i>Completing Microsoft account authentication during Outlook configuration.</i>
</p>

After authentication was completed, the organisational account was successfully added to the workstation.

Outlook then began synchronising the user's mailbox.

<p align="center">
  <img width="552" height="482" alt="image" src="https://github.com/user-attachments/assets/3a294d2b-9f2d-4709-84a5-548e3673812f" />

</p>

<p align="center">
  <i>Organisational Microsoft account successfully added to the workstation.</i>
</p>

I verified that Outlook was able to access and synchronise the user's mailbox before continuing.

---

# 8. Microsoft Teams Configuration

After Outlook, I configured **Microsoft Teams** using the same organisational Microsoft account.

During this stage, we encountered an unexpected issue.

---

# Troubleshooting Case – Microsoft Teams Synchronisation Issue

## Issue

After signing into Microsoft Teams, the application was unable to synchronise correctly.

Teams displayed a message similar to:

> **"Can't sync right now. We'll try again soon."**

Refreshing the application multiple times did not resolve the problem.

<p align="center">
 <img width="631" height="285" alt="image" src="https://github.com/user-attachments/assets/3fe680d4-b329-4361-b633-f018285cfef8" />

</p>

---

## Troubleshooting

Rather than repeatedly refreshing the application, I opened **Task Manager** to check the running Teams process.

I then:

1. Located **Microsoft Teams**
2. Right-clicked the process
3. Selected **End Task**
4. Relaunched Microsoft Teams

<p align="center">
  <img width="531" height="515" alt="image" src="https://github.com/user-attachments/assets/211afec2-5639-4981-9d97-f16dc7e7fcf5" />

</p>

Ending the task completely terminated the existing Teams process rather than simply refreshing the application interface.
<img width="638" height="523" alt="image" src="https://github.com/user-attachments/assets/cb0e1a89-cebd-4319-9434-85f6f9bd7226" />

After relaunching Teams, the application started a fresh process and the synchronisation issue was resolved.

---

## Result

**Issue:** Microsoft Teams was unable to synchronise correctly.

**Initial Action:** Refreshed Teams multiple times.

**Troubleshooting:** Terminated the Teams process through Task Manager.

**Resolution:** Relaunched Microsoft Teams.

**Result:** Teams resumed normal operation and synchronisation.

### What I Learned

This was a useful reminder that refreshing an application does not necessarily restart the underlying process.

When an application becomes stuck or fails to synchronise correctly, completely terminating and restarting the process can be an effective early troubleshooting step before moving to more disruptive actions such as reinstalling the application.

---

# 9. OneDrive Configuration

The final major user application I configured was **Microsoft OneDrive**.

I signed into OneDrive using the user's organisational account.

<p align="center">
 <img width="443" height="465" alt="image" src="https://github.com/user-attachments/assets/d310ae55-93c8-43ff-bfe4-0b87b401faca" />

</p>

Once authenticated, OneDrive began connecting the workstation to the user's organisational cloud storage.

I allowed the synchronisation process to begin and then verified the OneDrive status.

<p align="center">
  <img src="images/onedrive-synced.jpg" width="650">
</p>

A successful configuration displayed:

> **Backed up and synced**
<img width="486" height="297" alt="image" src="https://github.com/user-attachments/assets/a386f820-168e-4c81-8a29-57cdce6c59b9" />


This confirmed that OneDrive was connected and synchronising successfully.

---

# 10. Final Validation

After completing the workstation migration and application configuration, I performed final checks before considering each workstation ready for use.

The validation process included:

- Confirming the workstation had joined the Active Directory domain
- Confirming the user could log in with their domain account
- Verifying the migrated Windows profile
- Confirming the endpoint management agent was installed
- Verifying Microsoft 365 installation
- Confirming Outlook authentication and mailbox synchronisation
- Confirming Microsoft Teams was operational
- Confirming OneDrive was connected and synchronising
- Checking that the workstation was ready for the user

The same general deployment workflow was repeated across approximately **20 PCs throughout the warehouse and office areas**.

---

# Key Technical Workflow

```text
Existing Windows Workstation
          │
          ▼
Configure Internal DNS
          │
          ▼
Flush DNS Cache
          │
          ▼
Rename Workstation
          │
          ▼
Join Active Directory Domain
          │
          ▼
Restart
          │
          ▼
Domain Administrator Login
          │
          ▼
Migrate Existing User Profile
          │
          ▼
Restart
          │
          ▼
Domain User Login
          │
          ▼
Install ConnectWise Automate Agent
          │
          ▼
Deploy Microsoft 365 Apps
          │
          ▼
Configure Outlook + MFA
          │
          ▼
Configure Microsoft Teams
          │
          ▼
Configure OneDrive
          │
          ▼
Final Validation
          │
          ▼
Workstation Ready for User
```

---

# Technologies & Tools Used

| Technology / Tool | Purpose |
|---|---|
| Windows 11 | Workstation operating system |
| Active Directory | Domain membership and organisational authentication |
| DNS | Domain and internal resource name resolution |
| Command Prompt | DNS cache management and Microsoft 365 deployment |
| `ipconfig /flushdns` | Clear cached DNS resolver records |
| ForensiT User Profile Wizard | Existing Windows profile migration |
| ConnectWise Automate | Remote monitoring and endpoint management agent |
| ScreenConnect / ConnectWise Control | Remote support component |
| Microsoft 365 Apps | Productivity application suite |
| Microsoft Outlook | Email configuration |
| Microsoft Authenticator | User authentication / MFA verification |
| Microsoft Teams | Communication and collaboration |
| Microsoft OneDrive | Organisational cloud file synchronisation |
| Task Manager | Application process troubleshooting |

---

# Challenges

The deployment needed to be completed across approximately **20 workstations within two days**.

This required maintaining a consistent deployment process while also responding to unexpected issues such as the Microsoft Teams synchronisation problem.

Working through multiple workstations also reinforced the importance of following a repeatable configuration process and verifying each stage before moving on.

---

# What I Learned

This deployment gave me practical experience with a complete workstation migration process in a live business environment.

Rather than practising individual technologies separately in a lab, I was able to see how multiple IT support technologies work together during a real deployment.

In particular, I gained a stronger understanding of:

- Why DNS configuration is critical before joining a workstation to Active Directory
- How Windows workstations are renamed and joined to a corporate domain
- The difference between a local Windows profile and a domain user profile
- How existing profiles can be migrated during a domain transition
- How endpoint management agents are deployed and verified
- How Microsoft 365 applications can be deployed using a standardised configuration
- How Outlook, Teams and OneDrive are configured for organisational users
- How MFA forms part of the Microsoft 365 sign-in process
- How to troubleshoot application issues using Task Manager
- The importance of final validation before returning a workstation to the user
- The importance of maintaining a consistent workflow when deploying multiple endpoints

---

# Skills Demonstrated

- Windows 11 workstation deployment
- Active Directory domain joining
- DNS configuration
- Windows networking fundamentals
- Computer naming and domain membership
- User profile migration
- ForensiT User Profile Wizard
- Endpoint / RMM agent installation
- ConnectWise Automate
- Microsoft 365 deployment
- Outlook configuration
- Microsoft Authenticator / MFA
- Microsoft Teams configuration
- OneDrive configuration and synchronisation
- Windows Task Manager troubleshooting
- Application troubleshooting
- Post-deployment validation
- On-site IT support
- Working alongside a senior technician
- Multi-endpoint deployment in a production environment

---

# Role Clarification

I completed this deployment **alongside a senior technician** as part of my IT Support internship.

My hands-on responsibilities included workstation configuration, DNS changes, domain joining, profile migration, endpoint agent installation, Microsoft 365 deployment, user application setup, troubleshooting and validation.

The work was performed within an existing client environment using the organisation's established infrastructure, credentials, deployment packages and procedures.

---

# Key Takeaway

This project gave me hands-on experience supporting a **real multi-workstation deployment in a production business environment**.

The most valuable part of the experience was understanding how DNS, Active Directory, Windows profiles, endpoint management and Microsoft 365 fit together as part of a complete workstation migration process.

Repeating the workflow across approximately **20 PCs** also helped me become more confident and efficient with workstation deployment while maintaining consistency across multiple endpoints.
