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

  <div class="py-4 container-fluid">
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
          <div class="mx-auto col-lg-8 col-md-7">
            <div class="card z-index-0">
              <div class="pt-4 text-center card-header">
                <h5>Edit Account</h5>
              </div>

              <div class="card-body">
                <form role="form" @submit.prevent="submit" enctype="multipart/form-data">
                  <div class="mb-3">
                    <label for="name">Name :</label>
                    <soft-input
                      id="name"
                      type="text"
                      placeholder="Name"
                      aria-label="Name"
                      v-model="this.dataUser.data.name"
                    />
                  </div>

                  <div class="mb-3">
                    <label for="mobile">Phone :</label>
                    <soft-input
                      id="mobile"
                      type="number"
                      placeholder="Phone Number"
                      aria-label="Phone Number"
                      v-model="this.dataUser.data.phone"
                    />
                  </div>
                  <div class="mb-3">
                    <label for="email">Email :</label>
                    <soft-input
                      id="email"
                      type="email"
                      placeholder="Email"
                      aria-label="Email"
                      v-model="this.dataUser.data.email"
                    />
                  </div>
                  <div class="mb-3">
                    <label for="password">Old Password :</label>
                    <soft-input
                      id="OldPassword"
                      type="password"
                      placeholder="Old Password"
                      aria-label="Old Password"
                      v-model="oldPassword"
                    />
                  </div>
                  <div class="mb-3">
                    <label for="passwordConfirm">New Password : </label>
                    <soft-input
                      id="NewPassword"
                      type="password"
                      placeholder="New Password"
                      aria-label="New Password"
                      v-model="newPassword"
                    />
                  </div>

                  <div class="mb-3">
                    <label for="image">Photo : </label>
                    <soft-input
                      id="image"
                      type="file"
                      placeholder="Input Image"
                      aria-label="Input Image"
                      @change="uploadImage($event, this.dataUser)"
                    />
                    <div v-if="this.dataUser.data.photo">
                      <img :src="this.dataUser.data.photo" width="250" />
                    </div>
                    <div v-else>
                      <img src="../assets/img/user.png" width="250" />
                    </div>
                  </div>

                  <button
                    type="button"
                    class="btn btn-success mx-1 mt-2"
                    @click.prevent="
                      update(this.dataUser.data.id, this.dataUser.data)
                    "
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
      dataUser: null,
      userLocal: [],
      previewImg: ``,
      oldPassword: ``,
      newPassword: ``,
    };
  },

  methods: {
    uploadImage(event, item) {
      this.previewImg = event.target.files[0];
      item.photo = URL.createObjectURL(event.target.files[0]);
      this.dataUser.data.photo = item.photo;
      console.log(this.dataUser.data.photo);
      console.log(item.photo);
    },

    idProfile(data) {
      this.dataUser = data;
      console.log(this.dataUser.data);
    },

    async update(id, item) {
      // jika form kosong
      if (
        !this.dataUser.data.name ||
        !this.dataUser.data.phone ||
        !this.dataUser.data.email ||
        !this.oldPassword ||
        !this.newPassword ||
        !this.previewImg 
      ) {
        // pesan ketika sukses
        await swal({
          title: "Update Failed!",
          text: "Please Insert Form!",
          icon: "warning",
          button: "Ok",
        });
      } else {
        console.log(id);
        console.log(item);
        const token = localStorage.getItem("user-info");
        console.log(token);

        //  ubah nama
        let resultName = await axios.put(
          `https://dev.api.universal-iot.com/rest-api/v-1/test/account/profile`,
          {
            name: item.name,
          },
          {
            headers: {
              Authorization: `Bearer ${token}`,
            },
          }
        );
        console.log(resultName);

        // ubah no hp
        let resultPhone = await axios.put(
          `https://dev.api.universal-iot.com/rest-api/v-1/test/account/profile/phone`,
          {
            phone: item.phone,
          },
          {
            headers: {
              Authorization: `Bearer ${token}`,
            },
          }
        );
        console.log(resultPhone);

        // ubah email
        let resultEmail = await axios.put(
          `https://dev.api.universal-iot.com/rest-api/v-1/test/account/profile/email`,
          {
            email: item.email,
          },
          {
            headers: {
              Authorization: `Bearer ${token}`,
            },
          }
        );
        console.log(resultEmail);

          // ubah gambar
          let fd = new FormData();
          fd.append(`image`, this.previewImg);
          console.log(fd);
          console.log(this.previewImg);

          let resultPhoto = await axios
          .put(`https://dev.api.universal-iot.com/rest-api/v-1/test/account/profile/photo`,{
            photo : this.previewImg
          },    
        {
            headers : {
              'Authorization' : `Bearer ${token}`,
              'Content-Type': 'multipart/form-data'
            }
          }
        )
        console.log(resultPhoto)

        // reset password
      
          let resultPassword = await axios.patch(
            `https://dev.api.universal-iot.com/rest-api/v-1/test/account/changepassword`,
            {
              password_old: this.oldPassword,
              password_new: this.newPassword,
            },
            {
              headers: {
                Authorization: `Bearer ${token}`,
              },
            }
          );
          console.log(resultPassword);
       

        // pesan ketika sukses
        if(resultPassword.status === 201){
          await swal({
          title: "Update Failed!",
          text: "Incorrect Old Password!",
          icon: "warning",
          button: "Ok",
        })
        .then(() => {
          this.oldPassword = null,
          this.newPassword = null
        })
        } else {
        await swal({
          title: "Update Success!",
          text: "Your Account Has been Updated!",
          icon: "success",
          button: "Ok",
        });
        this.$router.push("/");
      }
      }
    },
  },

  async created() {
    let result = await axios
      .get(
        `https://dev.api.universal-iot.com/rest-api/v-1/test/account/profile`,
        {
          headers: {
            Authorization: "Bearer " + localStorage.getItem("user-info"),
          },
        }
      )
      .then((response) => {
        this.idProfile(response.data);
      });
    console.log(result);
  },

  mounted() {
    this.$store.state.isAbsolute = true;
    setNavPills();
    setTooltip(this.$store.state.bootstrap);
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
