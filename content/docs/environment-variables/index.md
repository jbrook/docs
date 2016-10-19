## Environment variables

What if you have an API key you need during a pipeline run? This is
information that is either unique for each server you want to deploy to or may
be too sensitive to store in the repository. Wercker supports a number of ways
to store and expose this data as environment variables.

[Read more about creating env vars &rsaquo;](/docs/environment-variables/creating-env-vars.html)

### Organization-level environment variables

When you have an organization you can create environment variables on that
organization from the organization settings. These environment variables will
be available to all projects and pipelines in that organization. These can be
used to set some global settings that should apply to everything under and
organization, such as an ssh key to fetch private Github repositories. Keep in
mind that public projects under the organization will also have access to these
variables.

### Application-level environment variables

The second set of variables are specific to the application. All runs under
this application will receive these environment variables. This can be useful
for setting AWS secrets, Docker credentials or anything else that several
pipelines in the application might use.

In the case of an identical name, an environment variable defined on an
application will override an environment variable defined on the organization.

### Pipeline-level environment variables

The third set of variables are specific to pipelines in a
[workflow](/docs/workflows/index.html). These are made available to each
pipeline run. Typically, these are used to store information such as hostnames,
ssh-keys, passwords and more. 

The pipeline environment variable will override environment variables with the
same name on the organization or the application.

### Available environment variables

You can also use a [script step](/learn/steps/introduction.html) and use the `env`
command to see the full list of all variables at that moment during the pipeline execution.
This is convenient since there are reasons why the environment variables step does
not show all environment variables available during the pipeline run.

```yaml
- script:
    code: |
        env
```

Keep in mind that this will list all variables — including protected ones — so
you might not want to do this on a public project.

[See the complete list of available env vars &rsaquo;](/docs/environment-variables/available-env-vars.html)
