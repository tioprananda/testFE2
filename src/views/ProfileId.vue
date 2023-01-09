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
          <h5>Manage Account</h5>
        </div>
      </div>
    </div>
  </div>

  <div class="py-4 container-fluid" v-for="item in dataUser" :key="item.id">
    <div class="mt-3 row">
      <!-- <div class="col-12 col-md-6 col-xl-6 my-2">
       
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
     
      </div> -->

      <div class="container">
        <div class="row justify-content-center">
          <div class="mx-auto col-xl-4 col-lg-5 col-md-7">
            <div class="card z-index-0">
              <div class="pt-4 text-center card-header">
                <h5>Edit Account</h5>
              </div>

              <div class="card-body">
                <form role="form" @submit.prevent="submit">
                  <div class="mb-3">
                    <label for="name">Name :</label>
                    <soft-input
                      id="name"
                      type="text"
                      placeholder="Name"
                      aria-label="Name"
                      v-model="item.name"
                    />
                  </div>

                  <div class="mb-3">
                    <label for="address">Address :</label>
                    <soft-input
                      id="address"
                      type="text"
                      placeholder="Address"
                      aria-label="Address"
                      v-model="item.address"
                    />
                  </div>

                  <div class="mb-3">
                    <label for="mobile">Mobile :</label>
                    <soft-input
                      id="mobile"
                      type="number"
                      placeholder="Phone Number"
                      aria-label="Phone Number"
                      v-model="item.telephone"
                    />
                  </div>
                  <div class="mb-3">
                    <label for="email">Email :</label>
                    <soft-input
                      id="email"
                      type="email"
                      placeholder="Email"
                      aria-label="Email"
                      v-model="item.email"
                    />
                  </div>
                  <div class="mb-3">
                    <label for="password">Password :</label>
                    <soft-input
                      id="password"
                      type="password"
                      placeholder="Password"
                      aria-label="Password"
                      v-model="item.password"
                    />
                  </div>
                  <div class="mb-3">
                    <label for="passwordConfirm">Password Confirm : </label>
                    <soft-input
                      id="passwordConfirm"
                      type="password"
                      placeholder="password Confirm"
                      aria-label="passwordConfirm"
                      v-model="item.passwordConfirm"
                    />
                  </div>

                  <div class="mb-3">
                    <label for="image">Image : </label>
                    <soft-input
                      id="image"
                      type="file"
                      placeholder="Input Image"
                      aria-label="Input Image"
                      @change="uploadImage($event, item)"
                    />
                    <img :src="previewImg" :alt="previewImg" v-if="previewImg" width="200">
                  </div>

                  <button
                    type="button"
                    class="btn btn-success mx-1 mt-2"
                    @click.prevent="update(item.id, item)"
                  >
                    Update
                  </button>

                  <router-link to="/profile">
                    <button type="button" class="btn btn-secondary mx-1 mt-2">
                      Cancel
                    </button>
                  </router-link>
                </form>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import SoftSwitch from "@/components/SoftSwitch.vue";
// import ProfileInfoCard from "./components/ProfileInfoCard.vue";
// import SoftAvatar from "@/components/SoftAvatar.vue";
import SoftInput from "@/components/SoftInput.vue";
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
import swal from "sweetalert";
import axios from "axios";

export default {
  name: "ProfileOverview",
  components: {
    SoftInput,
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
      previewImg: ``,
    };
  },

  methods: {
    uploadImage(event, item){
      // const dataImg = event.target.files[0].name;
      // item.image = dataImg;
      this.previewImg = URL.createObjectURL(event.target.files[0])
      item.image = URL.createObjectURL(event.target.files[0]);
      this.dataUser.image = item.image;
    },
    
    idProfile(data) {
      this.dataUser.push(data);
    },

    async update(id, item) {
      // validasi ketika password dan password confirm tidak sama
      if (item.password !== item.passwordConfirm) {
        await swal({
          title: "Update Failed!",
          text: "Your Password Not Match!",
          icon: "warning",
          button: "Ok",
        });

      } else if (item.name && item.email){
          let result = await axios.put(`http://localhost:3000/users/` + id, {
            name: item.name,
            address: item.address,
            telephone: item.telephone,
            email: item.email,
            password: item.password,
            image: item.image,
          });
          console.log(result);
          await swal({
            title: "Update Success!",
            text: "Your Account Has been Updated!",
            icon: "success",
            button: "Ok",
          });
          this.$router.push("/");
        }
        else {
          await swal({
            title: "Update Failed!",
            text: "Please Insert Your Name and Email!",
            icon: "warning",
            button: "Ok",
          });
        };
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
