<template>
<div>
    <button  @click="toggle" :class="{checked:value}">
        <span :class="{checked:value}"></span>
    </button>
    {{value}}
</div>
</template>

<script lang="ts">
import {
    reactive,
    onMounted,
    ref,

} from 'vue';

export default {
    props: {
        value:{
            default:true,
            type:Boolean
        }
    },
    setup(props, context) {
        let x = ref(props.value);
        const toggle = () => {
            context.emit('update:value',!props.value)
        }
        const a = reactive({
            abc: 123
        })
        onMounted(() => {
            a.abc = 3333
        })
        console.log(123);

        return {
            a,
            toggle,
            x
        }
    }
}
</script>

<style lang="scss">
$h:22px;
$h2:$h - 4px;

.set {
    color: red;
    background-attachment: fixed;
}

button {
    position: relative;
    width: 2*$h;
    height: $h;
    line-height: $h;
    border-radius: $h/2;
    outline: none;
    border: none;
    background-color: grey;
    &.checked{
        background-color: blue;
    }
    span {
        display: inline-block;
        position: absolute;
        // left:1px;
        left: calc(100% - #{$h2});
        top: 2px;
        height: $h2;
        line-height: $h2;
        width: $h2;
        background-color: #fff;
        border-radius: 50%;
        transition: left 250ms ease;

        &.checked {
            left: 1px;

        }
    }

}
</style>
