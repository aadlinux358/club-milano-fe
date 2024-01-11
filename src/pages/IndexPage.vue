<template>
  <q-page class="column items-center"
          padding>
    <q-table title="Guest List"
             flat
             style="height: 450px"
             :rows="guests"
             :columns="columns"
             row-key="name"
             class="q-my-md my-sticky-header-table">
      <template v-slot:top>
        <div class="col-4 q-table__title text-yellow-14">Guest List</div>
      </template>
      <template v-slot:header="props">
        <q-tr :props="props">
          <q-th v-for="col in props.cols"
                :key="col.name"
                :props="props"
                class="text-yellow-14">
            {{ col.label }}
          </q-th>
        </q-tr>
      </template>
      <template v-slot:body="props">
        <q-tr :props="props">
          <q-td key="full_name"
                :props="props">
            {{ props.row.full_name }}
          </q-td>
          <q-td key="payment"
                :props="props">
            <q-icon :class="{
              'text-green-14': props.row.payment === 'paid',
              'text-red-14': props.row.payment === 'unpaid'
            }
              "
                    :name="props.row.payment === 'paid' ? 'done' : 'close'" />
          </q-td>
          <q-td key="phone_number"
                :props="props">
            {{ props.row.phone_number }}
          </q-td>
        </q-tr>
      </template>
    </q-table>
  </q-page>
</template>

<script setup lang="ts">
import {ref} from 'vue';
const columns = [
  {
    name: 'full_name',
    required: true,
    label: 'Full Name',
    align: 'left',
    field: row => row.full_name,
    sortable: true
  },
  // {name: 'last_name', align: 'left', label: 'Last Name', field: row => row.last_name, sortable: true},
  {name: 'payment', align: 'center', label: 'Payment', field: row => row.payment, sortable: true},
  {
    name: 'phone_number',
    required: true,
    label: 'Phone Number',
    align: 'left',
    field: row => row.phone_number,
    sortable: true
  },
]
const guests = ref([
  {
    id: 1,
    phone_number: '+3133829384',
    full_name: "Isaias Afewerki",
    payment: "paid"
  },
  {
    id: 2,
    phone_number: '+3133829384',
    full_name: "Bil Clinton",
    payment: "paid"
  },
  {
    id: 3,
    phone_number: '+3133829384',
    full_name: "Abi Ahmed",
    payment: "unpaid"
  },
  {
    id: 4,
    phone_number: '+3133829384',
    full_name: "Vladmir Putin",
    payment: "paid"
  },
  {
    id: 5,
    phone_number: '+3133829384',
    full_name: "Mengstu Hailemaryam",
    payment: "unpaid"
  },
  {
    id: 6,
    phone_number: '+3133829384',
    full_name: "Awet Idris",
    payment: "paid"
  },
])
</script>
<style lang="sass">
.my-sticky-header-table
  /* height or max-height is important */
  height: 310px

  .q-table__top,
  .q-table__bottom,
  thead tr:first-child th
    /* bg color is important for th; just specify one */
    background-color: $dark

  thead tr th
    position: sticky
    z-index: 1
  thead tr:first-child th
    top: 0

  /* this is when the loading indicator appears */
  &.q-table--loading thead tr:last-child th
    /* height of all previous header rows */
    top: 48px

  /* prevent scrolling behind sticky top row on focus */
  tbody
    /* height of all previous header rows */
    scroll-margin-top: 48px
</style>
