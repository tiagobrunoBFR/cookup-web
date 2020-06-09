<template>
  <form-group :validator="v" :name="attributeError">
    <template slot-scope="{ attrs }">
      <v-text-field
        :label="label"
        :prepend-icon="icon"
        v-bind="attrs"
        v-model="name"
        :mask="mask"
        :color="color"
        :class="classInput"
        :return-masked-value="returnMaskedValue"
        :disabled="disabled"
        :single-line="singleLine"
        :outlined="outlined"
        :dark="dark"
        @input="v.$touch()"
        :type="type"
      >
        <template v-slot:label>
          <slot name="style"></slot>
        </template>
      </v-text-field>
    </template>
  </form-group>
</template>

<script>
import FormGroup from "@/components/vuelidate/FormGroup.vue";

export default {
  name: "BaseInput",
  comments: {
    FormGroup
  },
  props: {
    attributeError: {
      type: String,
      default: ""
    },
    classInput: {
      type: String,
      default: ""
    },
    color: {
      type: String,
      default: ""
    },
    type: {
      type: String,
      default: "text"
    },
    returnMaskedValue: {
      type: Boolean,
      default: false
    },
    dark: {
      type: Boolean,
      default: false
    },
    singleLine: {
      type: Boolean,
      default: false
    },

    outlined: {
      type: Boolean,
      default: false
    },

    disabled: {
      type: Boolean,
      default: false
    },

    mask: {
      type: String,
      default: ""
    },

    label: {
      type: String,
      default: ""
    },

    value: {
      type: String,
      default: ""
    },

    icon: {
      type: String,
      default: ""
    },

    v: {
      type: Object,
      required: false
    }
  },
  computed: {
    name: {
      get() {
        return this.value;
      },
      set(value) {
        this.$emit("input", value);
      }
    }
  }
};
</script>
