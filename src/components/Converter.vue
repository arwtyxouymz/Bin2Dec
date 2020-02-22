<template>
  <div>
    <h1>Bin2Dec</h1>
    <p>Convert binary number to decimal</p>

    <div class="form-table">
      <div class="binary form-item">
        <div class="label"><label for="binary">Binary</label></div>
        <div class="form-content binary-content">
          <ul class="validation-errors">
            <li v-if="!valid" class="error-text">
              Input value must be composed of only 0 and 1
            </li>
          </ul>
          <input
            id="binary"
            type="text"
            placeholder="Input number with 0 or 1"
            v-model="binary"
            v-bind:class="{ 'has-error': !valid }"
            >
        </div>
      </div>
      <div class="decimal form-item">
        <div class="label"><label for="decimal">Decimal</label></div>
        <div class="form-content">
          <input
            id="decimal"
            type="text"
            placeholder="Output decimal"
            v-model.number="decimal"
            readonly=true
            >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const RegExp = /^[0-1]+$/

export default {
  data () {
    return {
      binary: '',
    }
  },
  computed: {
    valid () {
      return RegExp.test(this.binary)
    },

    decimal () {
      if (!this.valid) {
        return ''
      }

      return this.binary.split('')
        .map(Number)
        .reverse()
        .reduce((accumulator, currentValue, idx) => accumulator + currentValue * Math.pow(2, idx), 0)
    }
  },

  methods: {
  }
}
</script>

<style scoped>
*, *:before, *:after {
  box-sizing: border-box;
}

div {
  margin: 0 auto;
  text-align: center;
  width: 60%;
  height: 100%;
}

h1 {
  background: #a3c9f7;
  vertical-align: middle;
  margin-bottom: 0;
}

p {
  font-size: 1.2em;
}

.form-table {
  border-collapse: collapse;
  width: 100%;
  height: 100%;
}

div.form-item {
  display: flex;
  width: 100%;
}

.binary {
  height: 25%;
}

.decimal {
  height: 25%;
}

div.label {
  background: #ffecea;
  font-size: 1.5em;
  width: 30%;
  border-top: 1px solid #d7d7d7;
  border-bottom: 1px solid #d7d7d7;
  display: flex;
  justify-content: center;
  align-items: center;
}

div.form-content {
  border-top: 1px solid #d7d7d7;
  border-bottom: 1px solid #d7d7d7;
  width: 70%;
  display: flex;
  justify-content: center;
  align-items: center;
}

div.binary-content {
  flex-direction: column;
}

ul.validation-errors {
  list-style: none;
  padding: 0;
  margin: 0.25em 0;
}

ul li {
  font-size: 0.8em;
  color: red;
}

input {
  background: #F8F8F8;
  border-radius: 0;
  box-shadow: none;
  outline: none;
  border: none;
  width: 70%;
  height: 35%;
  font-size: 1.5em;
  text-align: center;
}

input:focus {
  background: #e9f5fb;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

input.has-error {
  border: 2px solid red;
}
</style>
