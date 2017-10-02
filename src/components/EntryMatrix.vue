<template>
    <div class="entry-matrix">
        <div class="entry-creation">
            <button @click="createMatrix()" :disabled="!isInvalid">Crear regi&oacute;n</button>
        </div>
        <section v-if="matrix.length > 0">
            <div class="entry-matrix-container">
                <div v-for="row in matrix">
                    <span v-for="col in row">
                        {{col}}
                    </span>
                </div>
            </div>
            <div class="output-creation">
                <button @click="$emit('output', matrix)">Buscar estrellas</button>
            </div>
        </section>
    </div>
</template>

<script>
export default {
    name: 'entryMatrix',
    props: {
        rows: Number,
        cols: Number,
        isInvalid: Boolean,
        /*
        rows: {
            type: Number,
            validator: function(value) {
                return (value < 10 && value > 0);
            }
        },
        cols: {
            type: Number,
            validator: function(value) {
                return (value < 10 && value > 0);
            }
        },
        */
    },
    data: function() {
        return {
            matrix: []
        }
    },
    methods: {
        createMatrix: function() {
            this.matrix = [];
            this.$emit('cancel')
            for(var i = 0; i < this.rows; i++){
                var _row = [];
                for(var j = 0; j < this.cols; j++){
                    var _intensity = Math.round(Math.random() * 20);
                    _row.push(_intensity);
                }
                this.matrix.push(_row);
            }
        }
    }
}
</script>
