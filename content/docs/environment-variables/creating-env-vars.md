## Creating environment variables

Environment variables can be added on an organization, an application and a
pipeline. When running the pipeline environment variables will be merged from
these 3 targets into a unified list that is made available to your pipeline. In
case of duplicate names lower level ones override the higher level ones (for
instance `NODE_ENV` in pipeline will override `NODE_ENV` in an application).

Environment variables include text fields and ssh keys.

### <a name="text-env-var" class="anchor"></a>Creating a text environment variable

Creating a new environment variable is as simple as filling in a name, value and
hitting Save. The next pipeline run you will trigger now has the environment variable
available in its pipeline.

![Form to create new environment variable](/images/creating-env-vars_1.png)

If you check the `Protected` checkbox the value can only be read out in the
actual build and won't be made visible anywhere in the interface. Use this to
protect sensitive data such as passwords. [Read more on protected env vars
&rsaquo;](/docs/environment-variables/protected-variables.html)

#### How to use it

All environment variable that are available need to be used by adding a `$` character.
For instance a `SLACK_URL` environment variable  can be used in your
wercker.yml as `$SLACK_URL`.

Example how you to use a environment variable with our
[Slack notify step](https://app.wercker.com/applications/54d4a6c742494161430000f5/tab/details).

```yaml
build:
    after-steps:
        - slack-notifier:
            url: $SLACK_URL
            channel: notifications
            username: myamazingbotname
```

### <a name="ssh-env-var" class="anchor"></a>Creating a SSH key pair
environment variables

![+ Generate SSH Keys](/images/creating-env-vars_2.png)

Another common type of information used during deploys (but also during builds)
are SSH key pairs. Wercker can help you generate them for you and will only expose
the public part of the pair via the interface. Wercker will generate two
environment variables for you ending with `_PRIVATE` and `_PUBLIC`. The private
SSH key is used in the build and you should copy the public one to the
destination.

For instance if you created an `SSH key pair` to use as a bitbucket deploy key,
you may want to name the variable `DEPLOY_KEY`. During the pipeline
run you will now have two environment variables: `$DEPLOY_KEY_PRIVATE`
and `$DEPLOY_KEY_PUBLIC`.


