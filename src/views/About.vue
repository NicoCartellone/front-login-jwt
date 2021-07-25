<template>
  <div class="about">
    <h1>Ruta protegida</h1>
    {{token}}
  </div>
</template>


<script>
import {mapState} from 'vuex'
export default {
  computed: {
    ...mapState(['token'])
  },
  methods: {
    async datosProtegidos(){
      try {
        const res = await fetch('https://auth-jwt-practica.herokuapp.com/api/admin', {
          headers: {
            'Content-type': 'application/json',
            'auth-token': this.token
          }
        })
        const dataDB = await res.json()
        console.log(dataDB)
      } catch (error) {
        console.log(error)
      }
    }
  },
  created(){
    this.datosProtegidos()
  }
}
</script>