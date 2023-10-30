<script setup lang="ts">
import { ref, watch } from 'vue';

const todo = ref('');

type Drazen = {
  sir: string;
  mast: number;
};

async function submit() {
  await new Promise((r) => setTimeout(r, 1000));
  alert('Submitted! 🎉');
}

watch(todo, (newQuestion, oldQuestion) => {
  console.log(newQuestion, oldQuestion);
});
</script>

<template>
  <div class="your-first-form">
    <FormKit type="form">
      <FormKit
        type="text"
        label="Your todo"
        label-class="$reset only-my-class"
        help="Add a todo to your
      todo list"
        :delay="1000"
        validation="required|length:5|email"
        validation-visibility="live"
        v-model="todo"
        :help-class="{
          'add-this-class': true,
          'dont-add-this': false,
        }"
      />

      <FormKit
        type="date"
        value="2011-01-01"
        label="Birthday"
        help="Enter your birth day"
        validation="required|date_before:2010-01-01"
        validation-visibility="live"
      />
    </FormKit>
  </div>
</template>

<style>
.only-my-class {
  color: blue;
}

.your-first-form {
  width: calc(100% - 2em);
  max-width: 480px;
  box-sizing: border-box;
  padding: 2em;
  box-shadow: 0 0 1em rgba(0, 0, 0, 0.1);
  border-radius: 0.5em;
  margin: 4em auto;
}

pre {
  background-color: rgba(0, 100, 250, 0.1);
  padding: 1em;
}
</style>
