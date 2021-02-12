<template>
  <div class="home">
    
    <div>
      <b-overlay :show="show" rounded="sm">
        <b-card title="Card with overlay" :aria-hidden="show ? 'true' : null">
          <b-card-text
            >Laborum consequat non elit enim exercitation cillum.</b-card-text
          >
          <b-card-text>Click the button to toggle the overlay:</b-card-text>
          <b-button :disabled="show" variant="primary" @click="show = true">
            Show overlay
          </b-button>
        </b-card>
      </b-overlay>
      <!-- added this -->
      <b-button class="mt-3" @click="show = !show">Toggle overlay</b-button>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  components: {
  
  },
  data() {
    return {
      show: false,
    };
  },
};
</script>
