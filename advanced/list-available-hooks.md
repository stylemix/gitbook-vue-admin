# List available hooks

### Root Vue instance

| Key | Type | Description |
| :--- | :--- | :--- |
| mixins | filter | Array of mixins [https://vuejs.org/v2/api/\#mixins](https://vuejs.org/v2/api/#mixins) |
| beforeCreate | action | Lifecycle [https://vuejs.org/v2/api/\#beforeCreate](https://vuejs.org/v2/api/#beforeCreate) |
| created | action | Lifecycle [https://vuejs.org/v2/api/\#created](https://vuejs.org/v2/api/#created) |
| beforeMount | action | Lifecycle [https://vuejs.org/v2/api/\#beforeMount](https://vuejs.org/v2/api/#beforeMount) |
| mounted | action | Lifecycle [https://vuejs.org/v2/api/\#mounted](https://vuejs.org/v2/api/#mounted) |
| beforeUpdate | action | Lifecycle [https://vuejs.org/v2/api/\#beforeUpdate](https://vuejs.org/v2/api/#beforeUpdate) |
| updated | action | Lifecycle [https://vuejs.org/v2/api/\#updated](https://vuejs.org/v2/api/#updated) |
| beforeDestroy | action | Lifecycle [https://vuejs.org/v2/api/\#beforeDestroy](https://vuejs.org/v2/api/#beforeDestroy) |
| destroyed | action | Lifecycle [https://vuejs.org/v2/api/\#destroyed](https://vuejs.org/v2/api/#destroyed) |

### Auth module

| Key | Type | Description |
| :--- | :--- | :--- |
| authenticated | action | After user authenticated and account data loaded |
| logout | action | On logout before any state commits |
| logged-out | action | On logout after state commits |

