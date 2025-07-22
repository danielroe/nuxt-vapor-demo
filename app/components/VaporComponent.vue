<script setup vapor lang="ts">
import type { ShallowRef } from 'vue'
import { buildData } from '../data/shared'

const selected = ref();
const rows = shallowRef<Array<{ id: number; label: ShallowRef<string, string>; }>>([])

const timeElapsed = ref(0)

function add() {
  const start = performance.now();
  rows.value.push(...buildData(1000));
  triggerRef(rows);
  nextTick(() => {
    timeElapsed.value = performance.now() - start;
  });
}

function remove(id: number) {
  const start = performance.now();
  rows.value.splice(
    rows.value.findIndex((d) => d.id === id),
    1
  );
  triggerRef(rows);
  nextTick(() => {
    timeElapsed.value = performance.now() - start;
  });
}

function select(id: number) {
  const start = performance.now();
  selected.value = id;
  
  nextTick(() => {
    timeElapsed.value = performance.now() - start;
  });
}

function run() {
  const start = performance.now();
  rows.value = buildData();
  selected.value = undefined;
  
  nextTick(() => {
    timeElapsed.value = performance.now() - start;
  });
}

function update() {
  const start = performance.now();
  const _rows = rows.value;
  for (let i = 0, len = _rows.length; i < len; i += 10) {
    _rows[i]!.label.value += " !!!";
  }
  
  nextTick(() => {
    timeElapsed.value = performance.now() - start;
  });
}

function runLots() {
  const start = performance.now();
  rows.value = buildData(10000);
  selected.value = undefined;
  
  nextTick(() => {
    timeElapsed.value = performance.now() - start;
  });
}

function clear() {
  const start = performance.now();
  rows.value = [];
  selected.value = undefined;
  
  nextTick(() => {
    timeElapsed.value = performance.now() - start;
  });
}

function swapRows() {
  const start = performance.now();
  const _rows = rows.value;
  if (_rows.length > 998) {
    const d1 = _rows[1];
    const d998 = _rows[998];
    _rows[1] = d998!;
    _rows[998] = d1!;
    triggerRef(rows);
  }

  nextTick(() => {
    timeElapsed.value = performance.now() - start;
  });
}
</script>

<template>
  <div class="jumbotron">
    <div class="row">
      <div class="col-md-6">
        <h1>Vue Vapor component</h1>
      </div>
      <div>
        {{ timeElapsed }}ms
      </div>
      <div class="col-md-6">
        <div class="row">
          <div class="col-sm-6 smallpad">
            <button type="button" class="btn btn-primary btn-block" id="run" @click="run">Create 1,000 rows</button>
          </div>
          <div class="col-sm-6 smallpad">
            <button type="button" class="btn btn-primary btn-block" id="runlots" @click="runLots">
              Create 10,000 rows
            </button>
          </div>
          <div class="col-sm-6 smallpad">
            <button type="button" class="btn btn-primary btn-block" id="add" @click="add">Append 1,000 rows</button>
          </div>
          <div class="col-sm-6 smallpad">
            <button type="button" class="btn btn-primary btn-block" id="update" @click="update">
              Update every 10th row
            </button>
          </div>
          <div class="col-sm-6 smallpad">
            <button type="button" class="btn btn-primary btn-block" id="clear" @click="clear">Clear</button>
          </div>
          <div class="col-sm-6 smallpad">
            <button type="button" class="btn btn-primary btn-block" id="swaprows" @click="swapRows">Swap Rows</button>
          </div>
        </div>
      </div>
    </div>
  </div>
  <table class="table table-hover table-striped test-data">
    <tbody>
      <tr
        v-for="row of rows"
        :key="row.id"
        :class="{ danger: row.id === selected }"
        :data-label="row.label.value"
      >
        <td class="col-md-1">{{ row.id }}</td>
        <td class="col-md-4">
          <a @click="select(row.id)">{{ row.label.value }}</a>
        </td>
        <td class="col-md-1">
          <a @click="remove(row.id)">
            <span class="glyphicon glyphicon-remove" aria-hidden="true"></span>
          </a>
        </td>
        <td class="col-md-6"></td>
      </tr>
    </tbody>
  </table>
  <span class="preloadicon glyphicon glyphicon-remove" aria-hidden="true"></span>
</template>
