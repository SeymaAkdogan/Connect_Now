<template>
  <div class="container contact">
    <h2 class="heading" style="margin-bottom: 20px">GET IN TOUCH</h2>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum
      doloremque debitis unde nulla provident quos fugiat maxime impedit odit
      ipsam, ut iste animi illo laborum blanditiis qui iure id officia.
    </p>
    <div class="row mb-4">
      <div class="col-md-2"></div>
      <div class="col-md-8">
        <form class="formSearch" style="padding-bottom: 20px">
          <h4 class="mb-1" style="color: #ffffff">Contact Form</h4>
          <div class="row mt-1 mx-4">
            <div class="col">
              <label style="color: #ffffff" for="username"
                >Name <span style="color: #5692e8">*</span></label
              >
              <input type="text" class="form-control py-2" id="username" style="background-color: #182c47; border: none;color:#ffffff;"/>
            </div>
            <div class="col">
              <label style="color: #ffffff" for="email"
                >Email Address <span style="color: #5692e8">*</span></label
              >
              <input type="email" class="form-control py-2" id="email" style="background-color: #182c47; border: none;color:#ffffff;"/>
            </div>
          </div>
          <div class="form-group mt-4 mx-4" style="margin-bottom: 5px">
            <label for="message"
              >Message <span style="color: #5692e8">*</span></label
            >
            <input
              style="padding: 50px;background-color: #182c47; border: none;color:#ffffff;"
              type="textarea"
              class="form-control"
              id="message"
            />
          </div>
          <button type="submit" class="btnSend mt-2 px-4 py-2">Send</button>
        </form>
      </div>
      <div class="col-md-2"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "contact",
  data() {
    return {};
  },
  methods: {},
  mounted() {},
};
</script>

<style scoped>
.form-control {
  background-color: #182c47;
  border-radius: 0%;
}
.btnSend {
  background-color: #5692e8;
  color: #ffffff !important;
  border: none;
  font-family: 'Montserrat', sans-serif;
}
.heading {
  color: #ffffff;
  margin-bottom: 20px;
  font-family: 'Montserrat', sans-serif;
}
.contact {
  margin-top: 60px;
}
</style>
