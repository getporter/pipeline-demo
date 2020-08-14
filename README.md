# Bundle with Workflow

This is an example bundle that uses the [docker mixin](https://github.com/deislabs/porter-docker) along with a [GitHub workflow](https://docs.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow) to demonstrate how
you can use a workflow with your bundle. You can fork and clone this repository and then make pull requests
and merges to make the workflow run. For more details on how to use GitHub workflows with your Porter bundles, head to the [best practices page](https://porter.sh/best-practices/github-workflow/). 

# Contents

## porter.yaml

This is the porter manifest. See https://porter.sh/author-bundles/ for 
details on every field and how to configure your bundle. This is a required
file.

## helpers.sh

This is a bash script where you can place helper functions that you can call
from your porter.yaml file.

## README.md

This explains the files in this example bundle. It is not used by porter and
can be deleted.

## Dockerfile.tmpl

This is a template Dockerfile for the bundle's invocation image. You can
customize it to use different base images, install tools and copy configuration
files. Porter will use it as a template and append lines to it for the mixin and to set
the CMD appropriately for the CNAB specification. You can delete this file if you don't
need it.

Add the following line to **porter.yaml** to enable the Dockerfile template:

```yaml
dockerfile: Dockerfile.tmpl
```

By default, the Dockerfile template is disabled and Porter automatically copies
all of the files in the current directory into the bundle's invocation image. When
you use a custom Dockerfile template, you must manually copy files into the bundle
using COPY statements in the Dockerfile template.

## .gitignore

This is a default file that we provide to help remind you which files are
generated by Porter, and shouldn't be committed to source control. You can
delete it if you don't need it.

## .dockerignore

This is a default file that controls which files are copied into the bundle's
invocation image by default. You can delete it if you don't need it.