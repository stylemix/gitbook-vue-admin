# Configuration

### Brand Name

Set brand name for nav-bar

{% code title="main.js" %}
```javascript
import Admin from 'stylemix-vue-admin'

Admin.config.setBrandName('Cool Dashboard')
```
{% endcode %}

### Logo

Set logo in nav-bar. Accepts any url.

{% code title="main.js" %}
```javascript
import Admin from 'stylemix-vue-admin'
import logo from './assets/images/logo.png'

Admin.config.setLogo(logo)
```
{% endcode %}

### Default route

Default route is used to redirect user after authentication, or initial page load.

{% code title="main.js" %}
```javascript
import Admin from 'stylemix-vue-admin'

// Format compatible for Router.push()
Admin.config.setDefaultRoute({
    name: 'dashboard'
})
```
{% endcode %}

### Environment variables

`VUE_APP_API_LOCATION` - API base url

`VUE_APP_STORAGE_PREFIX` - prefix for local storage

### Hooks

To tweak different parts of Admin features use hooks that are build using cool package [@wordpress/hooks](https://www.npmjs.com/package/@wordpress/hooks). `Admin.hooks` is instance of hooks object:

```javascript
Admin.hooks.addAction()
Admin.hooks.removeAction()
Admin.hooks.addFilter()
Admin.hooks.removeFilter()
```

{% page-ref page="../advanced/list-available-hooks.md" %}



