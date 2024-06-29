<template>
  <div>
    {{ envFile }} / {{ env}}
  </div>
</template>
<script lang="ts" setup>
const config = useRuntimeConfig().public
const { envFile, env } = config
</script>
