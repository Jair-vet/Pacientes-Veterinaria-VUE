<script setup>
import { ref, reactive, watch, onMounted } from "vue";
import { uid } from 'uid'
import Header from "./components/Header.vue"
import Formulario from "./components/Formulario.vue"
import Paciente from "./components/Paciente.vue"

const pacientes = ref([])

const paciente = reactive({
    id: null,
    nombre: '',
    propietario: '',
    email: '',
    alta: '',
    sintomas: ''                 
})

watch(pacientes, () => {
    guardarLocalStorage()
  }, {
    deep: true
})


const guardarLocalStorage = () => {
    localStorage.setItem('pacientes', JSON.stringify(pacientes.value)) // Convertir a string y poderlo almacenar
}


// Asignar cuando el componente se monta por primera vez
onMounted(() => {

    const pacientesStorage = localStorage.getItem('pacientes')
    if(pacientesStorage){
      pacientes.value = JSON.parse(pacientesStorage) // Volvemos a convertir a un arreglo y lo agregamos

    }
})

const guardarPaciente = () => {
  if(paciente.id){
    const { id } = paciente
    const i = pacientes.value.findIndex(pacienteState => pacienteState.id === id) // Retorna la posicion del elemento
    pacientes.value[i] = {...paciente}

  } else{ 
    pacientes.value.push({
      ...paciente, // copia del paciente
      id: uid()
    })
  }

  // Otra Forma de limpiar
  Object.assign(paciente, {
    nombre: '',
    propietario: '',
    email: '',
    alta: '',
    sintomas: '',
    id: null
  })
}

const actualizarPaciente = (id) => {
  const pacienteEditar = pacientes.value.filter( paciente => paciente.id === id )[0]
  Object.assign(paciente, pacienteEditar)
}

const eliminarPaciente = (id) => {
  pacientes.value = pacientes.value.filter( paciente => paciente.id !== id )
}
</script>

<template>

  <div class="container mx-auto mt-20">
    <Header />


    <div class="mt-12 md:flex">
      <Formulario 
        v-model:nombre="paciente.nombre"
        v-model:propietario="paciente.propietario"
        v-model:email="paciente.email"
        v-model:alta="paciente.alta"
        v-model:sintomas="paciente.sintomas"
        @guardar-paciente="guardarPaciente"
        :id="paciente.id"
      />

      <div class="md:w-1/2 md:pl-10 pl-0 md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center">Administra tus pacientes</h3>
           
        <div v-if="pacientes.length > 0">
          <p class="mt-5 mb-10 text-center text-lg font-bold">
                Información de 
                <span class="text-sky-500 font-bold">Pacientes</span>
          </p>
          <Paciente
              v-for="paciente in pacientes"
              :key="paciente.id"
              :paciente="paciente"
              @actualizar-paciente="actualizarPaciente"
              @eliminar-paciente="eliminarPaciente"
          />
        </div>

        <p v-else class="mt-10 text-2xl text-center">No hay Pacientes</p>
      </div>

    </div> 

  </div>  
</template>

   