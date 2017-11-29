<template>
    <label class="switch">
        <input :class="classes" type="checkbox" :checked="checked" :name="name" :disabled="disabled" v-model="checked">
        <span><slot></slot></span>
    </label>
</template>

<script>
    export default {
        props: {
            disabled: Boolean,
            classes: String,
            value: Boolean,
            name: String
        },
        data() {
            return {
                checked: null
            }
        },
        beforeMount() {
            this.checked = this.value
        },
        mounted() {
            this.$emit('input', this.checked)
        },
        watch: {
            checked(val) {
                this.$emit('input', val)
            },
            value (val) {
                this.checked = val
            }
        }
    }
</script>

<style lang="scss">
    label.switch {
    input[type="checkbox"] {
        display: none;
    &:checked {
    + span {
    &:before {
         background-color: rgba(#007FEB, 0.5);
     }
    &:after {
         background-color: #007FEB;
         transform: translate(80%, -50%);
     }
    }
    }
    + span {
          position: relative;
          display: inline-block;
          cursor: pointer;
          font-weight: 500;
          text-align: left;
          margin: 0px;
          padding: 0px 44px;
    &:before,
    &:after {
         content: '';
         cursor: pointer;
         position: absolute;
         margin: 0;
         outline: 0;
         top: 50%;
         transform: translate(0, -50%);
         transition: all 200ms ease-out;
     }
    &:before {
         left: 1px;
         width: 34px;
         height: 14px;
         background-color: rgba(0, 0, 0, 0.2);
         border-radius: 8px;
     }
    &:after {
         left: 0;
         width: 20px;
         height: 20px;
         background-color: rgba(0, 0, 0, 0.5);
         border-radius: 50%;
         box-shadow: 0 3px 1px -2px rgba(0, 0, 0, .14), 0 2px 2px 0 rgba(0, 0, 0, .098), 0 1px 5px 0 rgba(0, 0, 0, .084);
     }
    }
    &:checked + span &:after {
         transform: translate(80%, -50%);
     }
    }
    }
</style>
