# Securely storing credentials in 1Password

We use [1Password for Teams](https://1password.com/) for securely storing and accessing credentials.

Our team's account is located at [`https://savaslabs.1password.com/`](https://savaslabs.1password.com).

## Usage

1. [Download the applications](https://1password.com/downloads/) for your phone and computer.
1. Sign-in to the Savas Labs vault. You can use 1Password with your personal account, if you have one.
1. Place credentials in client-specific vaults. You may need to create a new Vault if it doesn't exist; ask if you have questions. Use tags as appropriate so it's easier for teammates to find credentials.
    1. _Private_. This is your personal Savas Labs vault. You can store your personal account logins for websites (e.g. for `pm.savaslabs.com`, for client sites, etc)
    1. _Savas Labs_. This is for shared credentials that don't apply to a single client, for example, Pingdom. (Note that some of our intrastructure credentials live in an Infrastructure vault that only admins have access to.)
    1. _{Client name}_. Shared client credentials like server, API keys, etc. Your personal login credentials for the client go in your _private_ vault, not here.
1. _Do not store sensitive information in Redmine_. It is okay to store things like development site URLs or non-critical information in the Redmine wiki. Use 1Password for server credentials, API keys, etc.
1. Update READMEs as needed so that teammates know where in 1Password they can find credentials.
1. If needed, [we can add a client as a guest to a specific vault](https://support.1password.com/guests/) which eliminates the need for sharing credentials with a client via e-mail.
