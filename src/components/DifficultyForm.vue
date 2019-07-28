<template>
  <div id="difficulty-form">
    <input type="text" v-model.number="rows" />
    x
    <input type="text" v-model.number="cols" />
    <br />
    <label for>#mines:</label>
    <input type="text" v-model.number="mines" />
    <br />
    <button @click="handleSubmit">New Game</button>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class DifficultyForm extends Vue {
  @Prop() public defaultRows!: number;
  @Prop() public defaultCols!: number;
  @Prop() public defaultMines!: number;

  public rows: number = this.defaultRows;
  public cols: number = this.defaultCols;
  public mines: number = this.defaultMines;

  public handleSubmit(e: any) {
    e.target.blur();
    this.$emit('handle-submitted', this.rows, this.cols, this.mines);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
#difficulty-form {
  margin-bottom: 15px;
}

input[type='text'] {
  width: 50px;
  text-align: center;
}

label {
  margin-right: 5px;
  font-size: 12px;
}
</style>
