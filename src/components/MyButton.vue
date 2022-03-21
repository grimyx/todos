<template>
  <div :class="getButtonStyles" :id="disabled ? 'disabled' : variant">
    <span class="material-icons" v-if="startIcon">{{ startIcon }}</span>
    <span>
      <slot></slot>
    </span>
    <span class="material-icons" v-if="endIcon">{{ endIcon }}</span>
  </div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
  variant: {
    type: String,
    default: "default",
  },
  size: {
    type: String,
    default: "sm",
  },
  color: {
    type: String,
  },
  disabled: Boolean,
  startIcon: String,
  endIcon: String
});

// will calculate needed styles based on the properties
const getButtonStyles = computed(() => {
  // holds array of styles for button
  const res = [];

  // check if disabled option is enabled and add styles for disabled button
  if (props.disabled) {
    if (props.variant === "text") {
      res.push("color-disabled-text");
    } else {
      res.push("color-disabled");
    }
  } else { // button is not disabled

    // check if color option is set or not
    if (props.color) {
      // if color is set add color class to result array
      res.push(`color-${props.color}`);
    } else { // if not use default colors based on button variant
      switch (props.variant) {
        case 'default':
          res.push('color-default');
          break;
        case 'outline':
        case 'text':
          res.push('color-primary');
          break;
      }
    }
  }

  // add size class to styles array
  res.push(`size-${props.size}`);

  return res.join(" ");
});


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
:root {
  --bg-color: #e0e0e0;
  --color: black;
  --focus-color: #aeaeae;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

div {
  border-radius: 6px;
  cursor: default;
  display: flex;
  align-content: center;
  width: fit-content;
  font-weight: 700;
}

span {
  padding: 0 3px;
}

#disabled {
  color: var(--color);
  background: var(--bg-color);
}

#default {
  color: var(--color);
  background: var(--bg-color);
}

#default:hover,
:focus {
  background: var(--focus-color);
}

#outline {
  border: 1px solid var(--bg-color);
  color: var(--bg-color);
  background: white;
}

#outline:hover,
:focus {
  background: var(--bg-color);
  color: white;
}

#text {
  border: none;
  background: white;
  color: var(--bg-color);
}

#text:hover,
:focus {
  background: var(--bg-color);
  color: white;
}

.color-default {
  --bg-color: #e0e0e0;
  --color: black;
  --focus-color: #aeaeae;
}

.color-primary {
  --bg-color: #2962ff;
  --color: white;
  --focus-color: #0039cb;
}

.color-secondary {
  --color: white;
  --bg-color: #455a64;
  --focus-color: #1c313a;
}

.color-danger {
  --color: white;
  --bg-color: #d32f2f;
  --focus-color: #9a0007;
}

.color-disabled {
  --color: #9e9e9e;
  --bg-color: #e0e0e0;
}

.color-disabled-text {
  --color: #9e9e9e;
  --bg-color: white;
}

.size-sm {
  padding: 6px 12px;
}

.size-md {
  padding: 10px 16px;
}

.size-lg {
  padding: 14px 22px;
}
</style>
