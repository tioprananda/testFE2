<template>
  <div class="card h-100">
    <div class="p-3 pb-0 card-header">
      <div class="row">
        <div class="col-md-8 d-flex align-items-center">
          <h6 class="mb-0">Profile Information</h6>
        </div>
        <div class="col-md-4 text-end">
          <router-link :to="'/profile/'+info.id.data.id">
          <i
              class="text-sm fas fa-user-edit text-secondary"
              title="Edit Profile"
            ></i>
          </router-link> 
        </div>
      </div>
    </div>
    <div class="p-3 card-body">
      <p class="text-sm">
        
      </p>
      <hr class="my-4 horizontal gray-light" />
      <ul class="list-group">
        <li class="pt-0 text-sm border-0 list-group-item ps-0">
          <strong class="text-dark">Full Name:</strong> &nbsp;
          {{ info.fullName.data.name }}
        </li>
        <li class="text-sm border-0 list-group-item ps-0">
          <strong class="text-dark">Phone:</strong> &nbsp; {{ info.mobile.data.phone }}
        </li>
        <li class="text-sm border-0 list-group-item ps-0">
          <strong class="text-dark">Email:</strong> &nbsp; {{ info.email.data.email }} 
        </li>
        <li class="text-sm border-0 list-group-item ps-0">
          <strong class="text-dark">Location:</strong> &nbsp; {{ info.location.data.company.company_name }}
          
        </li>
        <li class="pb-0 border-0 list-group-item ps-0">
          <strong class="text-sm text-dark">Social:</strong> &nbsp;
          <a
            v-for="({ icon, link }, index) of social"
            :key="index"
            class="py-0 mb-0 btn-simple ps-1 pe-2"
            :href="link"
          >
            <font-awesome-icon :icon="icon" />
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

export default {
  name: "ProfileInfoCard",
  components: {
    FontAwesomeIcon,
  },
  props: {
    title: {
      type: String,
      default: "",
    },
   
    info: {
      type: Object,
      id: String,
      fullName: String,
      mobile: String,
      email: String,
      location: String,
      description : String,
      default: () => {},
    },
    social: {
      type: Array,
      link: String,
      icon: String,
      default: () => [],
    },
    action: {
      type: Object,
      route: String,
      tooltip: String,
      default: () => ({
        route: "javascript:;",
      }),
    },
  },
};
</script>