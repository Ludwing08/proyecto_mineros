<template>
    <div class="container">
        <div class="row g-3">
            <div class="col-md-9">
                <input v-model="search" v-on:keyup.enter="buscar" type="text" class="form-control"
                    placeholder="Cédula del empleado" aria-label="Cedula">
            </div>
            <div class="col-md-3">
                <button v-on:click="buscar" type="submit" class="btn btn-primary">Buscar</button>
            </div>
            <div class="col-md-6" v-if="ok">
                <label for="inputEmail4" class="form-label">Nombre</label>
                <div type="email" class="form-control" id="inputEmail4" placeholder="Ej. Juan"
                    disabled> {{ empleado.NOM_EMP }}  </div>                 
            </div>

            <div class="col-md-6" v-else>
                <label for="inputEmail4" class="form-label">Nombre</label>
                <input type="email" class="form-control" id="inputEmail4" placeholder="Ej. Juan"
                    disabled>             
            </div>

            <div class="col-md-6" v-if="ok">
                <label for="inputEmail4" class="form-label">Apellido</label>
                <div type="email" class="form-control" id="inputEmail4" placeholder="Ej. Lara" disabled>
                    {{ empleado.APE_EMP }}
                </div>
            </div>
            <div class="col-md-6" v-else>
                <label for="inputEmail4" class="form-label">Apellido</label>
                <input type="email" class="form-control" id="inputEmail4" placeholder="Ej. Lara" disabled>                
            </div>

        </div>


    </div>
</template>

<script>

export default {

    data() {
        return {
            search: "",
            empleado: {},
            estado: false
        }
    },

    created: function () {
        this.buscar();
    },

    methods: {
        buscar() {
            this.axios.get(`http://localhost/PROYECTO_MINEROS/buscar.php?Cedula=${this.search}`)
            .then((response) => {
                console.log(response.data)                
                this.empleado = {}
                this.empleado = response.data;
                if (response.status == 404){
                    console.log('adsa')
                }                
            })
        }
    }
}
</script>
