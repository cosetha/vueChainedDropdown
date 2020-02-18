<template>
  <div id="app" class="container">
    <div class="form-row">
    <div class="form-group col-md-6">
      <label for="inputProvince">Province</label>
      <select v-model="selectedProvice" class="form-control" id="inputProvince">
        <option :value="provinces.id" v-for="(provinces,index) in province" :key="index" >{{provinces.name}}</option>
      </select>
    </div>
    <div class="form-group col-md-4">
      <label for="inputCity">City</label>
      <select id="inputCity" class="form-control" v-model="selectedCity" >
        <option :value="cities.idCity" v-for="(cities,index) in citiesz" :key="index">{{cities.name}}</option>
      </select>
    </div>
    <div class="form-group col-md-2">
      <label for="inputDistrict">District</label>
     <select id="inputDistrict" class="form-control" v-model="selectedDistrict">
        <option :value="districts.idDistrict" v-for="(districts,index) in districtez" :key="index">{{districts.name}}</option>
      </select>
    </div>
  </div>
      <div class="alert alert-success alert-dismissible fade show" v-if="selectedDistrict" role="alert">
       <p>Provinsi {{provinceValue}},{{cityValue}},{{districtValue}}</p>
        <button type="button" class="close" data-dismiss="alert" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
    </div>
</template>

<script>
export default {
  name: 'App',
  components: {
   
  },
  data(){
    return{
      province: [
        { 
          id: '1',
          name: 'Jawa Timur' 
        },
        { 
          id: '2',
          name: 'Jawa Barat' 
        }
      ],
      city: [
        { 
          id: '1',
          idCity:'1',
          name: 'Malang' 
        },
        { 
          id: '1',
          idCity:'2',
          name: 'Surabaya' 
        },
        { 
          id: '2',
          idCity:'3',
          name: 'Bandung' 
        },
        { 
          id: '2',
          idCity:'4',
          name: 'Bogor' 
        }
      ],
      district: [
        { 
          id: '1',
          idDistrict:'1',
          name: 'Kec.Lowokwaru' 
        },
        { 
          id: '1',
          idDistrict:'2',
          name: 'Kec.Klojen' 
        },
        { 
          id: '2',
          idDistrict:'3',
          name: 'Kec.Rungkut' 
        },
        { 
          id: '2',
          idDistrict:'4',
          name: 'Kec.Genteng' 
        },
        { 
          id: '3',
          idDistrict:'5',
          name: 'Kec.Babalak' 
        },
        { 
          id: '3',
          idDistrict:'6',
          name: 'Kec.Bojongloa' 
        },
        { 
          id: '4',
          idDistrict:'7',
          name: 'Kec.Culug' 
        },
         { 
          id: '4',
          idDistrict:'8',
          name: 'Kec.Babakan' 
        }
      ],
      selectedDistrict: null,
      selectedProvice: null,
      selectedCity:null,
      cityValue:null,
      provinceValue:null,
      districtValue:null,
      
    }
  },
  computed:{
    districtez () {
      if (!this.selectedProvice) {
        return
      }
      return this.district.filter(c => c.id.toLowerCase().indexOf(this.selectedCity) > -1);
    },
    citiesz () {
     if (!this.selectedProvice) {
        return 
      }
      return this.city.filter(c => c.id.toLowerCase().indexOf(this.selectedProvice) > -1);
    }
    
  },
  methods:{
    filterCity:function(){

    }
  },
  watch:{
    selectedProvice:function(){
      var province = this.province.filter(c => c.id.toLowerCase().indexOf(this.selectedProvice) > -1);
      this.provinceValue = province[0].name
    },
    selectedCity:function(){
      var city = this.city.filter(c => c.idCity.toLowerCase().indexOf(this.selectedCity) > -1);
      this.cityValue = city[0].name
    },
    selectedDistrict:function(){
      var district = this.district.filter(c => c.idDistrict.toLowerCase().indexOf(this.selectedDistrict) > -1);
      this.districtValue = district[0].name
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
