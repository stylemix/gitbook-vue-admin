# Advanced

### Register bootstrapper function

Bootstrapper functions are run after plugins, but before root Vue application initialization. 

```javascript
import Admin from 'stylemix-vue-admin'

Admin.registerBootstraper(() => {
    // your stuff
})
```

### Register ready-function

Ready-functions are run after root Vue application is created. As argument `$app` Vue instance is passed.

```javascript
import Admin from 'stylemix-vue-admin'

Admin.registerReady($app => {
    // your stuff
})
```

