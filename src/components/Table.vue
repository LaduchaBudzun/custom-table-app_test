<template>
  <div class="hello">


    
   <div>
     <button v-b-modal.modal-1  class="btn-settings">Настройка</button>

     <b-modal static ref="my-modal" id="modal-1" title="Настройка" ok-title="Сохранить" cancel-title="Отмена" cancel-variant="danger" @ok="handleOk" @cancel="handlerCancel" >
    <div class="D-n-D">

    <div class="selected">
      <h4>Выбранные</h4>
       <draggable :list="itemsPopup" group="todosapp" ghostClass="on-drag" animation="400">
          <div class="item" v-for="item in itemsPopup" :key="item.id" :item="item">
           <td >{{item.name}}</td>
        </div>
        </draggable>
    </div>

      
     <div class="available">
       <h4>Скрытые</h4>
        <draggable :list="hiddenItemsPopup" group="todosapp" ghostClass="on-drag" animation="400"> 
          <div class="item" v-for="hitem in hiddenItemsPopup" :key="hitem.id" :item="hitem">
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
    ],
    itemsPopup:[
        { name: 'Ivan', value: '12345', department: 'qwerty',id:1},
        { name: 'Sergei', value: '12345', department: 'qwerty',id:2},
        { name: 'Alex', value: '12345', department: 'qwerty',id:3}
    ],
    hiddenItemsPopup:[
      { name: 'Vlad', value: '20', department: 'Domus',id:4},
      { name: 'Stas', value: '20', department: 'Domus',id:5},
      { name: 'Genri', value: '1267', department: 'Ford',id:6},
    ],
    
    }
  },
  methods:{
    handleOk() {

        // // Prevent modal from closing
        // bvModalEvt.preventDefault()
        
        
        this.items = this.itemsPopup
        this.hiddenItems = this.hiddenItemsPopup
        // bvModalEvt - setTimeout(() => this.$bvModal.hide('modal-1'));
       
      },
      handlerCancel(){

      
      this.itemsPopup = this.items
      this.hiddenItemsPopup = this.hiddenItems
      
      
      
      
      // this.hiddenItems = this.hiddenItems.filter(item => this.items.includes(item));
      
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
.D-n-D h4{
  text-align: center;
}
.selected{
  width: 100%;
  height: 100%;
  border: 1px solid #777777;
  border-radius: 4px;
  padding: 10px;
  margin: 3px;
}
.available{
  width: 100%;
  height: 100%;
  border: 1px solid #777777;
  border-radius: 4px;
  padding: 10px;
  margin: 3px;
}
.item{
  cursor: move;
  padding: 15px 70px;
  border: 3px solid #5a567f;
  border-radius: 4px;
  background-color:#f3f2ff;
  margin: 2px;
   -webkit-touch-callout: none; /* iOS Safari */
  -webkit-user-select: none;   /* Chrome/Safari/Opera */
  -khtml-user-select: none;    /* Konqueror */
  -moz-user-select: none;      /* Firefox */
  -ms-user-select: none;       /* Internet Explorer/Edge */
  user-select: none;           /* Non-prefixed version, currently
                                  not supported by any browser */
}
.on-drag{
  color: #fff;
  background-color: rgb(103,174,255);
  z-index: 10;
  border: none;
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
