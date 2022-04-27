<template>
  <div class="header">
    <div class="friends">
      <!-- moody buddy -->
      <div class="moody-pot">
        <Theme />
      </div>

      <!-- daisy buddy -->
      <div class="daisy-pot">
        <div class="daisy-buddy">
          <div class="daisy-head">
            <div class="daisy-eye left">
              <span></span>
            </div>
            <div class="daisy-eye right">
              <span></span>
            </div>
          </div>
        </div>

        <!-- daisy buddy speech bubble -->
        <span class="daisy-bubble">{{ daisy }}</span>
      </div>

      <!-- tulip-dude -->
      <div class="tulip-pot">
        <div class="tulip-dude">
          <div class="tulip-head">
            <div class="tulip-petal left"></div>
            <div class="tulip-petal middle"></div>
            <div class="tulip-petal right"></div>
            <div class="tulip-eye left">
              <span></span>
            </div>
            <div class="tulip-eye right">
              <span></span>
            </div>
          </div>
        </div>

        <!-- tulip dude speech bubble -->
        <a href="#about"><span class="tulip-bubble">{{ tulip }}</span></a>
      </div>

      <div class="pear-pot">
        <!-- pear pal speech bubble -->
        <span class="pear-bubble">{{ pear }}</span>

        <!-- pear pal -->
        <div class="pear-pal">
          <svg viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
            <path
              d="M56.5,-35C68.8,-11.3,71.3,15.7,60.3,33.2C49.2,50.7,24.6,58.8,-1.7,59.8C-28,60.8,-56,54.6,-63.8,39C-71.5,23.4,-59,-1.7,-45,-26.5C-31,-51.2,-15.5,-75.5,3.3,-77.4C22.1,-79.3,44.2,-58.8,56.5,-35Z"
              transform="translate(100 100)" />
          </svg>
          <div class="pear-eye left">
            <span></span>
          </div>
          <div class="pear-eye right">
            <span></span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Theme from "./Theme.vue";

export default {
  components: { Theme },
  name: "Friends",
  data: function () {
    return {
      daisy: "say what?! soo coool",
      pear: "meg griffin is a ux engineer",
      tulip: "jump to her bio!",
    };
  },
};
</script>


