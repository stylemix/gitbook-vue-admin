# Modules

### Register routes

```javascript
import Admin from 'stylemix-vue-admin'

const base = 'books'

Admin.router.addRoutes([
  {
    path: `/${base}`,
    name: `${base}.index`,
    component: () => import('./Index.vue'),
    meta: {
      auth: true,
    },
  },
  {
    path: `/${base}/create`,
    name: `${base}.create`,
    component: () => import('./Create.vue'),
    meta: {
      auth: true,
    },
  },
])
```

{% hint style="info" %}
Expression `component: () => import('./Create.vue')` above makes route components load in **lazy** mode. Read more about [Lazy Loading Routes](https://router.vuejs.org/guide/advanced/lazy-loading.html).
{% endhint %}

Refer to [Route object specification](https://router.vuejs.org/api/#route-object-properties) for details.

#### Meta

| Property | Type | Description |
| :--- | :--- | :--- |
| `auth` | `Boolean` | Flag that route requires authentication |
| `guest` | `Boolean` | Flag that route available only for unauthenticated |

### Register navigation menu items

```javascript
import Admin from 'stylemix-vue-admin'

const base = 'books'

Admin.nav.push({
  label: 'Attributes',
  id: `${base}.index`,
  route: {
    name: `${base}.index`,
  },
  icon: 'icon-cog',
})
```

#### Menu item properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `label` | `String` | Label of menu item |
| `route` | `String|Object` | Route identifier for Vue's router link. More info about [Router format](https://router.vuejs.org/api/#to). |
| `id` | `String` | Optional unique id of menu item. It used for Vue's internal foreach loop as **:key** prop for optimize list rendering. I you don't provide it, default will be generated. See [https://vuejs.org/v2/guide/list.html\#key](https://vuejs.org/v2/guide/list.html#key) for more information. |
| `order` | `Number` | \(Optional\) Order number by which menu items will be sorted |
| `icon` | `String` | \(Optional\) Icon class |
| `header` | `String` | \(Optional\) Header text by which menu items will be grouped |
| `onClick` | `Function` | \(Optional\) callback function, triggered when menu item clicked. Clicked menu item itself passed as an argument. If item contain's child menu items, item's  expand state toggled, in that case item's **onClick** property ignored and default expand/close behavior used |
| `children` | `Array` | \(Optional\) Sub-menu items. Only one level depth child items will be rendered, another sub items are ignored. Each child item must contain properties above-mentioned. |

