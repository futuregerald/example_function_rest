# intercom-tools
Tools for Support to work with our helpdesk Intercom
David has implemented an auto-responder in the bitballoon repo. For more info on that, [please read our docs](https://internal-docs.netlify.com/support/intercom-auto-responder/). In this repo we'll have additional tools that use Netlify's Lambda integration

## Functions:

- intercom_contact.js
    - function that's triggered from [https://www.netlify.com/support/](https://www.netlify.com/support/) and creates new conversations in intercom when users contact us. If the e-mail used to signup is associated with Netlify account, then conversations will be opened for that user. If not and a lead exists, then conversations will be opened using that lead ID. If a lead doesn't exist, a new lead will be created for the conversation.
- intercom_tag_enforcer.js
    - This function is called via webhook from intercom when a conversation closes. It checks if the conversation has been tagged, if not, it will re-open it and add a note to remind support to add a tag to the conversation. Only conversations in unassigned and paid mailboxes will be re-opened.
- intercom_user_info.js
    - This function is triggered when a new converation is opened. It polls Netlify's API for information about the user and their sites and posts it in private internal notes in the conversations when they are opened. 
   
## House Keeping

- Directories ending with `.old` contain old code that is not being used. 

## To Do

- Add function that uses bugsnags API to search for events related to the user and their domain when conversations are opened, and puts relevant information in the conversation as a private internal note. 