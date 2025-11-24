# Application Policies

App policies are important for securing self-hosted applications. In doing so this means that after exposing any app via tunnels, restriction to that app is defined, preventing any malicious parties from attempting to gain access.

## Creating a rule group

Rule groups are useful for defining users and their access levels. By defining a rule group, should a user need access to an application, the group itself is all that needs to be updated instead of going into the policy itself and updating the list of users directly.

Log into Cloudflare > Zero Trust > Access controls > Policies. You'll see two tabs: `Reusable policies` and `Rule groups`. Click on `Rule groups` and configure a group based on whichever chosen parameters. After saving the rule group it can then be used for any policies created in the future.

## Creating an application policy

Navigate to the `Application policies`, click `Add a policy`, define the basic information and then under `Add rules` you can select `Rule group` under the `Selector` dropdown list. Next to this under `Value`, select all rule groups that you wish to allow (or restrict) access for.

## Adding a self-hosted application

Now that a rule group and reusable policy are in place, any self-hosted applications can make use of both. Back under `Access controls` select `Applications` and `Add an application`. From here define the basic information for the app. Under `Access policies` click on `Select existing policies` and choose which policies should be applied to the application.  

Now, whenever a user attempts to access an application e.g. portainer at the specified domain e.g. `portainer.myhomelab.com`, they will have to authenticate themselves before access to the app is granted. By creating application policies via Cloudflare, you can ensure each of your applications is consistent in the level of access applied and fine-tune any authentication for applications that handle any sensitive data.
