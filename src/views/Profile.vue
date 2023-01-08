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
      <div class="row gx-4" v-for="item in dataUser" :key="item.id">
        
        <!-- gambar -->
        <div class="col-auto">
          <div class="avatar avatar-xl position-relative" v-if="item.image">
            <img
              :src="item.image"
              :alt="item.image"
              class="shadow-sm w-100 border-radius-lg"
            />
          </div>
          <div v-else class="avatar avatar-xl position-relative">
            <img
              src="@/assets/img/user.png"
              alt="user"
              class="shadow-sm w-100 border-radius-lg"
            />
          </div>
        </div>
        <!-- end gambar -->

        <div class="col-auto my-auto">
          <div class="h-100">
            <h5 class="mb-1">{{ item.name }}</h5>
          </div>
        </div>
        <div
          class="mx-auto mt-3 col-lg-4 col-md-6 my-sm-auto ms-sm-auto me-sm-0"
        >
          <div class="nav-wrapper position-relative end-0">
            <ul
              class="p-1 bg-transparent nav nav-pills nav-fill"
              role="tablist"
            >
              <!-- EDIT PROFILE -->
              <li class="nav-item editProfile">
                <router-link :to="'/profile/'+item.id" class="px-0 mt-2 py-1 nav-link">
                  <!-- <svg
                    class="text-dark"
                    width="16px"
                    height="16px"
                    viewBox="0 0 40 40"
                    version="1.1"
                    xmlns="http://www.w3.org/2000/svg"
                    xmlns:xlink="http://www.w3.org/1999/xlink"
                  >
                    <title>Edit Profile</title>
                    <g
                      stroke="none"
                      stroke-width="1"
                      fill="none"
                      fill-rule="evenodd"
                    >
                      <g
                        transform="translate(-2020.000000, -442.000000)"
                        fill="#FFFFFF"
                        fill-rule="nonzero"
                      >
                        <g transform="translate(1716.000000, 291.000000)">
                          <g transform="translate(304.000000, 151.000000)">
                            <polygon
                              class="color-background"
                              opacity="0.596981957"
                              points="18.0883333 15.7316667 11.1783333 8.82166667 13.3333333 6.66666667 6.66666667 0 0 6.66666667 6.66666667 13.3333333 8.82166667 11.1783333 15.315 17.6716667"
                            ></polygon>
                            <path
                              class="color-background"
                              d="M31.5666667,23.2333333 C31.0516667,23.2933333 30.53,23.3333333 30,23.3333333 C29.4916667,23.3333333 28.9866667,23.3033333 28.48,23.245 L22.4116667,30.7433333 L29.9416667,38.2733333 C32.2433333,40.575 35.9733333,40.575 38.275,38.2733333 L38.275,38.2733333 C40.5766667,35.9716667 40.5766667,32.2416667 38.275,29.94 L31.5666667,23.2333333 Z"
                              opacity="0.596981957"
                            ></path>
                            <path
                              class="color-background"
                              d="M33.785,11.285 L28.715,6.215 L34.0616667,0.868333333 C32.82,0.315 31.4483333,0 30,0 C24.4766667,0 20,4.47666667 20,10 C20,10.99 20.1483333,11.9433333 20.4166667,12.8466667 L2.435,27.3966667 C0.95,28.7083333 0.0633333333,30.595 0.00333333333,32.5733333 C-0.0583333333,34.5533333 0.71,36.4916667 2.11,37.89 C3.47,39.2516667 5.27833333,40 7.20166667,40 C9.26666667,40 11.2366667,39.1133333 12.6033333,37.565 L27.1533333,19.5833333 C28.0566667,19.8516667 29.01,20 30,20 C35.5233333,20 40,15.5233333 40,10 C40,8.55166667 39.685,7.18 39.1316667,5.93666667 L33.785,11.285 Z"
                            ></path>
                          </g>
                        </g>
                      </g>
                    </g>
                  </svg>
                  <span class="ms-1">Edit Profile</span> -->
                  <button class="btn btn-success">Edit Profile</button>
                </router-link>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="py-4 container-fluid">
    <div class="mt-3 row">
      <div class="col-12 col-md-6 col-xl-4">
        <div class="card h-100">
          <div class="p-3 pb-0 card-header">
            <h6 class="mb-0">Platform Settings</h6>
          </div>
          <div class="p-3 card-body">
            <h6 class="text-xs text-uppercase text-body font-weight-bolder">
              Account
            </h6>
            <ul class="list-group">
              <li class="px-0 border-0 list-group-item">
                <soft-switch
                  id="flexSwitchCheckDefault"
                  name="email"
                  class="ps-0 ms-auto"
                  label-class="mb-0 text-body ms-3 text-truncate w-80"
                  checked
                  >Email me when someone follows me</soft-switch
                >
              </li>
              <li class="px-0 border-0 list-group-item">
                <soft-switch
                  id="flexSwitchCheckDefault1"
                  name="Email"
                  label-class="mb-0 text-body ms-3 text-truncate w-80"
                  class="ps-0 ms-auto"
                  >Email me when someone answers on my post</soft-switch
                >
              </li>

              <li class="px-0 border-0 list-group-item">
                <soft-switch
                  id="flexSwitchCheckDefault2"
                  name="Email"
                  label-class="mb-0 text-body ms-3 text-truncate w-80"
                  class="ps-0 ms-auto"
                  checked
                  >Email me when someone mentions me</soft-switch
                >
              </li>
            </ul>
            <h6
              class="mt-4 text-xs text-uppercase text-body font-weight-bolder"
            >
              Application
            </h6>
            <ul class="list-group">
              <li class="px-0 border-0 list-group-item">
                <soft-switch
                  id="flexSwitchCheckDefault3"
                  name="Project Launch"
                  class="ps-0 ms-auto"
                  label-class="mb-0 text-body ms-3 text-truncate w-80"
                  >New launches and projects</soft-switch
                >
              </li>
              <li class="px-0 border-0 list-group-item">
                <soft-switch
                  id="flexSwitchCheckDefault4"
                  name="Product Update"
                  class="ps-0 ms-auto"
                  label-class="mb-0 text-body ms-3 text-truncate w-80"
                  checked
                  >Monthly product updates</soft-switch
                >
              </li>
              <li class="px-0 pb-0 border-0 list-group-item">
                <soft-switch
                  id="flexSwitchCheckDefault5"
                  name="Newsletter"
                  class="ps-0 ms-auto"
                  label-class="mb-0 text-body ms-3 text-truncate w-80"
                  >Subscribe to newsletter</soft-switch
                >
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div class="mt-4 col-12 col-md-6 col-xl-4 mt-md-0" v-for="item in dataUser" :key="item.id">
        <profile-info-card v-if="this.userLocal.password === item.password"
          title="Profile Information"
          description="Hi, I’m Alec Thompson, Decisions: If you can’t decide, the answer is no. If two equally difficult paths, choose the one more painful in the short term (pain avoidance is creating an illusion of equality)."
          :info="item"
          :social="[
            {
              link: 'https://www.facebook.com/CreativeTim/',
              icon: faFacebook,
            },
            {
              link: 'https://twitter.com/creativetim',
              icon: faTwitter,
            },
            {
              link: 'https://www.instagram.com/creativetimofficial/',
              icon: faInstagram,
            },
          ]"
          :action="{
            route: 'javascript:;',
            tooltip: 'Edit Profile',
          }"
        />
      </div>
      <div class="mt-4 col-12 col-xl-4 mt-xl-0">
        <div class="card h-100">
          <div class="p-3 pb-0 card-header">
            <h6 class="mb-0">Conversations</h6>
          </div>
          <div class="p-3 card-body">
            <ul class="list-group">
              <li
                class="px-0 mb-2 border-0 list-group-item d-flex align-items-center"
              >
                <soft-avatar
                  class="me-3"
                  :img="sophie"
                  alt="kal"
                  border-radius="lg"
                  shadow="regular"
                />
                <div
                  class="d-flex align-items-start flex-column justify-content-center"
                >
                  <h6 class="mb-0 text-sm">Sophie B.</h6>
                  <p class="mb-0 text-xs">Hi! I need more information..</p>
                </div>
                <a
                  class="mb-0 btn btn-link pe-3 ps-0 ms-auto"
                  href="javascript:;"
                  >Reply</a
                >
              </li>
              <li
                class="px-0 mb-2 border-0 list-group-item d-flex align-items-center"
              >
                <soft-avatar
                  class="me-3"
                  :img="marie"
                  alt="kal"
                  border-radius="lg"
                  shadow="regular"
                />
                <div
                  class="d-flex align-items-start flex-column justify-content-center"
                >
                  <h6 class="mb-0 text-sm">Anne Marie</h6>
                  <p class="mb-0 text-xs">Awesome work, can you..</p>
                </div>
                <a
                  class="mb-0 btn btn-link pe-3 ps-0 ms-auto"
                  href="javascript:;"
                  >Reply</a
                >
              </li>
              <li
                class="px-0 mb-2 border-0 list-group-item d-flex align-items-center"
              >
                <soft-avatar
                  class="me-3"
                  :img="ivana"
                  alt="kal"
                  border-radius="lg"
                  shadow="regular"
                />
                <div
                  class="d-flex align-items-start flex-column justify-content-center"
                >
                  <h6 class="mb-0 text-sm">Ivanna</h6>
                  <p class="mb-0 text-xs">About files I can..</p>
                </div>
                <a
                  class="mb-0 btn btn-link pe-3 ps-0 ms-auto"
                  href="javascript:;"
                  >Reply</a
                >
              </li>
              <li
                class="px-0 mb-2 border-0 list-group-item d-flex align-items-center"
              >
                <soft-avatar
                  class="me-3"
                  :img="peterson"
                  alt="kal"
                  border-radius="lg"
                  shadow="regular"
                />
                <div
                  class="d-flex align-items-start flex-column justify-content-center"
                >
                  <h6 class="mb-0 text-sm">Peterson</h6>
                  <p class="mb-0 text-xs">Have a great afternoon..</p>
                </div>
                <a
                  class="mb-0 btn btn-link pe-3 ps-0 ms-auto"
                  href="javascript:;"
                  >Reply</a
                >
              </li>
              <li
                class="px-0 border-0 list-group-item d-flex align-items-center"
              >
                <soft-avatar
                  class="me-3"
                  :img="nick"
                  alt="kal"
                  border-radius="lg"
                  shadow="regular"
                />
                <div
                  class="d-flex align-items-start flex-column justify-content-center"
                >
                  <h6 class="mb-0 text-sm">Nick Daniel</h6>
                  <p class="mb-0 text-xs">Hi! I need more information..</p>
                </div>
                <a
                  class="mb-0 btn btn-link pe-3 ps-0 ms-auto"
                  href="javascript:;"
                  >Reply</a
                >
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
    <div class="mt-4 row">
      <div class="col-12">
        <div class="mb-4 card">
          <div class="p-3 pb-0 card-header">
            <h6 class="mb-1">Projects</h6>
            <p class="text-sm">Architects design houses</p>
          </div>
          <div class="p-3 card-body">
            <div class="row">
              <default-project-card
                title="Modern"
                :image="img1"
                label="Project #2"
                description="As Uber works through a huge amount of internal
                management turmoil."
                :authors="[
                  {
                    image: team1,
                    name: 'Elena Morison',
                  },
                  {
                    image: team2,
                    name: 'Ryan Milly',
                  },
                  {
                    image: team3,
                    name: 'Nick Daniel',
                  },
                  {
                    image: team4,
                    name: 'Peterson',
                  },
                ]"
                :action="{
                  color: 'success',
                  label: 'View Project',
                }"
              />

              <default-project-card
                title="Scandinavian"
                :image="img2"
                label="Project #1"
                description="Music is something that every person has his or her own
                      specific opinion about."
                :authors="[
                  {
                    image: team3,
                    name: 'Nick Daniel',
                  },
                  {
                    image: team4,
                    name: 'Peterson',
                  },
                  {
                    image: team1,
                    name: 'Elena Morison',
                  },
                  {
                    image: team2,
                    name: 'Ryan Milly',
                  },
                ]"
                :action="{
                  color: 'success',
                  label: 'View Project',
                }"
              />

              <default-project-card
                title="Minimalist"
                :image="img3"
                label="Project #3"
                description="Different people have different taste, and various types
                      of music."
                :authors="[
                  {
                    image: team4,
                    name: 'Peterson',
                  },
                  {
                    image: team3,
                    name: 'Nick Daniel',
                  },
                  {
                    image: team1,
                    name: 'Elena Morison',
                  },
                  {
                    image: team2,
                    name: 'Ryan Milly',
                  },
                ]"
                :action="{
                  color: 'success',
                  label: 'View Project',
                }"
              />

              <div class="mb-4 col-xl-3 col-md-6 mb-xl-0">
                <place-holder-card
                  :title="{ text: 'New project', variant: 'h5' }"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SoftSwitch from "@/components/SoftSwitch.vue";
