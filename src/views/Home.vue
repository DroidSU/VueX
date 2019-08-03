<template>
  <div class="home">
    <Character />
  </div>
</template>

<script>
// @ is an alias to /src
import Character from "@/components/Characters.vue";

export default {
  name: "home",
  components: {
    Character
  }
};
</script>
