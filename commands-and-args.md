commands can be specified in shell format or json array format

In JSON array format, the first item SHOULD BE a executable command

`ENTRYPOINT` is the default command specified. All other commands will be only APPENDED to it

In practice, entrypoint will specify the executable command and command will specify the default cli params. This is only possible if both `entrypoint` and `command` instructions are specified in JSON array format