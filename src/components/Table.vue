<template>
  <div class="hello">


    
   <div>
     <button v-b-modal.modal-1  class="btn-settings">Настройка</button>

     <b-modal id="modal-1" title="Настройка">
    <div class="D-n-D">

    <div class="selected">
       <draggable :list="items" group="todosapp">
          <div class="item" v-for="item in items" :key="item.id" :item="item">
           <td >{{item.name}}</td>
        </div>
        </draggable>
    </div>

      
     <div class="available">
        <draggable :list="hiddenItems" group="todosapp">
          <div class="item" v-for="hitem in hiddenItems" :key="hitem.id" :item="hitem">
           <td >{{hitem.name}}</td>
        </div>
        </draggable>
     </div>

    </div>
    </b-modal> 
   </div>

 <div>
    <table class="table_blur">
    <tr>
      <th v-for="column in columns" :key="column.id">{{column.title}}</th>
    </tr>

    <tr v-for="item in items" :key="item.id">
      <td>{{item.name}}</td>
      <td>{{item.value}}</td>
      <td>{{item.department}}</td>
      </tr>
    
  
  </table>

 </div>
   
    
  </div>
</template>

<script>
import draggable from 'vuedraggable'

export default {
  components:{
    draggable
  },
  name: 'Table',
  data(){
    return{
  columns : [
        { alias: 'name', title: 'Наименование' },
        { alias: 'value', title: '...'},
        { alias: 'department', title: 'Отдел'},
    ],
    items:[
        { name: 'Ivan', value: '12345', department: 'qwerty',id:1},
        { name: 'Sergei', value: '12345', department: 'qwerty',id:2},
        { name: 'Alex', value: '12345', department: 'qwerty',id:3}
    ],
    hiddenItems:[
      { name: 'Vlad', value: '20', department: 'Domus',id:4},
      { name: 'Stas', value: '20', department: 'Domus',id:5},
      { name: 'Genri', value: '1267', department: 'Ford',id:6},
    ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello{
  
}
.D-n-D{
  display: flex;
  justify-content: space-between;
}
.selected{
  
}
.available{

}
.item{
  padding: 10px 5px;
  border: 1px solid #5a567f;
  margin: 2px;
}
.btn-settings{
   border-top: 1px solid #777777;	
  border-bottom: 1px solid #777777; 
  box-shadow: inset 0 1px 0 #999999, inset 0 -1px 0 #999999;
  background: linear-gradient(#9595b6, #5a567f);
  color: white;
  margin-bottom: 10px;
}
/*table */
.table_blur {
  background: #f5ffff;
  border-collapse: collapse;
  text-align: left;
}
.table_blur th {
  border-top: 1px solid #777777;	
  border-bottom: 1px solid #777777; 
  box-shadow: inset 0 1px 0 #999999, inset 0 -1px 0 #999999;
  background: linear-gradient(#9595b6, #5a567f);
  color: white;
  padding: 10px 70px;
  position: relative;
}
.table_blur th:after {
  content: "";
  display: block;
  position: absolute;
  left: 0;
  top: 25%;
  height: 25%;
  width: 100%;
  background: linear-gradient(rgba(255, 255, 255, 0), rgba(255,255,255,.08));
}
.table_blur tr:nth-child(odd) {
  background: #ebf3f9;
}
.table_blur th:first-child {
  border-left: 1px solid #777777;	
  border-bottom:  1px solid #777777;
  box-shadow: inset 1px 1px 0 #999999, inset 0 -1px 0 #999999;
}
.table_blur th:last-child {
  border-right: 1px solid #777777;
  border-bottom:  1px solid #777777;
  box-shadow: inset -1px 1px 0 #999999, inset 0 -1px 0 #999999;
}
.table_blur td {
  border: 1px solid #e3eef7;
  padding: 10px 15px;
  position: relative;
  transition: all 0.5s ease;
  text-align: center;
}
.table_blur tbody:hover td {
  color: transparent;
  text-shadow: 0 0 3px #a09f9d;
}
.table_blur tbody:hover tr:hover td {
  color: #444444;
  text-shadow: none;
}
</style>
