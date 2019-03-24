<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <h1>Built-in Directives</h1>
        <p v-text="'Here is some text'"></p>
        <p v-html="'<strong> Here is some strong text</strong>'"></p>
      </div>
    </div>
    <hr>
    <hr>
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <h1>User Created Directives</h1>
        <!-- Directive with no default value -->
        <p v-highlight>Background Color has been set by Directive</p>
        <!-- Passing a value to a Directive -->
        <p v-highlight="'green'">
          Background Color has been set by
          Directive
        </p>
        <!-- Passing a argument with value -->
        <p v-highlight:background.delayed="'green'">Background Color has been set by</p>
        <p v-local-higlight:background.delayed="'yellow'">Background Color has been set by</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  directives: {
    "local-higlight": {
      bind(el, binding, vnode) {
        var delay = 0;
        if (binding.modifiers["delayed"]) {
          delay = 3000;
        }
        setTimeout(() => {
          if (binding.arg === "background") {
            el.style.backgroundColor = binding.value;
          } else {
            el.style.color = binding.value;
          }
        }, delay);
      }
    }
  }
};
</script>

<style>
</style>
