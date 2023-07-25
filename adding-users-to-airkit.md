Overview
--------


Once an [Org](https://support.airkit.com/docs/airkit-organizations) has been created, users with [admin permissions](https://support.airkit.com/docs/managing-user-roles) can invite new users to join. Having an account associated with an Org is required to access any part of that Org, including the [Console](https://support.airkit.com/docs/console) and associated [Portals](https://support.airkit.com/docs/portal-capabilities). To grant someone the ability to view or work with any part of your Org, you will need to invite them and assign them a [role](https://support.airkit.com/docs/managing-user-roles) within it.


Invites are managed in the [Console](https://support.airkit.com/docs/console), under Settings -> Invites. Again, note that **only an admin can invite new users to join an Org**. If you cannot access this part of the Console, it is likely because you are not occupying a [user role](https://support.airkit.com/docs/managing-user-roles) that grants you permission to do so:


![Screen_Shot_2021-10-06_at_4.06.20_PM.png](./assets_v1714/adding-users-to-airkit-v1714-0.png)


To invite a new user to join your Org, click on the *Create New*button, fill out the Invite Fields that appear in the Inspector, and then click on the *Create* button that appears in the bottom left:


![2021-10-06_16-09-08__1_.gif](./assets_v1714/adding-users-to-airkit-v1714-1).gif)


Invite Fields
-------------


* **Email** *(required)* - The email address where the invite will be sent
* **SSO with Google Only** *(checkbox)*- If selected, the user’s Google OAuth credentials (if applicable) can be used to log in
* **Username** *(optional)*- The username that will be given to the invitee If no username is designated here, the user will be allowed to set their own. *Note: usernames are case-sensitive.*
* **First Name** *(optional)*- The invitee's first name. If no value is given, the user will be allow to set it themselves.
* **Last Name** *(optional)*- The invitee's last name. If no value is given, the user will be allow to set it themselves.
* **Starting URL** *(dropdown menu, default: Studio)* - Designates what part of the Org the invitee will be taken to upon first logging in. Options are [Studio](https://support.airkit.com/docs/studio), [Console](https://support.airkit.com/docs/console), and [Portal](https://support.airkit.com/docs/portal-capabilities).
* **Roles** *(dropdown menu, selection required)*- The [role](https://support.airkit.com/docs/managing-user-roles) granted to the invited user. The role a user is assigned defines the permissions and limitations they will have when working inside the Org.
* **User Variables** *(optional)*- Defines what (if any) User Variables (and their associated values) will be associated with the invitee's account. User Variables serve as an additional means of security, as they limit access to [Portal Pages](https://support.airkit.com/docs/portal-capabilities) to only users associated with precisely-matching pairs of User Variables and values. For more on how to implement this added layer of security, check out [documentation on the Portal Builder](https://support.airkit.com/docs/portal-builder). *Note: User Variables and their associated values are case-sensitive.*


Once an invite is accepted, users with [admin permissions](https://support.airkit.com/docs/managing-user-roles) can change the value of these fields, which are managed in the [Console](https://support.airkit.com/docs/console), under Settings -> Users.