<template>
  <!-- When the card is clicked, flip to the other side -->
  <!-- https://github.com/andersponders/vue-flip-card/blob/master/FlipCard.vue -->
  <!-- Using click.native prevents the highlight/ripple effect -->
  <v-card class="mx-auto my-1 mb=10 pa-5" height="100%">
    <div
      v-bind:class="
        flipped ? 'flip-container flipped scroll' : 'flip-container'
      "
    >
      <div class="flipper">
        <!-- Front of the card -->
        <div class="front">
          <slot name="front"></slot>
        </div>

        <!-- Back of the card -->
        <div class="back">
          <slot name="back"></slot>
        </div>
      </div>
    </div>
  </v-card>
</template>

<script>
export default {
  name: 'FlipCard',
  computed: {
    flipped() {
      return this.$store.state.flipped
    },
  },
}
</script>

<style type="text/css" scoped>
.flip-container {
  -webkit-perspective: 1000;
  -moz-perspective: 1000;
  -o-perspective: 1000;
  perspective: 1000;
}
.flip-container {
  height: 100%;
}
.flipper {
  -moz-transform: perspective(1000px);
  -moz-transform-style: preserve-3d;
  position: relative;
}
.front,
.back {
  -webkit-backface-visibility: hidden;
  -moz-backface-visibility: hidden;
  -o-backface-visibility: hidden;
  backface-visibility: hidden;
  -webkit-transition: 0.6s;
  -webkit-transform-style: preserve-3d;
  -moz-transition: 0.6s;
  -moz-transform-style: preserve-3d;
  -o-transition: 0.6s;
  -o-transform-style: preserve-3d;
  -ms-transition: 0.6s;
  -ms-transform-style: preserve-3d;
  transition: 0.6s;
  transform-style: preserve-3d;
  top: 0;
  left: 0;
  width: 100%;
  margin: auto;
}
.back {
  -webkit-transform: rotateY(-180deg);
  -moz-transform: rotateY(-180deg);
  -o-transform: rotateY(-180deg);
  -ms-transform: rotateY(-180deg);
  transform: rotateY(-180deg);
  position: absolute;
}
.flip-container.flipped .back {
  -webkit-transform: rotateY(0deg);
  -moz-transform: rotateY(0deg);
  -o-transform: rotateY(0deg);
  -ms-transform: rotateY(0deg);
  transform: rotateY(0deg);
}
.flip-container.flipped .front {
  -webkit-transform: rotateY(180deg);
  -moz-transform: rotateY(180deg);
  -o-transform: rotateY(180deg);
  -ms-transform: rotateY(180deg);
  transform: rotateY(180deg);
}
.front {
  z-index: 2;
}
</style>
