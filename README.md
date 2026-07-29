<p align="center">
  <img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/3f788404-0958-4c94-a27b-f6ad5c86a1ca" />
</p>

# Entra ID Users, Groups, & RBAC

This project demonstrates role-based access control and identity governance within a Microsoft Entra ID tenant for the fictional company, Kennon Technologies. Building on the users and groups established in Lab 1, this lab covers assigning built-in Entra ID roles with varying scopes of privilege, delegating administrative permissions using Administrative Units and role-assignable groups, automating group membership through dynamic membership rules, and streamlining license management through group-based licensing. All configurations are hands-on in a live Microsoft Entra ID tenant and reflect real-world IAM practices around least-privilege access, delegated administration, and identity lifecycle automation.

---

## Prerequisites

This is the second lab of the [Entra ID Lab Series](https://github.com/RyanKennon/Entra-ID-Lab-Series/tree/main).
The following are required before starting this lab:

- **Completion of [Lab 1: Entra ID Tenant Setup & Configuration](https://github.com/RyanKennon/Entra-Tenet-Setup)** — this lab builds directly on the users and groups created there
- **Microsoft Entra ID P1 or P2 License** — required for Administrative Units, dynamic group membership, and group-based licensing
- **GitHub Account** — required to follow along with lab documentation and host your own portfolio

---

## Environments and Technologies Used

- Microsoft Entra ID (Cloud-Native Tenant)
- Microsoft Entra Admin Center
- Microsoft Entra ID Roles and Administrators
- Microsoft Entra ID Administrative Units
- Microsoft Entra ID Dynamic Groups
- Microsoft 365 Admin Center (Group-Based Licensing)

---

## Table of Contents

- [1) Role-Based Access Control](#1-role-based-access-control)
- [2) Administrative Units](#2-administrative-units)
- [3) Dynamic Groups](#3-dynamic-groups)
- [4) Group-Based Licensing](#4-group-based-licensing)

---

### 1) Role-Based Access Control

Built-in Entra ID roles grant users specific administrative permissions across the tenant. Assigning distinct roles to different users based on their function — rather than granting broad access to everyone — demonstrates least-privilege role selection, a core IAM governance principle.

1. In the **Entra ID** dropdown select **Roles & Admins**
2. Find and select **User Administrator** then select **Add Assignments**
3. Select **John Smith** then **Add**

<p align="center">
  <img width="837" height="377" alt="image" src="https://github.com/user-attachments/assets/464cf4be-1a72-42f9-b6db-23880f8d9571" />
</p>

4. Select the **Roles & Admins** tab then select **Helpdesk Administrator**
5. Select **+Add Assignments** then select **Tyler Novak** then **Add**

<p align="center">
  <img width="840" height="382" alt="image" src="https://github.com/user-attachments/assets/9066cdf0-db51-45ec-a9e0-f297752ee118" />
</p>

6. Open the **Users** tab then select **John Smith**
7. Select the **Assigned Roles** tab and confirm the **User Administrator** role appears

<p align="center">
  <img width="984" height="292" alt="image" src="https://github.com/user-attachments/assets/0055336b-289d-47a9-a08f-b8cca2f4a4f0" />
</p>

8. Open the **Users** tab then select **Tyler Novak**
9. Select the **Assigned Roles** tab and confirm the **Helpdesk Administrator** role appears

<p align="center">
  <img width="974" height="288" alt="image" src="https://github.com/user-attachments/assets/66444f75-2697-4e2e-a0c3-0851eb35c3af" />
</p>

---

### 2) Administrative Units

Administrative Units allow administrative roles to be scoped to a specific subset of users rather than applying tenant-wide. Combined with a role-assignable group, this demonstrates a scalable delegation model — role membership is managed through group membership, and the resulting permissions only apply within the bounded administrative unit rather than across the entire tenant.

1. In the **Entra ID** dropdown select **Roles & Admins**
2. Select the **Admin Units** tab the press **Add**
3. Create an **Administrative Unit** with the following information then **Create:**
   - **Name:** AU-IT-Department
   - **Description:** Scoped Administrative Unit for IT Department Users
  
<p align="center">
  <img width="652" height="472" alt="image" src="https://github.com/user-attachments/assets/54260a0a-8631-4e30-80eb-712b767736ad" />
</p>

4. On the **Admin Units** page select **AU-IT-Department** then select **Add Member**
5. Choose **John Smith, Marcus Reed, and Tyler Novak** then press **Select**

<p align="center">
  <img width="837" height="361" alt="image" src="https://github.com/user-attachments/assets/c7bf3917-d839-4007-8ca2-5ee1519b2006" />
</p>

6. In the **Entra ID** dropdown select **Groups** then **New Group**
7. Create a **group** with the following information then select **Create:**
   - **Group Type:** Security
   - **Group Name:** RG-Helpdesk-Admins
   - **Microsoft Entra Roles can be Assigned to the Group:** Yes
   - **Members:** Marcus Reed
  
<p align="center">
  <img width="715" height="600" alt="image" src="https://github.com/user-attachments/assets/04f09e2d-7716-4a79-8ba8-731147fbdb93" />
</p>

8. In the **Entra ID** dropdown select **Roles & Admins**
9. Select **Helpdesk Administrator** then **Add Assignments**
10. Press the **Groups** tab then select **RG-Helpdesk-Admins** then press **Add**

<p align="center">
  <img width="837" height="400" alt="image" src="https://github.com/user-attachments/assets/dfef90dd-93eb-42cc-a151-ce5f67824cce" />
</p>

11. In the **Entra ID** dropdown select **Users** then select **Marcus Reed**
12. Select the **Assigned Roles** tab and confirm the **Helpdesk Administrator** role appears

<p align="center">
  <img width="809" height="331" alt="image" src="https://github.com/user-attachments/assets/90932d84-ab15-461b-ba7f-00c36cc51dfa" />
</p>

---

### 3) Dynamic Groups

Dynamic groups automatically manage membership based on rules evaluated against user attributes, rather than requiring manual add/remove actions. This eliminates administrative overhead and ensures group membership stays accurate as user attributes (such as department) change over time.

1. In the **Entra ID** dropdown select **Groups** then open the **All Groups** tab then press **New Group**
2. Create a **Group** with the following information:
   - **Group Type:** Security
   - **Group Name:** DG-IT-Department
   - **Dynamic Group:** Auto-Populated by Department Attribute
   - **Membership Type** Dynamic User
  
<p align="center">
  <img width="700" height="543" alt="image" src="https://github.com/user-attachments/assets/b23dd12b-faa0-4d69-a640-b4997aca7138" />
</p>

3. Click **Add Dynamic Query**
4. Then configure a **Rule** using the following information:
   - **Property:** Department
   - **Operator:** Equals
   - **Value:** IT
  
<p align="center">
  <img width="883" height="541" alt="image" src="https://github.com/user-attachments/assets/ab6cd2b0-f60e-46a8-ae69-a1b810ba54f5" />
</p>

5. Press **save** then **Create**
6. On the **Groups** page select the **DG-IT-Department** group then open the **Members** tab
7. Confirm **John Smith, Marcus Reed, and Tyler Novak** appear on the **Direct Members** page

<p align="center">
  <img width="868" height="448" alt="image" src="https://github.com/user-attachments/assets/10b7228f-2ad1-480b-a504-7e1137696bdd" />
</p>

---

### 4) Group-Based Licensing

Group-based licensing allows licenses to be assigned once at the group level rather than individually to each user. Members of the group automatically inherit the license, streamlining license management and ensuring consistent license assignment across a department or team.

1. In the **Entra ID** dropdown select **Groups** then open the **All Groups**
2. Select the **SG-IT-Staff** group then open the **Members** tab then **Add Members**
3. Add **Marcus Reed** then press **Select**

<p align="center">
  <img width="870" height="349" alt="image" src="https://github.com/user-attachments/assets/7b94a019-880b-43c5-926b-382558fcd23d" />
</p>

4. In the **SG-IT-Staff** group open the **licenses** page then press the **Go to M365 Admin Center** link
5. Open the **Groups** dropdown on the left side of the screen then select **All Groups**
6. Open the **Security Groups** tab then select the **SG-IT-Staff** group
7. Go to the **Licenses and Apps** tab then check **Microsoft Entra ID P2** then **Save Changes** then **Save**

<p align="center">
  <img width="772" height="605" alt="image" src="https://github.com/user-attachments/assets/c7563e29-d5ce-48f8-b7e9-dbcfffd6b526" />
</p>

8. In the **Entra ID** dropdown select **User**
9. Select **Marcus Reed** then open the **Licenses** tab
10. Confirm the **Microsoft Entra ID P2** license appears

<p align="center">
  <img width="834" height="275" alt="image" src="https://github.com/user-attachments/assets/04624722-af0d-4a30-9d7f-c6fdeba7d4ba" />
</p>

---

> **Note:** This lab is intentionally left open. The role, group, and 
> licensing structures configured here serve as the foundation for all 
> subsequent Entra ID labs in the 
> [Entra ID Lab Series](https://github.com/RyanKennon/Entra-ID-Lab-Series/tree/main).

---

<p align="left">
  <a href="https://github.com/RyanKennon/Entra-Tenet-Setup">⬅ Lab 1 — Entra ID Tenant Setup & Configuration</a>
</p>

<p align="right">
  <a href="[Lab 3 repo URL]">Lab 3 — Authentication Security & MFA ➡</a>
</p>
