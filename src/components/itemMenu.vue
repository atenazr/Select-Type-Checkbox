<template>
    <div 
    class="item-menu d-flex flex-row align-items-center justify-content-start p-2 w-100">
       <div>
             <i :class="data.icon"></i>
        </div>

        <div class="mx-auto">
            {{ data.title }}
        </div>

        <div class="number-item">
               <input class="mw-100" type="number" :value="data.number" >
        </div>                   
                    
    </div>
</template>

<script>
export default {
    props:[
        'data'
    ]

}
</script>

<style scoped>
.item-menu{
    border-bottom: .1rem solid #98C1D9;
    color: #E0FBFC;
    font-size: 1.1rem;
    cursor: pointer;
}
.item-menu i{
    margin-right: .5rem;
}
.item-menu .number-item{
    max-width: 20%;
}
.item-menu .number-item input{
    font-size: .85rem;
    background: transparent;
    outline: none;
    padding: .2rem;
    color: #E0FBFC;
}
</style>