<template>
  <div class="wrapper">
    <aside class="sidebar">
      <slot name="sidebar" />
    </aside>
    <main class="main">
      <slot name="main" />
    </main>

  </div>
  <footer class="footer">
    <slot name="footer" />
  </footer>
</template>

<style>
.wrapper {
  display: grid;
  grid-template-areas: "sidebar main"
                        "footer footer";
}
.sidebar {
  border: 2px solid red;
  grid-area: 'sidebar';
  padding: 20px;
}

.main {
  border: 2px solid green;
  grid-area: 'main';
  padding: 20px;
}

.footer {
  border: 2px solid blue;
  grid-area: footer;
  padding: 20px;
}
</style>