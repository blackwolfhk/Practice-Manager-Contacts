<template>
  <div class="container mt-3">
    <div class="row">
      <div class="col">
        <p class="h3 text-success fw-bold">Edit Contact</p>
        <p class="fst-italic">
          akjhflbkjhgkbkahvfblakdhfbvakdfhbvlahfdbvlafhvblafvhalfva;
        </p>
      </div>
    </div>
    <div class="container mt-3">
      <div class="row">
        <div class="col-md-4">
          <form>
            <div class="mb-2">
              <input
                v-model="contact.name"
                type="text"
                class="form-control"
                placeholder="Name"
              />
            </div>
            <div class="mb-2">
              <input
                v-model="contact.photo"
                type="text"
                class="form-control"
                placeholder="Photo URL"
              />
            </div>
            <div class="mb-2">
              <input
                v-model="contact.email"
                type="email"
                class="form-control"
                placeholder="Email"
              />
            </div>
            <div class="mb-2">
              <input
                v-model="contact.mobile"
                type="number"
                class="form-control"
                placeholder="Mobile"
              />
            </div>
            <div class="mb-2">
              <input
                v-model="contact.company"
                type="text"
                class="form-control"
                placeholder="Company"
              />
            </div>
            <div class="mb-2">
              <input
                v-model="contact.title"
                type="text"
                class="form-control"
                placeholder="Title"
              />
            </div>
            <div class="mb-2">
              <select
                v-model="contact.groupId"
                class="form-control"
                v-if="groups.length > 0"
              >
                <option value="">Select Group</option>
                <option
                  :value="group.id"
                  v-for="group of groups"
                  :key="group.id"
                >
                  {{ group.name }}
                </option>
              </select>
            </div>
            <div class="mb-2">
              <input type="submit" class="btn btn-success" value="Update" />
            </div>
          </form>
        </div>

        <div class="col-md-4">
          <img
            src="https://www.w3schools.com/howto/img_avatar.png"
            alt=""
            class="contact-img"
          />
        </div>
      </div>
    </div>
  </div>

  <!-- <pre>{{ contactId }}</pre> -->
  <pre>{{ contact }}</pre>
</template>

<script>
import { ContactService } from "@/services/ContactService";

export default {
  name: "EditContact",
  data: function () {
    return {
      contactId: this.$route.params.contactId,
      loading: false,
      contact: {},
      errorMessage: null,
      groups: [],
    };
  },
  created: async function () {
    try {
      this.loading = true;
      let response = await ContactService.getContact(this.contactId);
      let groupResponse = await ContactService.getAllGroups();
      this.contact = response.data;
      this.group = groupResponse.data;
      this.loading = false;
    } catch (error) {
      console.log("error: ", error);
      this.errorMessage = error;
      this.loading = false;
    }
  },
};
</script>

<style></style>
