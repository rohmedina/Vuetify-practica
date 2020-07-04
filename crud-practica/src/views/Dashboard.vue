<template>
  <v-container>
    <v-row wrap>
      <v-col cols="12" md="6" sm="6" v-if="formAgregar">
        <v-card class="mb-3 pa-4">
          <v-form @submit.prevent="agregarTarea">
            <v-text-field label="Titulo de tarea" v-model="titulo"> </v-text-field>
            <v-textarea label="Descripción de tarea" v-model="descripcion"></v-textarea>
            <v-btn block color="success" type="submit">agregar tarea</v-btn>
          </v-form>
        </v-card>
      </v-col>

      <v-col cols="12" md="6" v-if="!formAgregar">
        <v-card class="mb-3 pa-4">
          <v-form @submit.prevent="editarTarea">
            <v-text-field label="Titulo de tarea" v-model="titulo"> </v-text-field>
            <v-textarea label="Descripción de tarea" v-model="descripcion"></v-textarea>
            <v-btn block color="warning" type="submit">editar tarea</v-btn>
          </v-form>
        </v-card>
      </v-col>

      <v-col cols="12" md="6" sm="6">
        <v-card class="mb-3" v-for="(item, index) in listaTareas" :key="index">
          <v-card-text>
            <template v-if="!completada">
              <v-chip class="ma-2 ml-0" color="blue lighten-1" label text-color="white">
                <v-icon left>mdi-label</v-icon>
                {{ item.titulo }}
              </v-chip>

              <p>{{ item.descripcion }}</p>
            </template>

            <template v-if="completada">
              <v-chip class="ma-2 ml-0" color="success" label text-color="white">
                <v-icon left>mdi-thumb-up</v-icon>
                {{ item.titulo }}
              </v-chip>

              <p>{{ item.descripcion }}</p>
            </template>

            <v-btn color="warning" class="ml-0 mr-5" @click="editar(index)">Editar</v-btn>
            <v-btn dark color="red accent-4" class="mr-5" @click="eliminarTarea(item.id)">Eliminar</v-btn>
            <v-btn color="success" @click="completarTarea(index)">Realizada</v-btn>
          </v-card-text>
        </v-card>

        <!--    <v-card class="mb-3">
          <v-card-text>
            <v-chip class="ma-2 ml-0" color="pink" label text-color="white">
              <v-icon left>mdi-label</v-icon>
              Titulo de tarea #2
            </v-chip>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quo molestiae quisquam,</p>

            <v-btn color="warning" class="ml-0 mr-5">Editar</v-btn>
            <v-btn color="error">Eliminar</v-btn>
          </v-card-text>
        </v-card> -->
      </v-col>
    </v-row>

    <v-snackbar v-model="snackbar" :value="true" absolute center shaped top bottom color="red darken-1">
      {{ mensaje }}

      <template v-slot:action="{ attrs }">
        <v-btn dark text v-bind="attrs" @click="snackbar = false">
          Cerrar
        </v-btn>
      </template>
    </v-snackbar>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      listaTareas: [
        { id: 1, titulo: "Titulo Tarea #1", descripcion: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quo molestiae quisquam" },
        { id: 2, titulo: "Titulo Tarea #2", descripcion: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quo molestiae quisquam" },
      ],
      titulo: "",
      descripcion: "",
      snackbar: false,
      mensaje: "",
      formAgregar: true,
      indexTarea: "",
      completada: false,
    };
  },
  methods: {
    agregarTarea() {
      //  console.log(this.titulo, this.descripcion);
      if (this.titulo === "" || this.descripcion === "") {
        this.snackbar = true;
        this.mensaje = "Debes llenar todos los campos!";
      } else {
        this.listaTareas.push({
          id: Date.now(),
          titulo: this.titulo,
          descripcion: this.descripcion,
        });
        this.titulo = "";
        this.descripcion = "";
        this.snackbar = true;
        this.mensaje = "Tarea Agregada!";
      }
    },
    eliminarTarea(id) {
      this.listaTareas = this.listaTareas.filter((e) => e.id != id);
      this.snackbar = true;
      this.mensaje = "Tarea Eliminada!";
    },
    editar(index) {
      this.formAgregar = false;
      this.titulo = this.listaTareas[index].titulo;
      this.descripcion = this.listaTareas[index].descripcion;
      this.indexTarea = index;
    },
    editarTarea() {
      this.listaTareas[this.indexTarea].titulo = this.titulo;
      this.listaTareas[this.indexTarea].descripcion = this.descripcion;
      this.formAgregar = true;
      this.titulo = "";
      this.descripcion = "";
      this.snackbar = true;
      this.mensaje = "Tarea Editada!";
    },
    completarTarea(index) {
      console.log(index);

      this.index = this.completada = true;
    },
  },
};
</script>
