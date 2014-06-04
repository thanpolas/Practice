# Heroku Node.js Hands On


## Get Setup with Heroku

1. [Signup](https://signup.heroku.com/signup/dc) for a Heroku account.
1. Install the [Heroku Toolbelt](https://toolbelt.heroku.com/)
1. Login using the CLI

```shell
heroku login
```

## Prepare a Node.js Project for Heroku

### Heroku and Random Listening Ports

Due to the architecture or Heroku's Dynos the port number that the requests will be sent to is dynamically selected. Each new Dyno instance propagates the port number in the environment variable `PORT`, this is how to fetch it from within your Node.js Application:

```js
var port = Number(process.env.PORT || 5000);
```

### Create your Heroku application

* Through the heroku manage panel (preferred)
* From the command line: `heroku create`

#### The Success modal

![The success view](http://than.pol.as/Vtph/Screen%20Shot%202014-06-04%20at%202.47.26%20PM.png)

#### Get the git repository

In our case `git@heroku.com:stub-test.git`, then:

Add it as a remote to your current project:

```shell
git remote add heroku git@heroku.com:stub-test.git
```

#### Setup Heroku boot

In order for Heroku to know how it should boot up your application you need to create the `Procfile` at your project's root folder, here is a sample `Procfile`:

```
web: node .
```

#### First Deployment

...and every other deployment happens like that:

```shell
git push heroku master
```

#### Power up your application

This is required to kickstart your Heroku application, use only once.

```shell
heroku ps:scale web=1
```

## Tips & Tricks

### View logs

```shell
heroku logs --tail
```

### Setup Environment Variables

```shell
heroku config:set NODE_ENV=heroku_staging
```

### Export Sensitive Data to Heroku

Check out [this Gist](https://gist.github.com/thanpolas/5bcb42e0ae1f34e6dc56) on how to export sensitive data (passwords, keys, tokens) to Heroku without having them tracked in your repository.



