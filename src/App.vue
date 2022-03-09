<template>
   <KorovinskiiComponent></KorovinskiiComponent>
   <!-- <Vyatsu :results="results"></Vyatsu> -->
   <Regestration></Regestration>
    <!-- <Avtoreg></Avtoreg> -->
    <div class="dasBody">
      <div><Onecomponetn></Onecomponetn></div>
      <div class="dasHead">
        <div><Componenthead></Componenthead></div>
        <div><Dasboard></Dasboard></div>
      </div>
    </div>
</template>

<script>
import KorovinskiiComponent from 'korovinskii-component';
import Regestration from 'regestration';
import axios from 'axios';
// import Avtoreg from 'avtoreg';
// import Vyatsu from 'vytsu';
import Dasboard from 'dasboard';
import Onecomponetn from 'onecomponetn';
import Componenthead from 'componenthead';

const url = 'http://localhost:8080/admission/';

export default {
  components: {
    KorovinskiiComponent,
    // Vyatsu,
    Regestration,
    // Avtoreg,
    Dasboard,
    Onecomponetn,
    Componenthead,
  },
  data() {
    return { KorovinskiiComponent, results: [] };
  },
  mounted() {
    axios
      .get(url)
      .then((response) => {
        console.log(response);
        this.results = response.data;
      })
      .catch((error) => console.log(error));
  },
};
</script>

<style>
.dasBody {
  margin-top: 20px;
  height: 980px;
  width: 1980px;
  display: flex;
  background: #d1d2d4;
  border-radius: 120px;
}
.dasHead {
  width: 70%;
  height: 90px;

  margin-top: 70px;
  margin-left: 70px;
}
</style>
