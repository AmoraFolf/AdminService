# Updating AdminService

Updating AdminService is very easy; however, if you have custom commands or custom additions/changes to other modules, you'll have to carry them over to the new version.

---

!!! warning
    As mentioned above, it is VERY important to copy the custom commands you've made, as well as changes to other scripts inside of AdminService, or they will be deleted. This is because you are inserting a new version of AdminService from its factory form. It does not include your custom changes to it.

To update, you simply do the process shown on the `Setup` page. Insert the module, make sure it is parented to (or has the common ancestor of) `ServerScriptService` or `ServerStorage`, then copy over any custom commands and changes you made to other scripts over to the new ones, and delete the old version of AdminService.

After you've done those steps, boom! You successfully updated AdminService, and if you had any, carried over your custom commands and changes to it!

[Previous Page](https://amorafolf.github.io/AdminService/basics/adding_commands/){ .md-button .md-button--primary } [Next Page](https://amorafolf.github.io/AdminService/read-me-important/){ .md-button .md-button--primary }