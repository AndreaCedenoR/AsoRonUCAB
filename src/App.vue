<template>
  <div>
    <!-------------------------------------- Esto seria los rol --------------------------------------->
    <Header></Header>
    <div class="container">
      <div class="row">
        <div class="col-md-4 d-flex" style="margin-top:50px">
          <input type="text" id="rolNombre" class="flex-grow-1 form-control" v-model="nombreDelRol" placeholder="Nombre del Rol">
          <button class="btn btn-primary " @click="registrarRol" style="width:135px; height: 30px; margin-left:50px">Registrar</button>
        </div>
        <div class="col-md-12 text-center mt-3">
          <p>Permisos Asociados</p>
        </div>
          <div v-for="(item, index) in arrayCheckBox" :key="index" class="col-md-3 form-check form-switch">
            <input type="checkbox" class="form-check-input" v-model="item.selected">
            <label class="form-check-label">{{ item.text }}</label>
          </div>
          <!-- <button class="btn btn-primary" @click="obtenerEstadoCasillas">Obtener Estado</button> -->


      </div>
    </div>
    <!-------------------------------------- Esto seria Tienda física --------------------------------------->
    <!-- <div class="container">
        <div class="row" style="border-bottom: 2px solid black;">
            <div class="col-4 espace">
              <div class="espace" style="height: 100%;">
                  <button class="btn btn-primary" style="width: 185px; height: 65px">Agregar</button>
              </div>
            </div>
            <div class="col-4 espace">
              <div style="text-align: center;">
                <p style="margin: 5px 0; font-size: 25px;"><strong>DATOS DE CLIENTE</strong></p>
                <p style="margin: 5px 0;">NOMBRE: Andrea Cedeño</p>
                <p style="margin: 5px 0;">CEDULA: 283179652</p>
                <p style="margin: 5px 0;">TELF: 04141060970</p>
                <p style="margin: 5px 0;">DIRECCION: Caracas</p>
              </div>
            </div>
            <div class="col-4 espace" style="border: 2px solid black;">

                <div class="centered-div">
                  <p><strong>PUNTOS CLIENTE</strong></p>
                  <p>22</p>
                  <p><strong class="total">TOTAL</strong></p>
                  <p>1200 BS</p>
                  <p>33$</p>

              </div>
            </div>
        </div>
        <div class="tabla-con-scroll">
          <table  class="table mt-4">
            <thead style="border-bottom: 2px solid black;">
                <tr>
                    <th>Encabezado 1</th>
                    <th>Encabezado 2</th>
                    <th>Encabezado 3</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>Dato 1</td>
                    <td>Dato 2</td>
                    <td>Dato 3</td>
                </tr>
                <tr>
                    <td>Dato 4</td>
                    <td>Dato 5</td>
                    <td>Dato 6</td>
                </tr>
                <tr>
                    <td>Dato 1</td>
                    <td>Dato 2</td>
                    <td>Dato 3</td>
                </tr>
                <tr>
                    <td>Dato 4</td>
                    <td>Dato 5</td>
                    <td>Dato 6</td>
                </tr>
                <tr>
                    <td>Dato 1</td>
                    <td>Dato 2</td>
                    <td>Dato 3</td>
                </tr>
                <tr>
                    <td>Dato 4</td>
                    <td>Dato 5</td>
                    <td>Dato 6</td>
                </tr>
                <tr>
                    <td>Dato 1</td>
                    <td>Dato 2</td>
                    <td>Dato 3</td>
                </tr>
                <tr>
                    <td>Dato 4</td>
                    <td>Dato 5</td>
                    <td>Dato 6</td>
                </tr>
                <tr>
                    <td>Dato 19</td>
                    <td>Dato 29</td>
                    <td>Dato 39</td>
                </tr>
                <tr>
                    <td>Dato 49</td>
                    <td>Datogfffff 59</td>
                    <td>Dato 69</td>
                </tr>
            </tbody>
          </table>
        </div>
        <div class="row">
          <div class="col-12 azul-inferior">
            <button class="boton-canjear btn btn-primary" @click="modalCanjear">Canjear</button>
            <button class="boton-pagar btn btn-primary">Pagar</button>
          </div>
          <div v-if="modalVisible" class="modal">
            <div class="modal-content">
              <span class="close" @click="closeModal">&times;</span>
              <div class="modal-inner-content">
                <p class="modal-title total">Puntos disponibles</p>
                <p class="modal-number centered-div">13</p>
                <input type="text" class="modal-input" placeholder="Ingrese un valor" />
                <div class="modal-buttons">
                  <button class="btn btn-primary btn_position" >Canjear</button>
                  <button class="btn btn-primary btn_position" style="margin-left:30px"  @click="closeModal">Cancelar</button>
                </div>
              </div>
            </div>
          </div>
        </div>
    </div> -->
  </div>
</template>

