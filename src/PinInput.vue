<template>
    <input type="text" ref="input" class="masked" :value="this.value" @input="valueChanged" @keypress="restrictAlphabets">
</template>
<script>
    export default {
        props: {
            value: {
                required: false,
            },
            type: {
                required: false,
                default: 'number',
                type: String,
                validator(value)
                {
                    return ['string','number'].indexOf(value) !== -1;
                }
            }
        },
        install(Vue)
        {
            Vue.component('pin-input', this);
        },
        methods: {
            restrictAlphabets(e)
            {
                if(this.type=='string') return true;

                let x=e.which||e.keycode;
                if(x>=48 && x<=57)
                    return true;
                else
                    e.preventDefault();
            },
            focus()
            {
                this.$refs.input.focus();
            },
            valueChanged(e)
            {
                let formattedData = this.formatData(e.target.value, this.type)
                this.$emit('input', formattedData);
            },
            formatData(data, type)
            {
                if(data.length > 0)
                    return type == 'number' ? parseInt(data) : data
                else
                    return null;
            }
        }
    }
</script>
<style>
    .masked {
        -webkit-text-security: disc; 
    }
</style>

