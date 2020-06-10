<template>
  <div id="app">
    <main>
        <div class="structure">
            <router-view/>
        </div>
    </main>

    <footer id="site-footer">
      <router-link to="/">Where are you?</router-link> |
      <router-link to="/about">About this site</router-link>
    </footer>

  </div>
</template>

<style lang="scss">
// Variables
// to-do: move to their own variables file to be included project-wide
$teal: #008080;

// assign variables for color usage
$cta-color: $teal;
$cta-active-color: darken($cta-color, 10%);

// to-do: use a reset or normalize stylesheet
body {
  margin: 0;
}

#app {
  font-family: 'Roboto Slab', Helvetica, Arial, sans-serif;
  text-align: center;
  display: flex;
  flex-direction: column;
  color: #2c3e50;
  height: 100vh;
}

main {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-grow: 1;
  flex-shrink: 1;
  padding: 20px;

  > .structure {
      max-width: 800px;
  }
}

.icon-clock {
    fill: $teal;
    width: 60px;
    height: 60px;
}

#site-footer {
  padding: 30px;
  background: #eee;
  // reliable way to stick footer to bottom on any size screen
  margin-top: auto;
}

// To-do - move all common styles to a shared typography.sass
a {
  color: $cta-color;
  text-decoration: none;
  border-bottom: solid 1px rgba($cta-active-color, 0);
  transition: border-color 0.2s ease;

  &:hover {
    border-color: $cta-color;
  }

  &:focus {
      color: darken($cta-color, 10%)
  }

  &.router-link-exact-active {
    color: $cta-active-color;
    // don't need a active state if we are on the page
    // Better to be done with Vue so active link isn't a link at all
    &:hover {
        border-color: transparent;
    }
  }
}

</style>
