<template lang="">
  <div>
    <h2>Let's Check This {{ msg }} and {{ secondMsg }}</h2>
  </div>
</template>
<script>
export default {
  name: "TryThis",

  props: ["msg", "secondMsg"],
};
</script>
<style lang=""></style>
