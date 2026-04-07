# Microsoft Entra ID Conditional Access Lab  
## Location-Based Policy: Block All Countries Except Canada

## Overview
In this lab, I created a new Microsoft 365 tenant, set up my own admin account, and configured a Conditional Access policy in Microsoft Entra ID to block sign-ins from any country other than Canada.

This was a basic hands-on exercise to practice tenant setup, Conditional Access configuration, location-based access control, and safe testing.

---

## Goal
Create a Conditional Access policy that blocks sign-ins from all countries except Canada.

---

## Environment
- Microsoft 365 tenant
- Microsoft Entra ID
- Conditional Access
- Admin account created inside the tenant

---

## Important Notes Before Configuration
There were 2 important things to handle before applying the policy:

1. **Canada must first be added in Named Locations**  
   Canada did not appear as a selectable location in the policy until I created it first under **Named Locations**.

2. **My own admin account had to be excluded from the policy**  
   Since the policy was applied to **All Users**, excluding my own account was important to avoid locking myself out of the tenant during testing.

---

## Step-by-Step Process

### 1. Create a new Microsoft 365 tenant
I first created a new Microsoft 365 tenant for this lab environment.

This gave me:
- a tenant
- a default domain ending in `.onmicrosoft.com`
- my first user account, which served as the admin account

---

### 2. Sign in to Microsoft Entra ID
After the tenant was created, I signed in to Microsoft Entra ID using my admin account.

From there, I navigated to the Conditional Access section.

---

### 3. Attempt to create the Conditional Access policy
I initially went to:

**Microsoft Entra ID → Conditional Access → Policies → New policy**

My goal was to create a location-based rule that would block sign-ins from every country except Canada.

However, I ran into an issue:  
**Canada was not yet available as a selectable location.**

---

### 4. Create Canada as a Named Location
To solve that, I went to:

**Microsoft Entra ID → Conditional Access → Named locations**

Then I created a new location and added **Canada** as the country.

This step was necessary because the policy could not properly reference Canada until it had first been defined in Named Locations.

---

### 5. Go back and create the policy again
After adding Canada in Named Locations, I returned to:

**Conditional Access → Policies → New policy**

This time I was able to continue with the location-based configuration.

---

### 6. Configure users
In the policy settings, I selected:

- **All Users**

Then I added an exclusion for **my own admin account**.

This was an important safety step so I would not accidentally block my own access to the tenant.

---

### 7. Configure location conditions
Under location settings, I configured the policy to:

- **Include:** Any location
- **Exclude:** Canada

This means the policy would target sign-ins from everywhere, except Canada.

---

### 8. Configure access control
For access control, I selected:

- **Block access**

This made the policy deny sign-ins coming from locations outside Canada.

---

### 9. Enable the policy
After reviewing the settings, I saved and enabled the policy.

---

## Testing
To test the setup, I signed in to my Microsoft 365 account from another browser to create a fresh sign-in session.

This allowed me to verify whether the Conditional Access policy was being applied correctly to a new login attempt.

---

## Result
The policy was successfully configured to block sign-ins from countries outside Canada.

To further validate the setup, I tested sign-in attempts using a VPN from external locations such as Romania and Ukraine.

- When attempting to sign in from these locations, I was able to observe the access behavior based on the policy configuration.
- The sign-in attempts and their outcomes were visible in Microsoft Entra ID under:
  - **Monitoring & Health → Sign-in logs**

This confirmed that:
- location-based conditions were being detected correctly
- Conditional Access policies were being applied during authentication
- sign-in activity could be tracked and analyzed through logs

---

## Skills Practiced
- Microsoft 365 tenant setup  
- Microsoft Entra ID administration  
- Conditional Access configuration  
- Named Locations setup  
- Location-based access restriction  
- VPN-based testing of access policies  
- Sign-in log analysis in Microsoft Entra ID  
- Security testing and validation  
- Basic security documentation  
