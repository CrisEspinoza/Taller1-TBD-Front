<template>
  <div class="center">
    <h2>{{title}}</h2>
    <!--//Formulario actor nuevo-->
    <form v-if="!submitted">
      <label for="nombre">
        Nombre
      </label><br>
      <input id="nombre" required type="text" v-model="actor.firstName" required /><br>
      <label for="apellido">Apellido</label><br>
      <input id="apellido" required type="text" v-model="actor.lastName" required /><br>
      <button v-on:click="sendData">Agregar actor</button>
    </form>
    <div v-if="submitted">
      <h2>¡Actor añadido!</h2>
      <!--Añadir otro actor
      <button v-on:click="refresh">Agregar otro actor</button>-->
    </div>
    </ul>
  </div>
</template>


<script>
export default {
  data(){
    //Datos objeto actor
    return{
      title:'Nuevo Actor',
      actor:{
        firstName:'',
        lastName:''
      },
      submitted: false
    }
  },

  methods:{
    //Metodo para agregar actores

    sendData() {
       this.$http.post('http://localhost:8081/actors/create', this.actor).then((response) => {
            //succes
        }, (response) => {
          //false
        });
      }
    }
}
</script>