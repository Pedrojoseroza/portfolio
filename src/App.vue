<script setup>

</script>

<template>
  <section class="container">
    <header>
      <div>
        <h1>
          <span>P</span>
        </h1>
        <p>
          Pedro.Js
        </p>
      </div>
      <nav>
        <ul>
          <li>
            <a href="#">Home</a>
          </li>
          <li>
            <a href="#about">About</a>
          </li>
          <li>
            <a href="#contacts">Contacts</a>
          </li>
          <li>
            <a href="#projects">Projects</a>
          </li>
        </ul>
      </nav>
    </header>
</section>

</template>

<style scoped>
section.container {
  min-height: 100vh;
  background-color: var(--bg-color);
}
header{
  background-color: var(--first-color);
  display: flex;
  justify-content: space-between;
  padding: 25px 35px;
}
header div, ul {
  display: flex;
}
header div {
  font-family: "Allura", cursive;
  font-size: 1.4rem;
}
header div span {
  margin: 0 10px 0 0;
  padding: 10px 14px;
  background-color: var(--bg-color);
  border-radius: 100%;
}
</style>
