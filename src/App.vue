<template>
  <div>
    <Beverage 
      :isIced="currentTemp === 'Cold'" 
      :selectedBase="selectedBase"
      :selectedCreamer="selectedCreamer"
      :selectedSyrup="selectedSyrup"
    />
    <ul>
      <li>
        <template v-for="temp in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :id="`r${temp}`"
              :value="temp"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>
      <li>
        <template v-for="base in bases" :key="base.id">
          <label>
            <input
              type="radio"
              name="base"
              :id="base.id"
              :value="base"
              v-model="selectedBase"
            />
            {{ base.name }}
          </label>
        </template>
      </li>
      <li>
        <template v-for="creamer in creamers" :key="creamer.id">
          <label>
            <input
              type="radio"
              name="creamer"
              :id="creamer.id"
              :value="creamer"
              v-model="selectedCreamer"
            />
            {{ creamer.name }}
          </label>
        </template>
      </li>
      <li>
        <template v-for="syrup in syrups" :key="syrup.id">
          <label>
            <input
              type="radio"
              name="syrup"
              :id="syrup.id"
              :value="syrup"
              v-model="selectedSyrup"
            />
            {{ syrup.name }}
          </label>
        </template>
      </li>
    </ul>
  </div>
</template>

<script>
import { ref } from "vue";
import Beverage from "./components/Beverage.vue";
import { temps, bases, creamers, syrups, currentTemp } from "./stores/beverage";

export default {
  components: {
    Beverage
  },
  setup() {
    // Set default selections
    const selectedBase = ref(bases.value[0]);
    const selectedCreamer = ref(creamers.value[0]);
    const selectedSyrup = ref(syrups.value[0]);

    return {
      temps,
      bases,
      creamers,
      syrups,
      currentTemp,
      selectedBase,
      selectedCreamer,
      selectedSyrup
    };
  }
};
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}
ul {
  list-style: none;
}
</style>