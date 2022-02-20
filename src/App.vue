<template>
    <div class="container">
      <add-section/>
      <list-item/>
    </div>
</template>

<script>
import axios from 'axios'
import AddSection from './components/AddSection.vue'
import ListItem from './components/ListItem.vue'
export default {
  components: { AddSection, ListItem },
  provide(){
    return{
      onSave : this.onSave,
      listObject : this.listObject,
      onDelete : this.onDelete,
    }
  },
    data(){
        return{
            listObject:{itemList : []},
        }
    },
    mounted(){
            axios.get("http://localhost:3000/items").then(items_response => {
                this.listObject.itemList = items_response.data;   
            });
        },
    methods: {
        
        onSave(event){
            let saveObject = {
                title : event.target.value,
                createdAt : new Date(),
                completed : false,
            }
            axios.post("http://localhost:3000/items",saveObject).then(save_response => {
                console.log(save_response);
                this.listObject.itemList.push(save_response.data);
                event.target.value = "";
                event.target.focus();
            })
        },
        onDelete(item){
          axios.delete(`http://localhost:3000/items/${item.id}`).then(delete_response =>{
            console.log(delete_response);
            this.listObject.itemList = this.listObject.itemList.filter(i => i.id !== item.id);
          })
        }
    }
}
</script>