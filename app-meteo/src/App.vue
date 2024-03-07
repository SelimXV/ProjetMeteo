<script setup>
import SearchInput from "@/components/SearchInput.vue";

const places = ref([]);
const addPlace =(data) =>{
  places.value.push(data)
}
</script>

<template>
  <main>
    <!-- Date -->
    <div class="text-center mb-6">
      {{
        capitalizeDate(new Date().toLocaleDateString('fr-FR', {
          weekday: 'long',
          year: 'numeric',
          month: 'long',
          day: 'numeric'
        }))
      }}
    </div>

    <!-- Search -->
    <div>
      <SearchInput @place-data="addPlace" />
    </div>
    <!-- Weather Card -->
    <div>
      <p v-for = "place in places">
        {{ place.location.name }}

      </p>
    </div>
  </main>
</template>

<script>
export default {
  methods: {
    capitalizeDate(date) {
      return date.split(' ').map(word => word.charAt(0).toUpperCase() + word.slice(1)).join(' ');
    }
  }
}
</script>