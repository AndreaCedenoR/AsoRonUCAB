<template>
  <div>
    <!-------------------------------------- Esto seria los rol --------------------------------------->
    <!-- <Header></Header>
    <div class="container">
      <div class="row">
        <div class="col">

          <div v-for="(item, index) in arrayCheckBox" :key="index" class="form-check form-switch">
            <input type="checkbox" class="form-check-input" v-model="item.selected">
            <label class="form-check-label">{{ item.text }}</label>
          </div>
          <button class="btn btn-primary" @click="obtenerEstadoCasillas">Obtener Estado</button>

        </div>
      </div>
    </div> -->
    <div class="container">
        <div class="row">
            <div class="col-4 gris">
              <div class="d-flex align-items-center justify-content-center" style="height: 100%;">
                  <button class="btn btn-primary" style="width: 215px; height: 85px">Agregar</button>
              </div>
            </div>
            <div class="col-4 rojo d-flex align-items-center justify-content-center">
              <div style="text-align: center;">
                <p style="margin: 5px 0;"><strong>DATOS DE CLIENTE</strong></p>
                <p style="margin: 5px 0;">NOMBRE: Andrea Cedeño</p>
                <p style="margin: 5px 0;">CEDULA: 283179652</p>
                <p style="margin: 5px 0;">TELF: 04141060970</p>
                <p style="margin: 5px 0;">DIRECCION: Caracas</p>
              </div>
            </div>
            <div class="col-4 azul d-flex align-items-center justify-content-center" style="border: 2px solid black;">
              <div style="text-align: center;">
                <p style="margin: 5px 0;"><strong>PUNTOS CLIENTE</strong></p>
                <p style="margin: 5px 0;">22</p>
                <p style="margin: 5px 0;"><strong>TOTAL</strong></p>
                <p style="margin: 5px 0;">1200 BS</p>
                <p style="margin: 5px 0;">33$</p>
              </div>
            </div>
        </div>
        <div class="tabla-con-scroll">
          <table  class="table mt-4">
            <thead>
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
          <div class=" col-12 azul-inferior"></div>
        </div>
    </div>
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
.gris {

  height: 25vh;
}


.rojo {

  height: 25vh;
}


.azul {

  height: 25vh;
}

.azul-inferior {
  background-color: #00f;
  height: 25vh;
  position: absolute;
  bottom: 0;
  width: 88%;
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


</style>
