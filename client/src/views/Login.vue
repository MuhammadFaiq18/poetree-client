<script>
import axiosInstance from "../axiosInstance";
import WelcomeNav from "../components/WelcomeNav.vue";

export default {
  name: "Login",
  components: {
    WelcomeNav,
  },
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    async login() {
      try {
        const { data } = await axiosInstance.post("/login", {
          email: this.email,
          password: this.password,
        });
        console.log(data);

        localStorage.setItem("id", data.id);
        localStorage.setItem("email", data.email);
        localStorage.setItem("username", data.username);
        localStorage.setItem("access_token", data.access_token);
        swal("You Have Logged In", "");
        this.$router.push("/");
      } catch (err) {
        console.log(err);
        swal("Warning", "Invalid Email/Password", "error");
      }
    },
    changePage(page) {
      this.$router.push(`${page}`);
    },
  },
};
</script>
<template>
  <WelcomeNav />
  <div class="container mt-5">
    <div class="row">
      <div class="col-6 offset-3">
        <div class="card">
          <div class="card-body">
            <h3 class="card-title mb-3 text-center">Login Form</h3>
            <div class="mb-3">
              <label for="email" class="form-label">Email</label>
              <input
                v-model="email"
                type="email"
                class="form-control"
                id="email"
              />
            </div>
            <div class="mb-3">
              <label for="password" class="form-label">Password</label>
              <input
                v-model="password"
                type="password"
                class="form-control"
                id="password"
              />
            </div>
            <div>
              <button class="button" @click.prevent="login">Login</button>
            </div>
            <div>
              <p class="text-center text-muted mb-0" style="margin-top: 15px">
                Don't have an account yet?
                <a
                  @click.prevent="changePage('/register')"
                  href="#"
                  class="fw-bold text-body"
                  ><u>Register here</u></a
                >
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* button */

.button {
  transition-duration: 0.5s;
  background-color: white;
  height: 40px;
  width: 100%;
  border-radius: 5px;
  color: #292828;
  border-color: #292828;
}

.button:hover {
  background-color: #292828; /* Green */
  color: white;
  border: none;
}
</style>
