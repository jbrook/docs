## Protected variables

Protected variables functionality was added to limit the exposure of sensitive
information via the interface. The behavior of the variables during pipeline runs
(builds/deploys) are the same as other variables, but with the following exceptions:

Protected variables are not displayed/logged during the setup environment step
values are not shown in the settings tab and can only be set, not read back.
The behavior is optional for regular environment variables, SSH keys generated
by Wercker will always mark the private key as protected.

Once a protected environment value has been created it cannot be read from the
interface. The value can be overwritten by specifying a new value. The name can
also be changed in which case the value is kept as it was before but the name
is updated. This is useful if you want to change the name but don't have access
to the original value.

[Read more on creating env vars &rsaquo;](/docs/environment-variables/creating-env-vars.html)
