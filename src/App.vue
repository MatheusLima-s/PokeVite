<script setup></script>

<template>
  <!-- NAVBAR -->
  <nav
    class="navbar navbar-expand-lg navbar-dark bg-dark"
    style="border-bottom: 1px solid rgba(255, 255, 255, 0.1)"
  >
    <div class="container-fluid">
      <router-link class="navbar-brand" to="/">
        <img
          src="https://cdn-icons-png.flaticon.com/512/188/188987.png"
          alt="PokeVit"
          width="30"
          height="24"
        />
      </router-link>
      <router-link class="navbar-brand" to="/">PokeVit</router-link>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link class="nav-link active" aria-current="page" to="/"
              >Home</router-link
            >
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/about">About</router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <!-- CONTENT -->
  <div class="content main bg-dark">
    <router-view> </router-view>
  </div>

  <footer class="bg-dark text-light">
    <div class="footer">Matheus Lima - {{ new Date().getFullYear() }}</div>
  </footer>
</template>

<style>
footer {
  position: fixed;
  bottom: 0;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 56px;
}
.content {
  min-height: calc(
    100vh - 56px - 56px
  ); /* 56px para o navbar e 56px para o footer */
}
</style>
