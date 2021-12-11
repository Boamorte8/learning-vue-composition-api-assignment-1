<template>
  <h2>My Course Goal</h2>
  <!-- Task 1: Output your main course goal with help of the composition API -->
  <!-- Don't hardcode it into the template, instead hardcode it into the JS code -->
  <!-- <h3 v-if="showGoal">{{ goal }}</h3> -->
  <h3 v-if="dataGoal.showGoal">{{ dataGoal.goal }}</h3>
  <h3 v-if="showGoalByOptions">{{ goalByOptions }}</h3>
  <!-- Task 2: Toggle (show/ hide) the goal with help of the button  -->
  <button @click="toggleGoal">Toggle Goal</button>
  <button @click="toggleGoalByOptions">Toggle Goal By Options API</button>
  <!-- Task 3: Manage data in three ways -->
  <!-- => Separate refs -->
  <!-- => Ref Object -->
  <!-- => Reactive Object -->
  <!-- Task 4: Also solve the assignment with the Options API -->
</template>

<script>
import { reactive, ref } from 'vue';

export default {
  setup() {
    // const goal = ref("My main course goal is to become a full-stack developer (Separate refs)");
    // const showGoal = ref(false);
    const dataGoalRef = {
      goal: ref("My main course goal is to become a full-stack developer (Ref Object)"),
      showGoal: ref(true),
    };
    const dataGoal = reactive({
      goal: "My main course goal is to become a full-stack developer (Reactive Object)",
      showGoal: true,
    });

    const toggleGoal = () => {
      // showGoal.value = !showGoal.value;
      dataGoalRef.showGoal.value = !dataGoalRef.showGoal.value;
      dataGoal.showGoal = !dataGoal.showGoal;
    };

    return {
      goal: dataGoalRef.goal,
      showGoal: dataGoalRef.showGoal,
      dataGoal,
      toggleGoal,
    };
  },
  data() {
    return {
      goalByOptions: "My main course goal is to become a full-stack developer (Options API)",
      showGoalByOptions: true,
    };
  },
  methods: {
    toggleGoalByOptions() {
      this.showGoalByOptions = !this.showGoalByOptions;
    },
  },
}
</script>

<style>
html {
  font-family: sans-serif;
}
body {
  margin: 3rem;
  text-align: center;
}
</style>