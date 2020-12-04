<template>
  <div class="container">
    <div class="table-wrapper">
      <div class="table">
        <div class="thead">
          <div class="tr">
            <div class="title td">title</div>
            <div
              class="td"
              v-for="colTitle in colTitles"
              :key="colTitle.id"
            >{{colTitle}}</div>
          </div>
        </div>
        <div class="tbody">
          <div
            class="tr"
            v-for="item in list"
            :key="item.id"
          >
            <div
              class="td"
              v-for="col in item.cols"
              :key="col.id"
            >{{col}}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FixedLeftTopTable',
  data () {
    return {
      list: [],
      colTitles: []
    }
  },
  mounted () {
    const list = []
    const colTitles = []
    for (let i = 1, ii = 20; i <= ii; i++) {
      colTitles.push(`col-${i}`)
      const obj = {
        title: `title-${i}`
      }
      const cols = []
      for (let j = 1, jj = 20; j <= jj; j++) {
        cols.push(`col-${i}-${j}`)
      }
      obj.cols = cols
      list.push(obj)
    }
    this.list = list
    this.colTitles = colTitles
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.container {
  width: 100vw;
  height: 100vh;
  // width: 200px;
  // height: 300px;
  // margin: 50px;
}
.table-wrapper {
  // width: 100vw;
  height: 100%;
  overflow: scroll;
  .table {
    table-layout: fixed;
    display: table;
    width: 100%;
    .thead {
      display: table-header-group;
      .tr {
        .td {
          position: sticky;
          left: 0;
          top: 0;
          &:first-child {
            z-index: 2;
          }
        }
      }
    }
    .tbody {
      display: table-row-group;
      .tr {
        .td:first-child {
          position: sticky;
          left: 0;
          top: 0;
        }
      }
    }
    .tr {
      display: table-row;
      .td {
        display: table-cell;
        width: 100px;
        height: 50px;
        vertical-align: middle;
        background-color: #fff;
        z-index: 1;
      }
    }
  }
}
</style>
