 <template>
  <div class="center">
    <h1>Orders</h1>
    <div class="container_seller">
      <p>
        Total of Seller #1
        <span>$9999.99</span>
      </p>
      <p>
        Total of Seller #2
        <span>$9999.99</span>
      </p>
      <p>
        Total of Seller #3
        <span>$9999.99</span>
      </p>
    </div>
    <div class="container_select">
      <vs-select class="container_border" placeholder="Select" v-model="value1">
        <vs-option label="All sellers" value="All sellers"
          >All sellers</vs-option
        >
      </vs-select>
      <vs-select placeholder="Select" v-model="value2">
        <vs-option label="All countries" value="All countries"
          >All countries</vs-option
        >
      </vs-select>
    </div>

    <vs-table>
      <template #thead>
        <vs-tr>
          <vs-th sort @click="data = $vs.sortData($event, data, 'orderId')">
            Order ID
          </vs-th>
          <vs-th sort @click="data = $vs.sortData($event, data, 'product')">
            Product
          </vs-th>
          <vs-th sort @click="data = $vs.sortData($event, data, 'price')">
            Price
          </vs-th>
          <vs-th sort @click="data = $vs.sortData($event, data, 'seller')">
            Seller
          </vs-th>
          <vs-th sort @click="data = $vs.sortData($event, data, 'country')">
            Country
          </vs-th>
        </vs-tr>
      </template>
      <template #tbody>
        <vs-tr
          :key="i"
          v-for="(tr, i) in $vs.getPage($vs.getSearch(data, search), page, max)"
          :data="tr"
        >
          <vs-td
            edit
            @click="(edit = tr), (editProp = 'orderId'), (editActive = true)"
          >
            {{ tr.orderId }}
          </vs-td>
          <vs-td>
            {{ tr.product }}
          </vs-td>
          <vs-td>
            {{ tr.price }}
          </vs-td>
          <vs-td>
            {{ tr.seller }}
          </vs-td>
          <vs-td>
            {{ tr.country }}
          </vs-td>
        </vs-tr>
      </template>
      <template #footer>
        <vs-pagination
          v-model="page"
          :length="$vs.getLength($vs.getSearch(data, search), max)"
        />
      </template>
    </vs-table>
    <div class="container_button">
      <button class="button1"><span class="container_span">Older</span></button>
      <button class="button2" role="button">
        <span class="container_span">Newer</span>
      </button>
    </div>

    <vs-dialog>
      <template #header> Change Prop {{ editProp }} </template>
      <vs-input
        @keypress.enter="editActive = false"
        v-if="editProp == 'email'"
        v-model="edit[editProp]"
      />
      <vs-select
        @change="editActive = false"
        block
        v-if="editProp == 'name'"
        placeholder="Select"
        v-model="edit[editProp]"
      >
        <vs-option label="Vuesax" value="Vuesax"> Vuesax </vs-option>
        <vs-option label="Vue" value="Vuejs"> Vue </vs-option>
        <vs-option label="Javascript" value="Javascript">
          Javascript
        </vs-option>
        <vs-option disabled label="Sass" value="Sass"> Sass </vs-option>
        <vs-option label="Typescript" value="Typescript">
          Typescript
        </vs-option>
        <vs-option label="Webpack" value="Webpack"> Webpack </vs-option>
        <vs-option label="Nodejs" value="Nodejs"> Nodejs </vs-option>
      </vs-select>
    </vs-dialog>
  </div>
</template>

  <script>
import data from "../components/data/data.js";
export default {
  data: () => ({
    editActive: false,
    edit: null,
    editProp: {},
    search: "",
    allCheck: false,
    page: 1,
    max: 6,
    active: 0,
    data: data,
    value1: "All sellers",
    value2: "All countries",
    value3: "Older",
    value4: "Newer",
  }),
};
</script>

<style lang="scss" scoped>
.container_select {
  display: flex;
  justify-content: flex-end;
  margin-bottom: 1rem;
  gap: 1rem;
}
.container_button {
  display: flex;
  justify-content: space-around;
  margin-bottom: 1rem;
  margin-top: 1rem;
}

.container_seller {
  display: flex;
  justify-content: space-between;
  color: #195faa;
  p {
    padding: 1rem;
    border: #195faa solid 1px;
    margin-right: 1rem;
    margin-top: 0;
    span {
      display: block;
      text-align: right;
      font-weight: 600;
    }
  }
}
h1 {
  margin-bottom: 1rem;
}
#seta {
  position: absolute;
  box-shadow: 2px -2px 0 1px #000 inset;
  border: solid transparent;
  border-width: 0 0 2px 2px;
}
button {
  background-color: transparent;
  border: 0.1em solid #195faa;
  outline: none;
  padding: 0.75em 3em;
  border-radius: 2rem;
  opacity: 0.5;
  .container_span {
    color: #195faa;
  }
}
button:hover {
  cursor: pointer;
}
.button2:after {
  border-right: 0.1em solid #195faa;
  border-bottom: 0.1em solid #195faa;
  content: "";
  display: inline-block;
  height: 1em;
  vertical-align: bottom;
  width: 1em;

  -webkit-transform: rotate(-45deg);
  -ms-transform: rotate(-45deg);
  transform: rotate(-45deg);
}
.button1:before {
   border-right: 0.1em solid #195faa;
  border-bottom: 0.1em solid #195faa;
  content: "";
  transform: rotate(135deg);
  display: inline-block;
  height: 1em;
  vertical-align: bottom;
  width: 1em;
}
</style>

