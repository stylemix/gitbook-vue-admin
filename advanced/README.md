# Advanced

### Register boot function

Boot functions are run after plugins, but before root Vue application initialization. 

```javascript
import Admin from 'stylemix-vue-admin'

Admin.hooks.addAction('boot', '<your-ns>', () => {
    // your stuff
})
```

### 

