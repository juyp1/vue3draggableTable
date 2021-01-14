<template>

  <div>
    <a-row>
      <a-col :span="24">
        <div >

          <a-row  :span="24">
            <a-col :span="6" class="table-header"> 序号</a-col>
            <a-col :span="6" class="table-header">  消息</a-col>
            <a-col :span="6" class="table-header">创建时间</a-col>
            <a-col :span="6" class="table-header"> 次数</a-col>
          </a-row>

        </div>

      </a-col>

      <draggable  :list="tablelist" item-key="id" :move="checkMove" @start="dragging = true" @end="dragging = false">
        <template #item="{ element }" >
          <a-Row :span="24">
            <a-col :span="6" class="table-td-item"> {{element.id}}</a-col>
            <a-col :span="6" class="table-td-item">  {{element.name}}</a-col>
            <a-col :span="6" class="table-td-item">{{element.time}}</a-col>
            <a-col :span="6" class="table-td-item"> {{element.num}}</a-col>
          </a-Row>
        </template>
      </draggable>

    </a-row>
  </div>


</template>

<script>
import draggable from "vuedraggable";
let id = 1;
export default {
  name: "draggableTable.vue",

  components: {
    draggable
  },
  data() {
    return {
      enabled: true,
      tablelist: [
        { id: 1, name: "活动消息1", time: "2018-08-25 14：54", num: "1000" },
        { id: 2, name: "公司消息2", time: "2018-08-25 14：54", num: "200" },
        { id: 3, name: "个人消息3", time: "2018-08-25 14：54", num: "30000" },
        { id: 4, name: "客户消息4", time: "2018-08-25 14：54", num: "40" }
      ],
      dragging: false
    };
  },
  computed: {
    draggingInfo() {
      return this.dragging ? "under drag" : "";
    }
  },
  methods: {

    checkMove: function(e) {
      console.log(e.draggedContext)
      window.console.log("Future index: " + e.draggedContext.futureIndex);
    }
  }
};
</script>
<style scoped lang="scss">
.table-header{
  color: rgba(0, 0, 0, 0.85);
  font-weight: 500;
  background: #fafafa;
  border-bottom: 1px solid #f0f0f0;
  transition: background 0.3s ease;
  height: 55px;
  line-height: 55px;
  text-align: center;
}
.table-td-item{
  height: 55px;
  line-height: 55px;
  text-align: center;
  border-bottom: 1px solid #f0f0f0;
}
</style>
