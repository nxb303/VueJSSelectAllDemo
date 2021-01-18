<template>
  <div>
    <ol>
      <li>
        <label for="selectAll">Select All</label>
        <input type="checkbox" id="selectAll" v-model="allSelected" :indeterminate.prop="selectAllIndeterminate">
      </li>
      <li>
        <label for="optionA">Option A</label>
        <input type="checkbox" id="optionA" v-model="options[0].selected">
      </li>
      <li>
        <label for="optionB">Option B</label>
        <input type="checkbox" id="optionB" v-model="options[1].selected">
      </li>
      <li>
        <label for="optionC">Option C</label>
        <input type="checkbox" id="optionC" v-model="options[2].selected">
      </li>
    </ol>

  </div>
</template>

<script>
export default {
  name: 'SelectAllDemo',
  props: {
    msg: String
  },
  data() {
    return {
      selectAll: false,
      options: [
        {selected: false},
        {selected: false},
        {selected: false}
      ]
    }
  },
  methods: {},

  computed: {
    selectAllIndeterminate: function () {
      return !((this.options.every(option => option.selected)) || (this.options.every(option => !option.selected)));
    },
    allSelected: {
      get: function () {
        if (this.options.every(option => option.selected)) {
          return true;
        } else {
          return false;
        }
      },
      set: function (value) {
        for (let option of this.options) {
          option.selected = value
        }
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

</style>
