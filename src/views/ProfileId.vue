<template>
  <div class="container-fluid">
    <div
      class="mt-4 page-header min-height-300 border-radius-xl"
      :style="{
        backgroundImage:
          'url(' + require('@/assets/img/curved-images/curved14.jpg') + ')',
        backgroundPositionY: '50%',
      }"
    >
      <span class="mask bg-gradient-success opacity-6"></span>
    </div>
    <div class="mx-4 overflow-hidden card card-body blur shadow-blur mt-n6">
      <div class="row gx-4">
        <div class="col-auto">
          <h4>Edit Profile</h4>
        </div>
      </div>
    </div>
  </div>

  <div class="py-4 container-fluid" v-for="item in dataUser" :key="item.id">
    <div class="mt-3 row">
      <div class="col-12 col-md-6 col-xl-6 my-2">
        <!-- gambar -->
        <div class="col-auto">
          <div class="position-relative" v-if="item.image">
            <img
              :src="item.image"
              :alt="item.image"
              class="shadow-sm w-500 border-radius-lg"
            />
          </div>
          <div v-else class="position-relative">
            <img
              src="@/assets/img/user.png"
              alt="user"
              class="shadow-sm w-100 border-radius-lg"
            />
          </div>
        </div>
        <!-- end gambar -->
      </div>

      <div class="col-12 col-md-6 col-xl-6 my-2">
        <div class="card-body">
          <form role="form">
            <div class="mb-3">
              <label for="name">Name :</label>
              <input
                id="name"
                type="text"
                placeholder="Name"
                aria-label="Name"
                v-model="item.name"
              />
            </div>
            <div class="mb-3">
              <label for="address">Address : </label>
              <input
                id="address"
                type="text"
                placeholder="Address"
                aria-label="Adress"
                v-model="item.address"
              />
            </div>
            <div class="mb-3">
              <label for="telephone">telephone</label>
              <input
                id="telephone"
                type="text"
                placeholder="Telephone"
                aria-label="Telephone"
                v-model="item.telephone"
              />
            </div>

            <div class="mb-3">
              <label for="email">email</label>
              <input
                id="email"
                type="email"
                placeholder="Email"
                aria-label="Email"
                v-model="item.email"
              />
            </div>
            <div class="mb-3">
              <label for="password">password</label>
              <input
                id="password"
                type="password"
                placeholder="Password"
                aria-label="Password"
                v-model="item.password"
              />
            </div>

            <button type="submit" class="btn btn-success m-2" @click="update(item.id, item)">
              Update Data
            </button>
            <button
              type="submit"
              class="btn btn-warning m-2"
              @click.prevent="reset"
            >
              Reset
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import SoftSwitch from "@/components/SoftSwitch.vue";
// import ProfileInfoCard from "./components/ProfileInfoCard.vue";
// import SoftAvatar from "@/components/SoftAvatar.vue";
import sophie from "@/assets/img/kal-visuals-square.jpg";
import marie from "@/assets/img/marie.jpg";
import ivana from "@/assets/img/ivana-square.jpg";
import peterson from "@/assets/img/team-4.jpg";
import nick from "@/assets/img/team-3.jpg";
import img1 from "@/assets/img/home-decor-1.jpg";
import img2 from "@/assets/img/home-decor-2.jpg";
import img3 from "@/assets/img/home-decor-3.jpg";
import team1 from "@/assets/img/team-1.jpg";
import team2 from "@/assets/img/team-2.jpg";
import team3 from "@/assets/img/team-3.jpg";
import team4 from "@/assets/img/team-4.jpg";
import {
  faFacebook,
  faTwitter,
  faInstagram,
} from "@fortawesome/free-brands-svg-icons";
// import DefaultProjectCard from "./components/DefaultProjectCard.vue";
// import PlaceHolderCard from "@/examples/Cards/PlaceHolderCard.vue";
import setNavPills from "@/assets/js/nav-pills.js";
import setTooltip from "@/assets/js/tooltip.js";
import axios from "axios";

export default {
  name: "ProfileOverview",
  components: {
    // SoftSwitch,
    // ProfileInfoCard,
    // SoftAvatar,
    // DefaultProjectCard,
    // PlaceHolderCard,
  },
  data() {
    return {
      showMenu: false,
      sophie,
      marie,
      ivana,
      peterson,
      nick,
      img1,
      team1,
      team2,
      team3,
      team4,
      img2,
      img3,
      faFacebook,
      faTwitter,
      faInstagram,
      dataUser: [],
      userLocal: [],
    };
  },

  methods: {
    idProfile(data) {
      this.dataUser.push(data);
    },
    reset() {
      this.dataUser.forEach((item) => {
        item.name = "";
      });
    },
    async update(id, item){
      let result = await axios.put(`http://localhost:3000/users/`+id,{
        name : item.name,
        address : item.address,
        telephone : item.telephone,
        email : item.email,
        password : item.password
      })
      console.log(result);
      this.$router.push('/');
    },
  },

  mounted() {
    this.$store.state.isAbsolute = true;
    setNavPills();
    setTooltip(this.$store.state.bootstrap);

    // get data user dar api
    axios
      .get(`http://localhost:3000/users/${this.$route.params.id}`)
      .then((response) => this.idProfile(response.data));

    //  get data user dari local storage
    let user = localStorage.getItem("user-info");
    if (user) {
      this.userLocal = JSON.parse(user);
    } else {
      this.$router.push("/sign-in");
    }
  },
  beforeUnmount() {
    this.$store.state.isAbsolute = false;
  },
};
</script>

<style scoped>
/* .editProfile a:hover{
  background-color : rgb(117, 243, 195);
} */
</style>