import ProfileInfoCard from "./components/ProfileInfoCard.vue";
import SoftAvatar from "@/components/SoftAvatar.vue";
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
import DefaultProjectCard from "./components/DefaultProjectCard.vue";
import PlaceHolderCard from "@/examples/Cards/PlaceHolderCard.vue";
import setNavPills from "@/assets/js/nav-pills.js";
import setTooltip from "@/assets/js/tooltip.js";
import axios from 'axios';

export default {
  name: "ProfileOverview",
  components: {
    SoftSwitch,
    ProfileInfoCard,
    SoftAvatar,
    DefaultProjectCard,
    PlaceHolderCard,
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
      dataUser : [],
      userLocal : [],
      
    };
  },

  methods: {
    editProfile(data) {
     data.forEach((item) => {
      if(item.id === this.userLocal.id){
        this.dataUser.push(item)
      }
     })

    },
  },

  mounted() {
    this.$store.state.isAbsolute = true;
    setNavPills();
    setTooltip(this.$store.state.bootstrap);

    // get data user dar api
    axios.get(`http://localhost:3000/users`)
    .then((response) => this.editProfile(response.data))

    //  get data user dari local storage
    let user = localStorage.getItem("user-info");
    if(user){
      this.userLocal = JSON.parse(user);
    }
    else {
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
