<template>
  <li class="item completed" :class="{ dark: darkMode }">
    <span>{{ todo.value }}</span>
    <div class="item-buttons">
      <button class="restore-button" @click="restoreTodo()">Restore</button>
      <button class="clear-button" @click="removeTodo()">Clear</button>
    </div>
  </li>
</template>
<script lang="ts">
import { PropType, Ref, defineComponent, inject } from "vue";

interface TODO {
  id: string;
  value: string;
}

export default defineComponent({
  props: {
    todo: {
      required: true,
      type: Object as PropType<TODO>,
    },
    restoreTodo: {
      required: true,
      type: Function as PropType<() => void>,
    },
    removeTodo: {
      required: true,
      type: Function as PropType<() => void>,
    },
  },
  setup() {
    const darkMode = inject<Ref<boolean>>("dark-mode");

    return {
      darkMode,
    };
  },
});
</script>
