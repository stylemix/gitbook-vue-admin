# Page header

### Title & actions

To set page heading and actions to page header:

{% tabs %}
{% tab title="Books.vue" %}
```javascript
import { HasPageHeader } from 'stylemix-vue-admin'

export default {
  
  mixins: [HasPageHeader],

  pageTitle() {
    return this.$t('dynamic_attributes.edit')
  },

  
  pageActions() {
    return [
      {
        id: 'invoices',
        label: 'Invoices',
        icon: 'icon-calculator',
        route: {
          name: 'invoices.index',
        }
      }
    ]
  },
}
```
{% endtab %}
{% endtabs %}

### Custom page header

When defining a route for some page, modify `components` declaration as follows:

{% tabs %}
{% tab title="module.js" %}
```javascript
Admin.router.addRoutes([
  {
    // route props...
    components: {
      header: () => import('./BooksHeader.vue'),
      default: () => import('./Books.vue'),
    },
  },
])
```
{% endtab %}
{% endtabs %}

 And create your custom header component:

{% tabs %}
{% tab title="BookHeader.vue" %}
```markup
<template>
  <admin-page-header />
</template>
<script>
import { AdminPageHeader } from 'stylemix-vue-admin'

export default {
  name: 'BooksHeader',
  components: {
    AdminPageHeader,
  },
}
</script>
```
{% endtab %}
{% endtabs %}

###  PageHeader reference

| Prop | Type | Description |
| :--- | :--- | :--- |
| `title` | `String` | Header title |
| `titleSmall` | `String` | Header small sub-title |
| `actions` | `MenuItem[]` | Action buttons |
| `showBack` | `Boolean` | Show back button |
| `@click-back` | Event | When back button clicked |

