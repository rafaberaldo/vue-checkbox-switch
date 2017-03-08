# Vue Checkbox Switch

A simple Vue component for checkbox's switch style based on [vue-bulma/switch](https://github.com/vue-bulma/switch) and [this PR](https://github.com/jgthms/bulma/pull/544) on [Bulma](https://github.com/jgthms/bulma)

## Installation

**You don't need any dependencies** except Vuejs 2

Copy ``src/Switch.vue`` to your components folder

## Exemple

![Screenshot](https://github.com/rafaelpimpa/vue-checkbox-switch/blob/master/screenshot.png)

```vue
<template>
    <app-switch classes="is-warning" v-model="value" checked>Test</app-switch>
</template>

<script>
    import Switch from './components/Switch'

    export default {
        components: {
            'app-switch': Switch
        },
        data() {
            return {
                value: false,
                text: ''
            }
        },
        watch: {
            value(val) {
                this.text = val ? 'Yes' : 'No'
            }
        }
    }
</script>
```

---

> Twitter [@rafaelpimpa](https://twitter.com/rafaelpimpa)
