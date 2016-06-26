# Cloud Foundry Python Buildpack

A Cloud Foundry [buildpack](http://docs.cloudfoundry.org/buildpacks/) for Python based apps with SciPy/NumPy support.

**This buildpack incorporates SciPy support implemented in [Heroku SciPy buildpack](https://github.com/thenovices/heroku-buildpack-scipy) to standard [Cloudfoundry Python buildpack](https://github.com/cloudfoundry/python-buildpack). See [Heroku SciPy buildpack](https://github.com/thenovices/heroku-buildpack-scipy) README for details how to use it and which versions of SciPy/NumPy are supported.**

This buildpack supports running Django and Flask apps.

# Building the Buildpack

1. Make sure you have fetched submodules

  ```bash
  git submodule update --init
  ```

1. Get latest buildpack dependencies

  ```shell
  BUNDLE_GEMFILE=cf.Gemfile bundle
  ```

1. Build the buildpack

  ```shell
  BUNDLE_GEMFILE=cf.Gemfile bundle exec buildpack-packager [ --uncached | --cached ]
  ```

1. Use in Cloud Foundry

    Upload the buildpack to your Cloud Foundry and optionally specify it by name

    ```bash
    cf create-buildpack custom_python_buildpack python_buildpack-cached-custom.zip 1
    cf push my_app -b custom_python_buildpack
    ```

## Testing
Buildpacks use the [Machete](https://github.com/cloudfoundry/machete) framework for running integration tests.

To test a buildpack, run the following command from the buildpack's directory:

```
BUNDLE_GEMFILE=cf.Gemfile bundle exec buildpack-build
```

More options can be found on Machete's [Github page.](https://github.com/cloudfoundry/machete)

