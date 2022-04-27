<template>
  <div>
    <input @change="toggleTheme" id="checkbox" type="checkbox" class="theme-toggle" />

    <label for="checkbox">
      <div class="moody-buddy">
        <span class="night-moon"></span>
        <span class="day-sun"></span>
        <small class="day-sun-ray"></small>
        <small class="day-sun-ray"></small>
        <small class="day-sun-ray"></small>
        <small class="day-sun-ray"></small>
        <small class="day-sun-ray"></small>
        <small class="day-sun-ray"></small>

        <div class="moody-eye left">
          <span></span>
        </div>
        <div class="moody-eye right">
          <span></span>
        </div>
      </div>

      <!-- moody buddy speech bubble -->
      <span class="moody-bubble">{{ moody }}</span>
      <div :class="{ 'switch-toggle-checked': userTheme === 'night-theme' }"></div>
    </label>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userTheme: "day-theme",
      moody: "",
      day: "change to light theme!",
      night: "change to dark theme!",
    };
  },
  mounted() {
    const initUserTheme = this.getTheme() || this.getMediaPreference();
    this.setTheme(initUserTheme);
    if (initUserTheme == "day-theme") {
      this.moody = this.night;
    } else {
      this.moody = this.day;
    }
  },
  methods: {
    toggleTheme() {
      const activeTheme = localStorage.getItem("user-theme");
      if (activeTheme === "day-theme") {
        this.setTheme("night-theme");
        this.moody = this.day;
      } else {
        this.setTheme("day-theme");
        this.moody = this.night;
      }
    },

    getTheme() {
      return localStorage.getItem("user-theme");
    },

    setTheme(theme) {
      localStorage.setItem("user-theme", theme);
      this.userTheme = theme;
      document.documentElement.className = theme;
    },

    getMediaPreference() {
      const hasNightPreference = window.matchMedia(
        "(prefers-color-scheme: night)"
      ).matches;
      if (hasNightPreference) {
        return "night-theme";
      } else {
        return "day-theme";
      }
    },
  },
};
</script>
