<template>
  <div class="card h-100">
    <div class="p-3 pb-0 card-header">
      <div class="row">
        <div class="col-md-8 d-flex align-items-center">
          <h6 class="mb-0">Profile Information</h6>
        </div>
        <div class="col-md-4 text-end">
          <a href="#">
            <i
              class="text-sm fas fa-user-edit text-secondary"
              data-bs-toggle="tooltip"
              data-bs-placement="top"
            ></i>
          </a>
        </div>
      </div>
    </div>
    <div class="p-3 card-body">
      <hr class="horizontal gray-light" />
      <ul class="list-group">
        <li class="text-sm border-0 list-group-item ps-0">
          <strong class="text-dark">Name:</strong> &nbsp; {{ info.name }}
        </li>
        <li class="text-sm border-0 list-group-item ps-0">
          <strong class="text-dark">Address:</strong> &nbsp; {{ info.address }}
        </li>
        <li class="text-sm border-0 list-group-item ps-0">
          <strong class="text-dark">Telephone :</strong> &nbsp; {{ info.telephone }}
        </li>
        <li class="text-sm border-0 list-group-item ps-0">
          <strong class="text-dark">Email:</strong> &nbsp; {{ info.email }}
        </li>
        <li class="text-sm border-0 list-group-item ps-0">
          <strong class="text-dark">password:</strong> &nbsp; {{ info.password }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>


export default {
  name: "ProfileInfoCard",
  components: {
  
  },
  props: ['info'],
};
</script>
