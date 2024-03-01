<template>
  <div class="wrapper">
    <main class="main">
      <slot name="main" />
    </main>
    <aside class="sidebar">
      <slot name="sidebar" />
    </aside>
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
  padding: 20px;
}

.main {
  border: 2px solid green;
  padding: 20px;
}

.footer {
  border: 2px solid blue;
  padding: 20px;
}
</style>