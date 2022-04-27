<template>
  <div class="header">
    <!-- animated gradient name -->
    <svg
      xmlns="http://www.w3.org/2000/svg"
      version="1.1"
      xmlns:xlink="http://www.w3.org/1999/xlink"
      width="100%"
      height="100%"
    >
      <rect x="0" y="0" fill="none" width="100%" height="100%" />

      <text
        x="50%"
        text-anchor="middle"
        y="50%"
        dy="0.4em"
        fill="url(#pattern)"
        class="header-text"
      >
        {{ header }}
      </text>

      <defs>
        <!-- set gradient -->
        <linearGradient id="gradient" x1="0%" y1="0%" x2="100%" y2="0">
          <stop offset="0%" class="stop-one" />
          <stop offset="25%" class="stop-two" />
          <stop offset="50%" class="stop-three" />
          <stop offset="75%" class="stop-four" />
          <stop offset="100%" class="stop-five" />
        </linearGradient>

        <pattern
          id="pattern"
          x="0"
          y="0"
          width="300%"
          height="100%"
          patternUnits="userSpaceOnUse"
        >
          <rect x="0" y="0" width="150%" height="100%" fill="url(#gradient)">
            <animate
              attributeType="XML"
              attributeName="x"
              from="0"
              to="150%"
              dur="20s"
              repeatCount="indefinite"
            />
          </rect>
          <rect
            x="-150%"
            y="0"
            width="150%"
            height="100%"
            fill="url(#gradient)"
          >
            <animate
              attributeType="XML"
              attributeName="x"
              from="-150%"
              to="0"
              dur="20s"
              repeatCount="indefinite"
            />
          </rect>
        </pattern>
      </defs>
    </svg>

    <!-- wavy border -->
    <svg
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 1440 320"
      class="header-border"
    >
      <path
        fill-opacity="1"
        d="M0,32L24,37.3C48,43,96,53,144,85.3C192,117,240,171,288,170.7C336,171,384,117,432,101.3C480,85,528,107,576,101.3C624,96,672,64,720,48C768,32,816,32,864,42.7C912,53,960,75,1008,85.3C1056,96,1104,96,1152,101.3C1200,107,1248,117,1296,106.7C1344,96,1392,64,1416,48L1440,32L1440,0L1416,0C1392,0,1344,0,1296,0C1248,0,1200,0,1152,0C1104,0,1056,0,1008,0C960,0,912,0,864,0C816,0,768,0,720,0C672,0,624,0,576,0C528,0,480,0,432,0C384,0,336,0,288,0C240,0,192,0,144,0C96,0,48,0,24,0L0,0Z"
      ></path>
    </svg>
  </div>
</template>

<script>
export default {
  name: "Header",
  data: function () {
    return {
      header: "MEG GRIFFIN",
    };
  },
};
</script>

