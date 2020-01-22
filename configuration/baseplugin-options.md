# BasePlugin options

To hook into base plugin options use the following filter:

```javascript
Admin.hooks.addFilter('base-plugin-options', '<your-namespace>', options => {
  // customize options
  return options
})
```

