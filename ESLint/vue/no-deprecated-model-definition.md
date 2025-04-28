Pattern: Deprecated `model` definition

Issue: -

## Description

This rule reports use of the component `model` option, which has been deprecated in Vue.js 3.0.0+.

```vue
<script>
export default defineComponent({
  model: {
    prop: 'my-value',
    event: 'input'
  }
})
</script>

```


## Further Reading

* [eslint-plugin-vue - no-deprecated-model-definition ](https://eslint.vuejs.org/rules/no-deprecated-model-definition.html)
