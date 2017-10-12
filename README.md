# Authentiq OpenID Registration Handler for Salesforce

Registration handler for using Authentiq as a Salesforce OpenID provider.

It will create/register a new user and update an already registered one based on the info the user provides from the Authentiq ID application.

Handles the following user attributes:

First name
Last name
Email
Preferred username (if its an existing one, it generates a new)
Mobile Phone
Phone
Address
Locale
Timezone

Also, in the case of a new user it creates an alias
