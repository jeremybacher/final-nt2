<template>
  <section class="final">
    <div class="opciones">
      <label for="color">Color</label>
      <input
        type="text"
        id="color"
        class="form-control"
        v-model="color" >
      <label for="fondo">Fondo</label>
      <input
        type="text"
        id="fondo"
        class="form-control"
        v-model="fondo" >
      <label for="size">Size</label>
      <input
        type="text"
        id="size"
        class="form-control"
        v-model="size" >
    </div>
    <hr />
    <label for="texto">Texto</label>
    <input
      type="text"
      id="texto"
      class="form-control"
      v-model="texto" 
      :style="{
          'color': color,
          'background-color': fondo,
          'font-size': size ? size + 'px' : '14px'
        }">
    <div v-if="calcularCantidadPalabras > 0">
      <p> Cantidad de palabras {{ calcularCantidadPalabras }}</p> 
    </div>
    <div class="multiple-choice">
      <table>
        <tr>
          <th>Preguntas</th>
          <th>Respuestas</th>
        </tr>
        <tr
          v-for="(question, index) in questions"
          :key="index"
        >
          <td>{{ question.question }}</td>
          <td >{{ question.answers.join(",") }}</td>
        </tr>
      </table>
    </div>
  </section>
</template>

<script>
  export default  {
    name: 'final',
    props: [],
    mounted () {

    },
    data () {
      return {
        color: "",
        fondo: "",
        size: "",
        texto: "",
        questions: [
          {
            question: 1,
            answers: ['B'],
          }, 
          {
            question: 2,
            answers: ['C'],
          }, 
          {
            question: 3,
            answers: ['B'],
          }, 
          {
            question: 4,
            answers: ['A'],
          }, 
          {
            question: 5,
            answers: ['A', 'D'],
          },        
        ]
      }
    },
    methods: {

    },
    computed: {
      calcularCantidadPalabras() {
        let cantPalabras = this.texto.trim()
        if (cantPalabras != "") {
          cantPalabras = cantPalabras.replace(/[ ]+/g, " ")
          cantPalabras = cantPalabras.split(" ")
          return cantPalabras.length
        }
        return 0
      }
    }
  }

</script>

<style scoped lang="css">
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
</style>
