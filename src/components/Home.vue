<template>
    <div class="home">
        <section class="test-header">
            <h1>Ejercicio de algoritmos: <span>Estrellas</span></h1>
            <h2>
                <p>Enunciado:</p> 
                <img src="../assets/EstrellasEjercicio.png">
            </h2>
        </section>
        <section>
            <label for="row-value">
                <span>N&uacute;mero de filas</span>
                <input type="number" v-model="rowValue" name="row-value">
            </label>
            <label for="column-value">
                <span>N&uacute;mero de columnas</span>
                <input type="number" v-model="columnValue" name="column-value">
            </label>
            
        </section>
        <section>
            <entry-matrix v-on:output="toggleOutput(true, $event)" v-on:cancel="toggleOutput(false, null)"
            :rows="parseInt(rowValue)" 
            :cols="parseInt(columnValue)" 
            :isInvalid="isInvalid()">
            </entry-matrix>
        </section>
        <section v-if="showOutput">
            <output-matrix :entry-matrix="entryMatrix"></output-matrix>
        </section>
    </div>
</template>

<script>
import EntryMatrix from './EntryMatrix.vue';
import OutputMatrix from './OutputMatrix.vue';

export default {
    name: 'home',
    components: {
        EntryMatrix,
        OutputMatrix,
    },
    data: function() {
        return {
            rowValue: 0,
            columnValue: 0,
            showOutput: false,
            entryMatrix: []
        }
    },
    methods: {
        isInvalid: function(){
            return (this.rowValue && this.columnValue) < 10 && (this.rowValue && this.columnValue) > 0? true : false
        },
        toggleOutput: function(value, evt){
            if(value){
                this.entryMatrix = evt;
            } else {
                this.entryMatrix = [];
            }
            this.showOutput = value;
        }
    }
}
</script>