# Simple GHCR example

Demonstrates how a simple workflow **with no additional configuration/passwords/tokens** is sufficient to publish Docker images to GitHub Container Registry.

Based primarily on the [official instrutions](https://docs.github.com/en/packages/managing-github-packages-using-github-actions-workflows/publishing-and-installing-a-package-with-github-actions) which are likely more up-to-date.

## Steps

1. Ensure that you have a `Dockerfile` in the root of the repo, and a workflow file that has been pushed to GitHub.
2. The provided workflow is triggered only by "workflow dispatch". To start a build:
   1. Go to the main page of your repo.
   2. Click on the "Actions" tab
   3. Select "Build Docker image and publish to GHCR" on the left
   4. Click the grey "Run workflow" button
   5. With the desired branch selected, click the green "Run workflow" button.

The workflow is extremely basic so you will probably want to adapt it to your needs.
The following suggestions are beyond the scope of this simple demonstration:

* Add other build triggers besides "workflow dispatch" by modifying the `on` section.
* Customize the name of the image. (Currently it's the repo name with `-image` as a suffix.)
* Generate tags and other metadata with [docker/metadata-action](https://github.com/docker/metadata-action)
* Enable caching of build layers.
* Set up QEMU if you want to build images for other architectures.
* Test the image before pushing it.
* Push conditionally only on release or tag events, but still build and test on every push.
