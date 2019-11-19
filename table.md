# Table

AdminTable component is extended version of [Vue Bootstrap Table](https://bootstrap-vue.js.org/docs/components/table). It has the following features:

* Requesting data from Api
* Pagination
* Search form
* Columns schema
* Row actions
* Bulk select and bulk actions

```markup
<template>
  <admin-table
    :base="base"
    :api-builder="apiBuilder"
    :columns="columns"
    />
</template>

<script>
import { AdminTable } from 'stylemix-vue-admin'
import BooksApi from './BooksApi'

export default {
  name: 'BookIndex',
  
  components: {
    AdminTable,
  },
  
  data() {
    return {
      base: 'books',
      apiBuilder() {
        return new BooksApi();
      },
      columns: [
        {
          key: 'id',
          label: 'ID',
          sortable: true,
        },
        {
          key: 'title',
          label: 'Title',
          sortable: true,
        },
        // define column fields here
      ],
    }
  }
}
</script>
```

### Events

`api-result` - after api result succeed and pagination updated. Api result passed as 1st arg.

### Column definition

Supports all options from [https://bootstrap-vue.js.org/docs/components/table/\#fields-as-an-array-of-objects](https://bootstrap-vue.js.org/docs/components/table/#fields-as-an-array-of-objects). Additionally:

### Row actions

By default table adds **edit** and **delete** actions for each row. You can add additional actions by providing callback, which accepts current row item:

```javascript
{
    rowActions(item) {
        return [
            {
                label: 'Custom action',
                variant: 'success', // BS button variants
                handler: ($event) => {
                  doSomethingWith(item)
                },
            },
            // to preserve built-in actions
            'edit',
            'delete',
        ]
    }
}
```

### Available table props

* `component`: Component name that is responsible for rendering the content. The component internally is injected the following way:

  ```markup
  <component
    v-if="column.component"
    :key="column.key"
    :is="column.component"
    :attribute="column.key"
    :config="column.config"
    :item="item"
  />
  ```

* `base: String` Base prefix for resource. Used to create Api wrapper \(if not provided\) with given base URI, builds route for edit link using ```${base}.edit``` format. You can overwrite both options.
* `apiBuilder: Function`  Function that returns Api wrapper instance. Read about [Api wrappers here](). 
* `columns: Array` List of [column definitions]()
* `pagination: Boolean` Enable/disable pagination. Default: `true`.
* `perPage: Integer` Items per page for pagination.
* `sortBy: String` Initial sort column.
* `sortDesc: Boolean` Initial sort descending or not.
* `searchFields: Array` List of fields for search bar. By default it is text field labelled "Search". To disable just pass `null`
* `searchData: Object` Initial search data.
* `onSearch: Function` Callback when search values are changed. Accepts search parameters as 1st arg.
* `beforeApiRequest: Function` Callback that is called before each api request. Accepts Api wrapper as 1st arg, current context as 2nd arg.  Context structure can be found [here](https://bootstrap-vue.js.org/docs/components/table/#using-items-provider-functions).
* `rowActions: Function` Callback function that return list of [button actions](table.md#row-actions) for single row
* `bulkActions: Function` Callback function that return list of buttons for selected rows
* `onEditItem: Function` Callback for edit row action. Accepts current item as first argument.
* `onDeleteItem: Function` Callback for delete row action. Accepts current item as first argument.
* `onBulkDelete: Function` Callback for delete bulk action. Accepts current selected items as first argument.



