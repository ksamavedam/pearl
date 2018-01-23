# Pearl
<p align="center"><img src="pearl.png" width="100"/></p>

Pearl is a lightweight framework for making Google Hangouts bots. It is structured as a set of plugins, which either run passively or respond to commands. For example, the `hello` plugin replies with a custom greeting whenever a user sends `/pearl hello`. Pearl only comes with a few sample plugins, but it's incredibly easy to make custom ones. Pearl is built on [hangups](https://github.com/tdryer/hangups).

# Prerequisites
Pearl requires a Gmail account, which you must independently create. Pearl does not support accounts with two factor authentication. Once you've made an account, add it to conversations that you would like it to interact with.

In the `pearl` directory, create a new directory called `private`. Inside, create two files, `auth.json` and `token.txt`. Write the following to `auth.json`, but with your own credentials. If you have two-factor authentication enabled, include it in the `secret` field; otherwise, leave it as an empty string.
```json
{
	"email": "pearl@gmail.com",
	"password": "pearl",
	"secret": "",
	"token": "private/token.txt"
}
```

# Running
All it takes to get Pearl up and running is `python3 pearl.py`. For a permanent bot, we recommend that you build and run a Docker instance from the given `Dockerfile`. On some servers, Google may block login requests that Pearl makes. In these situations, first run Pearl on your home computer; you should then see a session cookie stored in `token.txt`. With the session cookie, you will be able to connect to Hangouts on any server.

In a conversation with Pearl, try sending `/pearl help`. Pearl should respond with a set of available commands.

# Customization
Generally speaking, `pearl.py` should not be modified. Instead, customize Pearl by making new plugins and adding them in `config.json`. An important detail to note is that you can run several Pearl instances on the same account. For more specialized bots, visit <https://github.com/pearl>.