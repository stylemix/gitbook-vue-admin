# Configuration

### Logo

Set logo in nav-bar. Accepts any url.

{% code title="main.js" %}
```javascript
import Admin from 'stylemix-vue-admin'
import logo from '@/assets/images/logo.png'

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

