# vue-google-signin-button

> A simple [Vue](https://vuejs.org) plugin to include a [Google sign-in button](https://developers.google.com/identity/sign-in/web/sign-in) into your web app.

<img src="https://github.com/phanan/vue-google-signin-button/raw/master/screenshot.png" width="677" alt="Screenshot">

## Install

This plugin can be installed as a module

``` bash
$ npm install vue-google-signin-button
```

or, if you're not in a modular environment, just include it as a `<script>`.

## Usage

> Important: `https://apis.google.com/js/api:client.js` must be included as a `<script>` in your web app, as this plugin depends on it.

Step 1: `import` and `use` the plugin if you're in a modular environment (you don't need this step otherwise, as the plugin will register itself).

``` js
import GSignInButton from 'vue-google-signin-button'
Vue.use(GSignInButton)
```

Step 2: Now you have a `g-signin-button` global component, ready for use. It's best to demonstrate the usage with an example:

``` html
<template>
  <g-signin-button
    :params="googleSignInParams"
    @success="onSignInSuccess"
    @error="onSignInError">
    Sign in with Google
  </g-signin-button>
</template>

<script>
export default {
  data () {
    return {
      /**
       * The Auth2 parameters, as seen on
       * https://developers.google.com/identity/sign-in/web/reference#gapiauth2initparams.
       * As the very least, a valid client_id must present.
       * @type {Object}
       */
      googleSignInParams: {
        client_id: 'YOUR_APP_CLIENT_ID.apps.googleusercontent.com'
      }
    }
  },
  methods: {
    onSignInSuccess (googleUser) {
      // `googleUser` is the GoogleUser object that represents the just-signed-in user.
      // See https://developers.google.com/identity/sign-in/web/reference#users
      const profile = googleUser.getBasicProfile() // etc etc
    },
    onSignInError (error) {
      // `error` contains any error occurred.
      console.log('OH NOES', error)
    }
  }
}
</script>

<style>
.g-signin-button {
  /* This is where you control how the button looks. Be creative! */
  display: inline-block;
  padding: 4px 8px;
  border-radius: 3px;
  background-color: #3c82f7;
  color: #fff;
  box-shadow: 0 3px 0 #0f69ff;
}
</style>
```

That's it!

> Looking for the [Facebook counterpart](https://github.com/phanan/vue-facebook-signin-button)?

## License

MIT © [Phan An](http://phanan.net)
