<template lang="html">
  <div class="todo">
    <div class="filter">
      <select>
        <option value="all">all</option>
        <option value="all">active</option>
        <option value="all">completed</option>
      </select>
    </div>
    <div class="spacer" />
    <table class="todo-list">
      <tr>
        <td>
          Do the dishes
        </td>
        <td>
          <button>toggle</button>
        </td>
        <td>
          <button>delete</button>
        </td>
      </tr>
      <tr>
        <td>
          Take out trash
        </td>
        <td>
          <button>toggle</button>
        </td>
        <td>
          <button>delete</button>
        </td>
      </tr>
      <tr>
        <td class="completed">
          Finish doing laundry
        </td>
        <td>
          <button>toggle</button>
        </td>
        <td>
          <button>delete</button>
        </td>
      </tr>
    </table>
    <div class="spacer" />
    <div class="new-todo-form">
      <input type="text" value="" />
      <div class="spacer" />
      <button>add</button>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="css" scoped>
* {
  font-size: 16px;
  outline: none;
}
.spacer {
  display: inline-block;
  width: 10px;
  height: 10px;
}
.completed {
  text-decoration: line-through;
}
</style>
