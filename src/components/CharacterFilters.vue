<template>
  <div>
    <input type="text" placeholder="Search by name" @input="$emit('filter', { name: $event.target.value })" />
    <select @change="$emit('filter', { species: $event.target.value })">
      <option value="">All Species</option>
      <option value="Human">Human</option>
      <option value="Alien">Alien</option>
    </select>
  </div>
</template>

