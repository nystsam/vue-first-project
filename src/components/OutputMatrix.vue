<template>
    <div class="output-matrix">
        <div v-for="row in output">
            <span v-for="col in row">
            {{col}}
            </span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'outputMatrix',
    props: {
        entryMatrix: Array
    },
    data: function() {
        return{
            output: Array
        }
    },
    created: function(){
        // (pos(i,j) + sumatoria veciones)/5 > 10
        var result = 0;
        this.output = [];
        console.log(this.entryMatrix);
        for(var i = 0; i < this.entryMatrix.length; i++){
            var row = [];
            for(var j = 0; j < this.entryMatrix[i].length; j ++){
                result = 0;
                if(i - 1 >= 0){
                    result += this.iterate(i - 1, j);
                }
                result += this.iterate(i, j);

                if(i + 1 < this.entryMatrix.length) {
                    result += this.iterate(i + 1, j);
                }
                
                if(result/5 > 10)
                    row.push('*');
                else
                    row.push('x');
            }
            this.output.push(row);
        }
    },
    methods: {
        iterate: function(row, col){
            var result = 0;
            for(var k = col - 1; k <= col + 1; k ++){
                if(k >= 0 && k < this.entryMatrix[row].length){
                    result += this.entryMatrix[row][k];
                }
            }
            return result;
        }
    }
}
</script>