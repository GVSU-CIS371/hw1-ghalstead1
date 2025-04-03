<template>
  <Mug>
    <Cold v-if="isIced" />
    <Hot v-else />
    <Contents>
      <template v-slot:top>
        <Creamer 
          v-if="showCreamer"
          :creamerColor="selectedCreamer.color" 
        />
      </template>
      <template v-slot:mid>
        <Syrup 
          v-if="showSyrup" 
          :syrupColor="selectedSyrup.color" 
        />
      </template>
      <template v-slot:bottom>
        <Base :baseColor="selectedBase.color" />
      </template>
    </Contents>
  </Mug>
</template>

<script>
import Contents from "./Contents.vue";
import Mug from "./Mug.vue";
import Syrup from "./Syrup.vue";
import Base from "./Base.vue";
import Creamer from "./Creamer.vue";
import Hot from "./Hot.vue";
import Cold from "./Cold.vue";

export default {
  components: {
    Contents,
    Mug,
    Syrup,
    Base,
    Creamer,
    Hot,
    Cold
  },
  props: {
    isIced: Boolean,
    selectedBase: Object,
    selectedCreamer: Object,
    selectedSyrup: Object
  },
  computed: {
    isNoCreamer() {
      return this.selectedCreamer?.name === "No Cream";
    },
    isNoSyrup() {
      return this.selectedSyrup?.name === "No Syrup";
    },
    showCreamer() {
      return !this.isNoCreamer;
    },
    showSyrup() {
      return !this.isNoSyrup;
    }
  }
}
</script>