<template>
  <iframe :srcdoc="results" class="frame" id="frame"></iframe>
</template>

<script>
export default {
  props: {
    results: [],
  },
};
</script>

<style>
.frame {
  width: 100%;
  height: 600px;
}
</style>