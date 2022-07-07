<template>
<div> 
<table v-if="equipments.length > 0" class="table table-bordered table-sm">
<thead>
  <tr>
    <th scope="col">#</th>
    <th scope="col">Name</th>
    <th scope="col">Description</th>
  </tr>
</thead>
<tbody>
  <tr v-for="(object, index) in equipments" :key="index">
    <td>
      {{object.id}}
    </td>
    <td>
      {{object.name}}
    </td>
    <td>
      {{object.description}}
    </td>
  </tr>
</tbody>
</table>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      equipments: []
    };
  },
  async mounted() {
    const { data } = await (await fetch("/api/getAllEquipments")).json();
    console.log('data', data);
    this.equipments = data;
  }
};
</script>