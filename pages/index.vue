<template>
  <div>
    <div class="container-buttons">
      <vs-button
        class="active1"
        :class="{ active1: orders == true }"
        @click="(orders = true), (info = false)"
        >Orders</vs-button
      >
      <vs-button
        class="active2"
        :class="{ active2: info == true }"
        @click="(orders = false), (info = true)"
        >Info</vs-button
      >
    </div>
    <orders v-if="orders" />
    <info v-if="info" />
  </div>
</template>
<script>
import Orders from "../components/Orders.vue";
import Info from "../components/Info.vue";
export default {
  components: {
    Orders,
    Info,
  },
  data() {
    return {
      orders: true,
      info: false,
    };
  },
};
</script>
<style >
.active1 {
  border: 4px solid #fff;
  padding: 0 2rem;
  background: #195faa;
}
.active2 {
  border: 4px solid #fff;
  padding: 0 2rem;
  background: #195faa;
}
.container-buttons {
  display: flex;
  justify-content: flex-end;
  background: #195faa;
  margin-bottom: 1rem;
}
body {
  max-width: 34rem;
  margin: 0 auto;
}
.vs-select__input {
  border: 2px solid black;
  opacity: 0.7;
}
.vs-select__input1 {
  border: 2px solid red !important;
  opacity: 0.7;
}
.vs-table__th {
  background: #195faa !important;
}
.vs-table__tr:nth-child(odd) {
  background: #fff;
}
.vs-table__tr:nth-child(even) {
  background: #e4f2f7;
  opacity: 0.8;
}
.vs-table__footer {
  margin-top: 1rem;
}
.vs-table__footer {
  padding: 8px 10px !important;
  border-radius: 0px 0px 14px 14px ;
  background: rgba(244, 247, 248, 1);
  background: rgba(var(--vs-gray-2), 1);
  border: 0.5px solid #195faa ;
  background: transparent;
}

</style>