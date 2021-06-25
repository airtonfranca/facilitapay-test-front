<template>
  <header>
    <div class="container">
      <nav class="navbar navbar-expand-lg navbar-light">
        <div class="logo">
          <img
            src="https://static.wixstatic.com/media/56d601_9aaf731636ee47b1b717f56ee734898f~mv2.png/v1/fill/w_158,h_53,al_c,q_85,usm_0.66_1.00_0.01/fpay_logo.webp"
            alt="Facilita Pay Logo"
          />
        </div>

        <button
          class="navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#conteudoNavbarSuportado"
          aria-controls="conteudoNavbarSuportado"
          aria-expanded="false"
          aria-label="Alterna navegação"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="conteudoNavbarSuportado">
          <ul class="navbar-nav ml-lg-auto">
            <li class="nav-item active">
              <a class="nav-link" href="#">Home</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">About</a>
            </li>
          </ul>
        </div>
      </nav>
    </div>
  </header>
</template>

<style>
header {
  width: 100%;
  background-color: white;
}
.logo {
  margin: 10px 10px 10px 35px;
  float: left;
}
.nav-item {
  font-weight: 800;
  font-size: 16px;
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}
.navbar-light .navbar-nav .nav-item .nav-link {
  color: rgb(6, 6, 61);
}
.navbar-light .navbar-nav .nav-item .nav-link:hover {
  color: rgb(12, 167, 133);
}
.navbar-collapse {
  background: #fff;
}
.container {
  width: 1280px;
  margin: 0 auto;
  font-size: 10px;
  height: 80px;
}
</style>
