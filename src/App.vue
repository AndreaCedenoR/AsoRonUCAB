<template>
  <div>
    <Header></Header>
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


*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.boton{
  margin: 10px;
}
.lbl_switch{
  display: inline-block;
  width: 55px;
  height: 30px;
  background: #aaa;
  border-radius: 100px;
  position: relative;
  cursor: pointer;
}

#btn_switch:checked~ .lbl_switch{
  background: #61A0FF;
}

.lbl_switch:after{
  position: absolute;
  content: '';
  width: 22px;
  height: 22px;
  background-color: #fff;
  border-radius: 100px;
  top: 4px;
  left: 5px;
  transition: 0.3s;
}

#btn_switch:checked~ .lbl_switch:after{
  left: 28px;
}

#btn_switch{
  display: none;
}

.toggle-button {

  padding: 10px 20px;
  margin: 5px;
  background-color: #ccc;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
}

.toggle-button.active {

  background-color: #007bff;
  color: #fff;
  transform: translateX(10px);
}

.checkbox-group {
  margin-bottom: 20px;
}

.checkbox-label {
  display: block;
  margin-bottom: 5px;
}


.checkbox-label span {
  font-weight: bold;
}


.custom-card {
  margin-top: 15px;
  background: linear-gradient(to bottom, #FFD700, #FFA500);
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
  transition: transform 0.3s;
  min-height: 200px;
}


.custom-button {
  margin-top: 20px;
  background-color: #FF4500;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: transform 0.2s;
  align-self: center;

}

.custom-buttom:hover .custom-button {
  transform: scale(1.2);
}

.card-body {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  font-size: 35px;
  color: white;
}

.item-text {
  margin-bottom: 10px;
}
</style>
