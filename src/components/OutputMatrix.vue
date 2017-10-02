<template>
    <div class="output-matrix">
        Salida
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
            
        }
    },
    created: function(){
        console.log(this.entryMatrix);
    }
}
</script>