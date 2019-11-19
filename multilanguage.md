# Multilanguage

Admin application includes i18n in core. It uses [vue-i18n](https://kazupon.github.io/vue-i18n/) package.

You can use any of this features to translate strings:

```javascript
// In *.vue components
this.$t('message.hello')
this.$tc('cars', 1)

// In any global scope
Vue.$t('message.hello')
Vue.$tc('cars', 1)
```

```javascript
<template>
    <p>{{ $t('message.hello') }}</p>
    <p>{{ $tc('cars', 1) }}</p>
</template>
```

### Reactivity for strings in objects

Often when string property inside the object should be translatable \(i.e. menu items, table columns\). You usually do the following:

```markup
<template>
    <p>{{ item.label }}</p>
</template>

<script>
export default {
    data() {
        return {
            item: {
                label: this.$t('my.item.label'),
            },
        }
    }
}
</script>
```

But after switching current language, that object will not be translated until you run its initialization again.

To make it translation reactive just pass the following hint to its `label`, and use `labelTranslated` prop for translated string:

```markup
<template>
  <label>{{ item.labelTranslated }}</label>
  <div>{{ item.descTranslated }}</div>
</template>
<script>
import { utils } from 'stylemix-vue-admin'

export default {
  data() {
    return {
      item: utils.addTranslators({
        label: '$t.my.item.label',
        desc: '$t.my.item.desc',
      }, ['label', 'desc']),
    }
  }
}
</script>
```

### Components supporting reactive translations

#### Navigation menu items

When defining [navigation menu items](modules.md#register-navigation-menu-items):

```javascript
Admin.nav.push({
  label: '$t.nav.item1',
  // ...
})

Admin.accountNav.push({
  label: '$t.account.item1',
  // ...
})

// and all other menu items
```

#### AdminTable columns

When defining [AdminTable columns](table.md#column-definition), [AdminTable row actions](table.md#row-actions), AdminTable bulk actions:

```javascript
columns: [
  {
    key: 'email',
    label: '$t.user.email',
  },
],
rowActions: [
  {
    label: '$t.user.edit',
  }
],
bulkActions: [
  {
    label: '$t.user.delete_all',
  }
],

```

