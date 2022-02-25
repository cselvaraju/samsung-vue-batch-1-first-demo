<template>
  <h1>Welcome to Vue</h1>
  <p>
    Your message is
    {{ msgLanguage === "hindi" ? hindiMessage : punjabiMessage }}
  </p>
  <p>
    <button @click="changeLanguage">{{ btnText }}</button>
  </p>
  <p>
    <button @click="toggleActorList">Toggle Actor List</button>
  </p>
  <div v-if="isActorListVisible">
    <h2>List of Actors</h2>
    <ul>
      <li v-for="(actor, index) in actorList" v-bind:key="index">
        {{ index + 1 }} Name: {{ actor.name }} City: {{ actor.city }}
      </li>
    </ul>
  </div>
  <div>
    <h2>New Actor</h2>
    <label>
      Name
      <input type="text" v-model="newActor.name" />
      <br />
      Name: {{ newActor.name }}
    </label>
    <br />
    <label>
      City
      <input
        type="text"
        :value="newActor.city"
        @input="updateActorCity($event)"
      />
      <br />
      City: {{ newActor.city }}
    </label>
    <br />
    <button @click="addActor">Add Actor</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      punjabiMessage: "Sat Shree Akal",
      hindiMessage: "Namaste",
      msgLanguage: "punjabi",
      btnText: "Change Language to HINDI",
      actorList: [
        { name: "Amitabh Bachhan", city: "Mumbai" },
        { name: "Kamal Hasan", city: "Chennai" },
        { name: "Deepika Padukone", city: "New Delhi" },
        { name: "Katrina Kaif", city: "London" },
        { name: "Rajnikant", city: "Chennai" },
      ],
      isActorListVisible: true,
      newActor: {
        name: "",
        city: "",
      },
    };
  },
  methods: {
    changeLanguage() {
      if (this.msgLanguage === "punjabi") {
        this.msgLanguage = "hindi";
        this.btnText = "Change Language to PUNJABI";
      } else {
        this.msgLanguage = "punjabi";
        this.btnText = "Change Language to HINDI";
      }
    },

    toggleActorList() {
      this.isActorListVisible = !this.isActorListVisible;
    },

    updateActorCity(event) {
      this.newActor.city = event.target.value;
    },

    addActor() {
      this.actorList.push(this.newActor);
      this.newActor = {
        name: "",
        city: "",
      };
    },
  },
};
</script>

<style>
h1 {
  text-align: center;
}
</style>