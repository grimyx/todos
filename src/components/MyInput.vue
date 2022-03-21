<template>
  <div id="inputContainer">
    <p id="label">{{ this.label }}</p>
    <div id="inputBorder" :class="this.getStyles">
      <input
        :placeholder="placeholder"
        :disabled="this.disabled"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "MyInput",
  props: {
    label: {
      type: String,
      default: "",
    },
    placeholder: {
      type: String,
      default: "Enter some text",
    },
    error: Boolean,
    disabled: Boolean,
  },
  computed: {
    getStyles() {
      if (this.error) {
        return "color-error";
      }
      if (this.disabled) {
        return "color-disabled";
      }
      return "color-default";
    },
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --color: #828282;
  --hover-color: #333333;
  --focus-color: #2962ff;
}

input {
  border: none;
  outline: none;
  width: 100%;
  font-size: 14px;
}

#inputBorder:hover {
  --color: var(--hover-color);
}

#inputBorder:focus-within {
  --color: var(--focus-color);
}

#inputBorder {
  border: 2px solid var(--color);
  border-radius: 8px;
  padding: 18px 12px;
}

#label {
  color: var(--color);
}

.color-default {
  --color: #828282;
  --hover-color: #333333;
  --focus-color: #2962ff;
}

.color-error {
  --color: #d32f2f;
  --hover-color: #333333;
  --focus-color: #d32f2f;
}

.color-disabled {
  background-color: #f2f2f2;
  border: 1px solid #e0e0e0;
}

.color-disabled > input {
  background-color: #f2f2f2;
}

.color-disabled:hover {
}
</style>
