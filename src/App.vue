<template>
  <div>
    <div class="box outer-box">
      <div class="box inner-box"></div>
    </div>
    <div class="theme-switcher">
      <label for="btn-1">Black</label>
      <label for="btn-2">White</label>
      <label for="btn-3">Orange</label>

      <input type="radio" id="btn-1" value="black"  v-model="theme">
      <input type="radio" id="btn-2" value="white"  v-model="theme">
      <input type="radio" id="btn-3" value="orange" v-model="theme">
    </div>
  </div>
</template>

<script>
import './App.css';

function toggleTheme(themeToApply){
  const themes = document.querySelectorAll('[data-theme]');

  themes.forEach(theme => {
    if (theme.dataset.theme === themeToApply) {
      theme.disabled = false;
      localStorage.setItem('theme', themeToApply);
    } else {
      theme.disabled = true;
    }
  });
}

export default {
  data() {
    return {
      theme : ''
    }
  },
  watch : {
    theme : theme => toggleTheme(theme)
  },
  mounted() {
    const theme = localStorage.getItem('theme');

    if (theme) {
      this.theme = theme;
    }
  }
}
</script>

<style>
.outer-box {
  background-color: var(--bg-color);
  border-color : var(--border-color);
}

.inner-box {
  background-color: var(--fg-color);
  border-color : var(--border-color);
  width : 100px;
  height : 100px;
}


</style>