<script>



  import Header from './shared/head.shared.vue';
  export default {
  components: {
    Header
  },
  data(){
    return {
        modalVisible: false,
        arrayCheckBox :[
        {value: 'Crear_producto', text: 'Crear producto', selected: false},
        {value: 'Editar_producto', text: 'Editar producto', selected: false},
        {value: 'Eliminar_producto', text: 'Eliminar producto', selected: false},
        {value: 'Registrar_empleado', text: 'Registrar empleado', selected: false},
        {value: 'Editar_empleado', text: 'Editar empleado', selected: false},
        {value: 'Eliminar_empleado', text: 'Eliminar empleado', selected: false},
        {value: 'Crear_proveedor', text: 'Crear proveedor', selected: false},
        {value: 'Editar_proveedor', text: 'Editar proveedor', selected: false},
        {value: 'Eliminar_proveedor', text: 'Eliminar proveedor', selected: false},
        {value: 'Registrar_cliente', text: 'Registrar cliente', selected: false},
        {value: 'Editar_cliente', text: 'Editar cliente', selected: false},
        {value: 'Eliminar_cliente', text: 'Eliminar cliente', selected: false},
        {value: 'Registrar_evento', text: 'Registrar evento', selected: false},
        {value: 'Editar_evento', text: 'Editar evento', selected: false},
        {value: 'Eliminar_evento', text: 'Eliminar evento', selected: false},
        {value: 'Registrar_inventario', text: 'Registrar inventario', selected: false},
        {value: 'Editar_inevntario', text: 'Editar inventario', selected: false},
        {value: 'Eliminar_inventario', text: 'Eliminar inventario', selected: false},
        {value: 'Registrar_rol', text: 'Registrar rol', selected: false},
        {value: 'Editar_rol', text: 'Editar rol', selected: false},
        {value: 'Eliminar_rol', text: 'Eliminar rol', selected: false},
      ]
    };
  },

  methods: {
    modalCanjear() {
      this.modalVisible = true;
      console.log('funciona el click')
    },
    closeModal() {
      this.modalVisible = false;
    },
    obtenerEstadoCasillas() {
    const a = []
    this.arrayCheckBox.forEach((item, index) => {
      a.push(this.arrayCheckBox[index].selected)
    });
    console.log(a);
    setTimeout(() => {
      this.arrayCheckBox.forEach((item, index) => {
      this.arrayCheckBox[index].selected = false;
      });
    }, 2000);
    },
    async getMonitor() {
      // https://bcv-api.deno.dev/v1/exchange
      const api = 'https://pydolarvenezuela-api.vercel.app/api/v1/dollar/';
      try {
        const response = await this.getContentPage(api);
        const allMonitors = response['monitors'];
        console.log(allMonitors)
        const monitorData = allMonitors['bcv'];
        console.log(monitorData.price);
        this.orden=[];
        console.log(this.orden);
        this.orden.push({
                    idProducto: 0,
                    idCliente: 1,
                    nombre: 0,
                    precio: 1,
                    nombreImagen: 0,
                    stock: 1,
                    cantidad: 1,
                    total: 0,
                });
        console.log(this.orden);
        return monitorData;
      } catch (error) {
         console.error(`KeyError: ${error.message}`);
      }
    },
    async getContentPage(url) {
      try {
        const response = await fetch(url);

        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        return response.json();
      } catch (error) {
        console.error(`Error fetching data: ${error.message}`);
        throw error;
      }
    },
  }
};

</script>






<style>

 /******************** Estos son los estilos de tienda física ***********************************/
.espace{
  height: 25vh;
  display: flex;
  align-items: center;
  justify-content: center;
}


.tabla-con-scroll {
  max-height: 49vh;
  overflow-y: auto;
}

.tabla-con-scroll thead {
    position: sticky;
    top: 0;
    background-color: #fff;
}

.azul-inferior {
  height: 25vh;
  position: relative;
  padding-right: 30px;
  display: flex;
  align-items: center;
  justify-content: center;

}

.boton-canjear,
.boton-pagar {
  position: absolute;
}

.boton-canjear {
  right: 45px;
  width: 150px;
  height: 60px;
  margin-right: 150px;
}

.boton-pagar {
  right: 15px;
  width: 150px;
  height: 60px;

}

.botones-container {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  height: 100%;
}

.centered-div {
  text-align: center;
}

.centered-div p {
  margin: 0;
  font-size: 20px;
}

.centered-div p strong {
  font-weight: bold;
}

.total {
  font-size: 25px;
  font-weight: bold;
  color: black;
}



/********************************** Estilo para el modal ***********************************/
.modal {
  display: flex;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
}

/* Estilo para el contenido del modal */
.modal-content {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #fff;
  padding: 20px;
  text-align: center;
  width: 35%;
}

/* Estilo para el botón de cerrar el modal */
.close {
  position: absolute;
  top: 0;
  right: 0;
  padding: 10px;
  cursor: pointer;
}

.modal-input{

}

.btn_position{
  width: 135px;
  height: 50px;
}

</style>
