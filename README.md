# selfcare-email-templates

This repo will contain the email's templates used by the selfcare projects.
These templates are created using mjml.

## How to apply changes

To modify them it's possible to use:
* [The online editor](https://mjml.io/try-it-live)
* [A local installation](https://mjml.io/download)
* [The VisualStudioCode plugin](https://marketplace.visualstudio.com/items?itemName=mjmlio.vscode-mjml)

Once completed the changes on the template, the output minified html should exported and saved together with the template itself.

## How to deploy changes
The templates are deployed through Terraform project developed inside [selfcare-infra](https://github.com/pagopa/selfcare-infra) repository.
Thus the exported html should be provided to DEVOPS team in order to deploy it.
The [table below](#stored-templates) describes for each template what selfcare-infra resource to update and what k8s's deployment's pods restart (often these templates are cached, thus it's recommended to restart them).

## Stored Templates

|Template|Figma|Descrizione|selfcare-infra resource|Deployment to restart|Note|
|--------------|---------------------|-----------|-----------------------|------------------------|----|
|PEC_Adesione|[PEC allegato contratto](https://www.figma.com/file/14WthFMcY9UU6G3BqnZHi2/Self-Care---MVP-v.2-UI?node-id=8235%3A154567)|Email sent once submitted a request to onboard a party to a product|[src/core/contracts_template/mail/1.0.0.json](https://github.com/pagopa/selfcare-infra/tree/main/src/core/resources/templates/email/user_added_single_role.ftlh)|interop-be-party-process|The html should be base64 encoded and put it inside the “body” field of the json in the selfcare-infra file|
|Email_AggiuntaSingoloRuolo-utente|[Aggiunta di un nuovo utente / singolo ruolo](https://www.figma.com/file/14WthFMcY9UU6G3BqnZHi2/Self-Care---MVP-v.2-UI?node-id=8237%3A154971)|Email sent once added a new role to a user in order to allow him/her to access to a product to which the party has already been onboarded|[src/core/resources/templates/email/user_added_single_role.ftlh](https://github.com/pagopa/selfcare-infra/tree/main/src/core/resources/templates/email/user_added_multi_role.ftlh)|b4f-dashboard||
|Email_AggiuntaMultiRuolo-utente|[Aggiunta di un nuovo utente / doppio ruolo](https://www.figma.com/file/14WthFMcY9UU6G3BqnZHi2/Self-Care---MVP-v.2-UI?node-id=10118%3A77009)|Email sent when adding multiple role to a user|[src/core/resources/templates/email/user_added_multi_role.ftlh](https://github.com/pagopa/selfcare-infra/tree/main/src/core/resources/templates/email/user_deleted.ftlh)|b4f-dashboard||
|Email_Rimozione|[Rimozione](https://www.figma.com/file/14WthFMcY9UU6G3BqnZHi2/Self-Care---MVP-v.2-UI?node-id=8237%3A155441)|Email sent when removing a role from a user|[src/core/resources/templates/email/user_deleted.ftlh](https://github.com/pagopa/selfcare-infra/tree/main/src/core/resources/templates/email/user_deleted.ftlh)|b4f-dashboard||
|Email_Sospensione|[Sospensione](https://www.figma.com/file/14WthFMcY9UU6G3BqnZHi2/Self-Care---MVP-v.2-UI?node-id=8237%3A155166)|Email sent when suspending a role to a user|[src/core/resources/templates/email/user_suspended.ftlh](https://github.com/pagopa/selfcare-infra/tree/main/src/core/resources/templates/email/user_suspended.ftlh)|b4f-dashboard||
|Email_Riabilitazione|[Riabilitazione](https://www.figma.com/file/14WthFMcY9UU6G3BqnZHi2/Self-Care---MVP-v.2-UI?node-id=8237%3A155225)|Email sent when resuming a role to a user|[src/core/resources/templates/email/user_activated.ftlh](https://github.com/pagopa/selfcare-infra/tree/main/src/core/resources/templates/email/user_activated.ftlh)|b4f-dashboard||
