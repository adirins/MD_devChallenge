<template>
    <div class="location-radio-wrapper">
      <h3 class="location--title margin--bottom--15">LOCATION</h3>
      <div class="search-wrapper">
        <font-awesome-icon icon="globe-americas" class="globe-americas" />
        <input
          @change="onSubmit"
          placeholder="City, state, zip code or country"
          v-model="city"
          type="search"
          class="location--textinput"
        />
      </div>
      <div v-for="capital in radioButtonLocations" :key="capital" class="margin--bottom--15">
        <label :for="capital" class="radio--label">
          <input
            @change="onSubmit"
            v-model="city"
            type="radio"
            :id="capital"
            name="location"
            :value="capital"
          />
          {{capital}}
          </label>
          <br />
      </div>
      </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';

const LocationSelection = defineComponent({
  components: {
    FontAwesomeIcon,
  },
  props: {
  },
  emits: ['locationSubmitted'],
  data() {
    return {
      city: '',
      radioButtonLocations: ['London', 'Amsterdam', 'New York', 'Berlin', 'Zeist'],
    };
  },
  methods: {
    onSubmit() {
      this.$emit('locationSubmitted', this.city);
    },
  },
});

export default LocationSelection;
</script>

<style src="./LocationSelection.scss" lang="scss" scoped></style>
