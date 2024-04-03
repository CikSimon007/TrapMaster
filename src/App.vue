<template>
  <div class="main-container">
    <div>
      <nav>
      <h1>TRAP MANAGER</h1>
        <div class="buttons-container">
          <div class="nav-button" :class="{ 'active-border':  floor1Active}" @click="changeFloor('floor1')">FLOOR 1</div>
          <div class="nav-button" :class="{ 'active-border':  floor2Active}" @click="changeFloor('floor2')">FLOOR 2</div>
          <div class="nav-button" :class="{ 'active-border':  overwiew}" @click="chagneToOverwiew('overwiew')">OVERWIEW</div>
          
        </div>
      </nav>
    </div>


    <div>
      <div v-if="currentFloor === 'floor1'"><FirstFloor /></div>
      <div v-if="currentFloor === 'floor2'"><SecondFloor /></div>
      <div v-if="overwiew == true"><TrapModal /></div>
    </div>
  </div>
</template>

 
<script>
import TrapModal from './components/TrapModal.vue';
import FirstFloor from './components/FirstFloor.vue';
import SecondFloor from './components/SecondFloor.vue';

export default {
  data() {
    return {
      currentFloor: 'floor1',
      floor1Active: true,
      floor2Active: false,
      overwiew: false,
    };
  },
  components: {
    FirstFloor,
    SecondFloor,
    TrapModal,
  },
  methods: {
    changeFloor(floor) {
      this.currentFloor = floor;
      this.floor1Active = this.currentFloor === 'floor1';
      this.floor2Active = this.currentFloor === 'floor2';
      this.overwiew = false;
      console.log(`Spustená časť pre ${this.currentFloor} a jej hodnota je:`);
      console.log(this.floor1Active);
      console.log(this.floor2Active);
      console.log("Zavolaná metóda changeFloor");
    },
    chagneToOverwiew(overwiew) {
      this.currentFloor = '';
      this.floor1Active = false;
      this.floor2Active = false;
      this.overwiew = true;
      console.log(`Spustená časť pre ${this.currentFloor} a jej hodnota je:`);
      console.log(this.floor1Active);
      console.log(this.floor2Active);
      console.log("Zavolaná metóda changeFloor");
    },
  },
};
</script>

<style scoped>


h1{
  margin: 0px;
  font-size: 20px;
  margin-left: 10px;
}

nav{
  background-color: #288ccf;
  width: 100%;
  height: 70px;
  padding-top: 10px;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: 800;
  color: white;
  box-shadow: 0 4px 0px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}
.nav-button{
  border: none;
  text-align: center;
  text-decoration: none;
  margin: 10px;
  margin-left: 10px;
  margin-right: 10px;
  cursor: pointer;
}

.buttons-container{
  display: flex;
  justify-content: center;
  margin-top: 10px;
  align-items: end;
  color: white;
  font-weight: 700;
  font-size: 13px;
  font-family: Arial, Helvetica, sans-serif;
}

.active-border{
  border-bottom: 3px solid #ffffff;
}


.open-modal-button{
  cursor: pointer
}

.main-container{
  height: 100vh;
  background-color: rgb(238, 238, 238)
}

</style>