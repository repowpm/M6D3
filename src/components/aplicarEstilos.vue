<template>
    <div class="container"> 
      <h1>{{ msg }}</h1>
      <div class="row">
        <div class="formulario col-md-6">
          <form>
            <div class="mb-3 form-group">
                <label for="">Color de Fondo</label>
                <input v-model="colorFondo" type="color" class="form-control" id="">
            </div>
            <div class="mb-3 form-group">
                <label for="colorTexto">Color de Texto</label>
                <input v-model="colorTexto" type="color" class="form-control" id="">
            </div>
            <div class="mb-3 form-group form-check">
                <input v-model="mostrarTexto" type="checkbox" class="form-check-input" id="">
                <label for="">Mostrar texto</label>
            </div>
            <div class="mb-3 form-group">
                <label for="borde">Borde</label>
                <input type="range" id="" v-model="borde" min="1" max="100" class="form-range">
                <span>{{ borde }}%</span>
            </div>
            <div class="mb-3 form-group">
                <label for="grosorBorde">Grosor del Borde</label>
                <input type="range" id="" v-model="grosorBorde" min="1" max="20" class="form-range">
                <span>{{ grosorBorde }}px</span>
            </div>
            <div class="mb-3 form-group">
                <label for="contenidoTexto">Contenido textual</label>
                <textarea v-model="contenidoTexto" id="" rows="3" class="form-control"></textarea>
            </div>
            <div class="mb-3 form-group">
                <label for="tipo">Tipografía</label>
                <select v-model="tipo" class="form-select" id="">
                    <option v-for="t in tipografia" :key="t" :value="t">{{ t }}</option>
                </select>
            </div>
            <div class="mb-3 form-group form-check">
                <input type="checkbox" v-model="opaco" class="form-check-input" id="">
                <label for="" class="form-check-label">Opaco</label>
            </div>
            <div class="mb-3 form-group">
              <label class="text-center">Tamaño de letra</label>
              <div class="d-flex justify-content-center">
              <div class="form-check">
                <input type="radio" class="form-check-input" id="" value="25px" v-model="tamanoLetra">
                <label class="form-check-label" for="">Pequeño</label>
              </div>
              <div class="form-check">
                <input type="radio" class="form-check-input" id="" value="75px" v-model="tamanoLetra">
                <label class="form-check-label" for="">Mediano</label>
              </div>
              <div class="form-check">
                <input type="radio" class="form-check-input" id="" value="150px" v-model="tamanoLetra">
                <label class="form-check-label" for="">Grande</label>
              </div>
            </div>
            </div>
          </form>
        </div>
            <div class="col-6">
                <div class="figura"
                :style="{
                      backgroundColor: colorFondo, 
                      border: `${grosorBorde}px solid black`,
                      borderRadius: `${borde}%`,
                      opacity: opaco ? 0.3 : 1, 
                      padding: '50px',
                      display: 'flex',
                      justifyContent: 'center',
                      alignItems: 'center',
                        }">
                    <h1 v-show="mostrarTexto"  :style="{color:colorTexto, fontSize:tamanoLetra, fontFamily:tipo}">{{ contenidoTexto }}</h1>
                </div>

            </div>
        </div>
    </div>
   
  </template>
  
  <script>
  export default {
    name: 'aplicarEstilos',
    data() {
        return {
            colorFondo: '',
            colorTexto: "",
            mostrarTexto: 'True',
            borde: 1,
            grosorBorde: 1,
            contenidoTexto: '',
            tipo: "Arial",
            tipografia: ['Arial', 'Courier New', 'Georgia', 'Times New Roman', 'Verdana', 'cursive'],
            opaco: 'false',
            tamanoLetra: '',
            }
            },
    props: {
      msg: String
    }
  }
  </script>
  
  <style>
  .formulario{
    background-color: #2f4f4e; 
    padding: 20px; 
    border-radius: 10px;
  }
  label{
    color: white;
    display: block;
    text-align: left; 
  }
  span{
    color: white;
  }
  .figura{
    height: 50vh;
    width: 30vw;
  }
  </style>
  