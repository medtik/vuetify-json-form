<template>
    <v-text-field
            type="number"

            v-model="model[name]"
            @input="formatValue($event)"
            @blur="validate()"
            :error-messages="allErrors"

            :label="$intl.translate(display.title)"

            :suffix="$intl.translate(display.suffix)"
            :prefix="$intl.translate(display.prefix)"
            :prepend-icon="$controlIcon(display.prependIcon)"
            :append-icon="$controlIcon(display.appendIcon)"
            :hint="$intl.translate(display.hint)"
            :placeholder="$intl.translate(display.placeholder)"
            :mask="display.mask"

            :clearable="display.clearable"
            :box="display.box"
            :counter="display.counter ? config.maxLength || false : false"

            :required="config.required"
            :step="config.multipleOf || 1"
            :min="config.minimum"
            :max="config.maximum"
    ></v-text-field>
</template>
<script>
    import {JsonFormElementMixin} from "@aquarelle/json-form";

    export default {
        name: 'number-control',
        mixins: [JsonFormElementMixin],
        methods: {
            formatValue(val)
            {
                this.$set(this.model, this.name, Number(val));
            }
        }
    }
</script>