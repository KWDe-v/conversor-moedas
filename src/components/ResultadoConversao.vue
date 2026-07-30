<script setup>
import { computed } from 'vue'

// Recebe o valor convertido e a moeda de destino.
const props = defineProps({
  valor: Number,
  moeda: String,
})

// Formata o valor de acordo com a moeda escolhida.
const valorFormatado = computed(() => {
  const localePorMoeda = {
    BRL: 'pt-BR',
    USD: 'en-US',
    EUR: 'de-DE',
  }
  return props.valor.toLocaleString(localePorMoeda[props.moeda], {
    style: 'currency',
    currency: props.moeda,
  })
})
</script>

<template>
  <div class="resultado">
    <span class="resultado__rotulo">Resultado</span>
    <strong class="resultado__valor">{{ valorFormatado }}</strong>
  </div>
</template>

<style scoped>
.resultado {
  margin-top: 1.5rem;
  background-color: #ecfdf5;
  border-radius: 10px;
  padding: 1.2rem;
  text-align: center;
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
}

.resultado__rotulo {
  font-size: 0.85rem;
  color: var(--cor-suave);
}

.resultado__valor {
  font-size: 2rem;
  color: var(--cor-primaria);
}
</style>
