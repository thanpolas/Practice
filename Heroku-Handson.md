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

### Create your application

* Through the heroku manage panel (preferred)
* From the command line: `heroku create`

![The success view](http://than.pol.as/Vtph/Screen%20Shot%202014-06-04%20at%202.47.26%20PM.png)


