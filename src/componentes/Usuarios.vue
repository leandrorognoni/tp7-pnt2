<template>

  <section class="src-componentes-usuarios">
    <div class="jumbotron">
      <h2>Usuarios</h2>
      <br>

      <div v-if="this.usuarios.length" class="table-responsive">
        <table class="table table-dark">
          <tr>
            <th>Nombre</th>
            <th>Edad</th>
            <th>Email</th>

          </tr>
          <tr v-for="(usuario,index) in usuarios" :key="index">
                   <td>{{ usuario.nombre }}</td>
                  <td>{{ usuario.edad }}</td>
                  <td>{{ usuario.email }}</td>
                
              </tr>
        </table>
      </div>
      <h4 v-else class="alert alert-warning text-center">No hay usuarios disponibles</h4>


      <button class="btn btn-primary my-3 mr-3" @click="getUsuarios()">GET</button>
      <button class="btn btn-warning my-3 mr-3" @click="usuarios = []">LIMPIAR</button>
      <br>

    </div>
  </section>

</template>

<script>

  export default  {
    name: 'src-componentes-tabla',
    props: [],
    mounted () {

    },
    data () {
      return {
        usuarios: [],
        url: 'https://63588a5ec26aac906f43e3f7.mockapi.io/usuarios',
      }
    },
    methods: {
      getUsuarios() {
        this.axios(this.url)
          .then( respuesta => { this.usuarios = respuesta.data })
          .catch( error => console.error(error))
      }
    },
    computed: {

    }
}

</script>

<style scoped lang="css">
  .jumbotron {
    background-color: #0d1b30;
    font-family:  'Courier New', Courier, monospace;
  }
</style>
