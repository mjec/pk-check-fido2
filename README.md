# pk-check-fido2
A script for use with polkit.spawn() to require a user to verify their presnce with a FIDO2 key

I use this together with [1Password's SSH agent](https://developer.1password.com/docs/ssh/agent/) to allow me to authorize use of an SSH key by tapping my FIDO2 authenticator (Yubikey). However in principle this could be used anywhere polkit is used.

The example rules file shows how this can be structured. Note that the example rules fall through on failure of the `pk-check-fido2` script. This means that if for any reason the script fails (e.g. key not tapped in time or not plugged in) the user may be given another chance to authenticate, in the "default" way (in my experience, this means using whatever is in /etc/pam.d/polkit-1).

This script does not provide any notification to the user that they must tap their key.
