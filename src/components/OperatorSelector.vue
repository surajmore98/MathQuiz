<template>
    <div>
      <button @click="$emit('select-operator', '+')">Addition (+)</button>
      <button @click="$emit('select-operator', '-')">Substraction (-)</button>
      <button @click="$emit('select-operator', '*')">Multiplication (*)</button>
      <button @click="$emit('select-operator', '/')">Division (/)</button>
    </div>  
</template>