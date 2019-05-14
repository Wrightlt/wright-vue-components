<template>
  <div class="usage">
    【1 rows-text-dot】：<rows-text-dot></rows-text-dot>
  </div>
</template>

<script>
  import RowsTextDot from '@/components/RowsTextDot'
  export default {
    name: 'UsageView',
    components: {RowsTextDot}
  }
</script>

<style lang="scss" scoped>
  .usage {
    text-align: left;
  }
</style>
