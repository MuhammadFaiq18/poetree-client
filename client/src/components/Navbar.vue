<script>
export default {
  name: "Navbar",
  methods: {
    changePage(page) {
      this.$router.push(`${page}`)
    },
    logout() {
      localStorage.clear()
      swal("You Have Logged Out", "");
      this.$router.push("/login")
    }
  }
};
</script>
<template>
  <nav
    class="navbar navbar-expand-lg mb-3"
    style="background-color: #292828; height: 10vh"
  >
    <div class="container-fluid">
      <a class="navbar-brand text-white" href="#">POETREE</a>
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
        <ul class="navbar-nav me-auto">
          <li class="nav-item">
            <a @click.prevent="changePage('/')" class="nav-link active text-white" aria-current="page" href="#"
              >Home</a
            >
          </li>
          <li class="nav-item">
            <a @click.prevent="changePage('/mypoem')" class="nav-link active text-white" aria-current="page" href="#"
              >My Poem</a
            >
          </li>
          <li class="nav-item">
            <a @click.prevent="changePage('/browse')" class="nav-link active text-white" aria-current="page" href="#"
              >Browse Poem</a
            >
          </li>
        </ul>
        <ul class="navbar-nav">
          <li class="nav-item">
            <a @click.prevent="logout" class="nav-link text-white" href="#">Logout</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
