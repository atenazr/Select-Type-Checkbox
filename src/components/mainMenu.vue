<template>
    <div class="main-menu mx-auto">

        <div class="container-fluid">
            
            <div class="row">
                    <div class="col-12 col-md-8 offset-md-2 py-2 ">
                        <div>
                            <div id="check-boxes" class="d-flex flex-row w-100 p-3">
                                <div>
                                    <label class="label-checkbox" for="plus"><i class="far fa-calendar-plus"></i></label>
                                    <input type="checkbox" id="plus" checked @change="setFilter">
                                </div>
                                <div class="mx-auto">
                                    <label class="label-checkbox" for="person"><i class="fas fa-universal-access"></i></label>
                                    <input type="checkbox" id="person" checked @change="setFilter">
                                </div>
                                <div>
                                    <label class="label-checkbox" for="branches"><i class="fas fa-code-branch"></i></label>
                                    <input type="checkbox" id="branches" checked @change="setFilter">
                                </div>
                            </div>
                        </div>
                    </div>
            </div>

            <div class="row py-1">
                <div v-if="!showNoitem" class="col-12 col-md-8 offset-md-2">
                    <item-menu v-for="data in filteredDataMenu" :key="data.id" :data="data"></item-menu>
                </div>
                <div v-else class="col-12 col-md-8 offset-md-2">
                    <p>
                        no item
                    </p>
                </div>
            </div>


        </div>

    </div>



</template>

<script>
import itemMenu from './itemMenu.vue'
export default {
    components:{
        itemMenu
    },
    data(){
        return{
            filters:{
                plus:true,
                person:true,
                branches:true
            },
            dataMenu:[
                {
                    id:0,
                    topic:'plus',
                    title:'bounding box',
                    icon:'far fa-calendar-plus',
                    number:30
                },
                {
                    id:1,
                    topic:'person',
                    title:'person box',
                    icon:'fas fa-universal-access',
                    number:60
                },
                {
                    id:2,
                    topic:'branches',
                    title:'box corners',
                    icon:"fas fa-code-branch",
                    number:24
                },
                {
                    id:3,
                    topic:'branches',
                    title:'box corners',
                    icon:"fas fa-code-branch",
                    number:14
                },
                {
                    id:4,
                    topic:'person',
                    title:'person box',
                    icon:'fas fa-universal-access',
                    number:40
                },
                {
                    id:5,
                    topic:'plus',
                    title:'bounding box',
                    icon:'far fa-calendar-plus',
                    number:30
                } 
            ]
        }
    },
    methods:{
        setFilter(event){
          const inputId = event.target.id;
          const isActive = event.target.checked;
          const updatedFilters = {
              ...this.filters,
              [inputId] : isActive
          };
          this.filters = updatedFilters;
          console.log('filters',this.filters);
        }
    },
    computed:{
        filteredDataMenu(){
        return this.dataMenu.filter(
            data => {
            if (this.filters.plus && data.topic.includes('plus')){
                return true;
            }
            if (this.filters.person && data.topic.includes('person')){
                return true;
            }
            if (this.filters.branches && data.topic.includes('branches')){
                return true;
            }
            return false;
            })
        },
        showNoitem(){
            return this.filteredDataMenu.length === 0 ;
        }
    }
}
</script>



<style scoped >
.main-menu{
    width: 60%;
    min-height: 100%;
}
#check-boxes{
    border-bottom: .15rem solid #EE6C4D;
}
.label-checkbox{
    font-size: 1.4rem;
    color:#E0FBFC;
}
.label-checkbox i{
    margin-right: .5rem;
}
p{
    color: #EE6C4D;
    text-align: center;
    font-size: 1.8rem;
    padding: 1rem 0;
}
</style>