# Authentication

Vue Admin comes with built-in authentication module. It includes API implementation, Login, Forgot routes and views.

### How to use

```javascript
import Admin from 'stylemix-vue-admin'

Admin.useAuth()
```

### Utilities

#### Global computed props for components

* `{Boolean} $authenticated` - Authentication state
* `{Object} $account` - Authenticated user account data

###  List of all available options:

```javascript
import Admin from 'stylemix-vue-admin'

Admin.useAuth({

  // Whether to use forgot form feature.
  // Optional. Default: true
  withForgot: Boolean,

  // Whether to use http interceptor which redirects to login form
  // when Unauthenticated (401) response is catched
  // Optional. Default: true
  withHttpInterceptor: Boolean,

  // Function that return instance of custom API class.
  apiBuilder: Function,

  // Custom login form component.
  // Optional. Default: built-in LoginForm
  loginForm: Component,

  // Custom forgot password form component.
  // Optional. Default: built-in ForgotForm
  forgotForm: Component,
  
  // Prefix for local storage where auth information is stored.
  // Optional. Default: process.env.VUE_APP_STORAGE_PREFIX
  storagePrefix: String,

  // Route names for links
  routes: {
    login: 'login',
    forgot: 'forgot-password',
  },
})
```

### Default API

_Docs coming soon..._

### Custom API

Define your class:

```javascript
import { auth } from 'stylemix-vue-admin'

export default class CustomAuthApi extends auth.AuthApi {

  login(payload) {
    /** your implementation **/
  }

  refresh() {
    /** your implementation **/
  }

  forgot(email) {
    /** your implementation **/
  }
  
  account() {
    /** your implementation **/
  }
}
```

{% hint style="info" %}
Since your class extends existing AuthApi from admin package you can override just those methods that behave different.
{% endhint %}

Custom API classes methods should be convenient with the following specifications:

* `login(payload)` - login attempt
  * `payload` - is model data from LoginForm.vue. By default it contains the following:
    * `email`
    * `password`
  * return promise that resolves to object containing:
    * `token` - Auth token
    * `expires_in` - Number of seconds after which it expires
* `refresh()` - refresh current token
  * return promise that resolves to object containing:
    * `token` - Auth token
    * `expires_in` - Number of seconds after which it expires
* `forgot(email)` - login attempt
  * `email` - provided email from ForgotForm.vue.
  * return promise that resolves to object containing:
    * `message` - Some message to user
* `account()` - get authenticated account data
  * return promise that resolves to account data

### Available hooks

Refer to the [List of Auth hooks](advanced/list-available-hooks.md#auth-module).

