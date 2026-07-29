<p align="center">
  <img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/3f788404-0958-4c94-a27b-f6ad5c86a1ca" />
</p>

# Entra-ID-Users-Groups-RBAC

### 1) Role-Based Access Control

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

