<template>
  <div class="container">
    <form @submit.prevent="sendEmail">
      <label>What Kind of Data You Request:</label>
      <input
        type="text"
        v-model="kind"
        name="kind"
        placeholder="eg. case, agency, program, contact, etc.,"
      />

      <label>Purposes of the Data Request:</label>
      <input
        type="text"
        v-model="purpose"
        name="purpose"
        placeholder="eg. call for government funding"
      />

      <label>Report template you choose: </label
      ><a
        target="_blank"
        href="https://drive.google.com/drive/u/1/folders/1GxDlc89yHR6hdbm3Jeumjlvx2QhgHLPN"
        >(Choose from the Google Drive)
      </a>
      <input
        type="text"
        v-model="template"
        name="template"
        placeholder="eg. template 1, 2, 3 please choose from the Google Drive folder"
      />

      <label>Data Range: </label>
      <input
        type="text"
        v-model="dataRange"
        name="dataRange"
        placeholder="eg. August 2020 - March 2021"
      />

      <label>Data Frequency: </label>
      <input
        type="text"
        v-model="dataFrequency"
        name="dataFrequency"
        placeholder="eg. Monthly, Weekly, Daily, etc.,"
      />

      <label>Fields you want to add from the template</label>
      <input
        type="text"
        v-model="add"
        name="add"
        placeholder="if you select a template"
      />

      <label>Fields you want to remove from the template:</label>
      <input
        type="text"
        v-model="remove"
        name="remove"
        placeholder="if you select a template"
      />

      <label>Severity Level:</label>
      <input
        type="text"
        v-model="severity"
        name="severity"
        placeholder="eg. High, Medium, Low"
      />

      <hr />

      <label>Name</label>
      <input type="text" v-model="name" name="name" placeholder="Your Name" />

      <label>Email</label>
      <input
        type="email"
        v-model="email"
        name="email"
        placeholder="Your Email"
      />
      <label>Message</label>
      <textarea
        name="message"
        v-model="message"
        cols="30"
        rows="5"
        placeholder="Message to me, especially if you did not choose a template"
      >
      </textarea>

      <input type="submit" value="Request the Data" />
    </form>
  </div>
</template>

<script>
import emailjs from "emailjs-com";

export default {
  name: "ContactUs",
  data() {
    return {
      name: "",
      email: "",
      message: "",
      kind: "",
      purpose: "",
      template: "",
      dataRange: "",
      dataFrequency: "",
      add: "",
      remove: "",
      severity: "",
    };
  },
  methods: {
    sendEmail(e) {
      try {
        emailjs.sendForm(
          "service_g2dn319",
          "template_ydbv6xp",
          e.target,
          "user_0K7gji1oiihV7OqyPPlTZ",
          {
            name: this.name,
            email: this.email,
            message: this.message,
            kind: this.kind,
            purpose: this.purpose,
            template: this.template,
            dataRange: this.dataRange,
            dataFrequency: this.dataFrequency,
            add: this.add,
            remove: this.remove,
            severity: this.severity
          }
        );
        console.log("it works!!!");
      } catch (error) {
        console.log({ error });
      }
      // Reset form field
      this.name = "";
      this.email = "";
      this.message = "";
      this.kind = "";
      this.purpose = "";
      this.message = "";
      this.template = "";
      this.dataRange = "";
      this.dataFrequency = "";
      this.add = "";
      this.remove = "";
      this.severity = "";
    },
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}

label {
  float: left;
}
input[type="text"],
[type="email"],
textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
  resize: vertical;
}

input[type="submit"] {
  background-color: #4caf50;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type="submit"]:hover {
  background-color: #b8c7b9;
}

.container {
  display: block;
  margin: auto;
  text-align: center;
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
  width: 50%;
}
</style>
