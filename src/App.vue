<script setup>
import { ref, computed } from 'vue'
import ResultadoConversao from './components/ResultadoConversao.vue'

// Cotações fixas em relação ao Real (valores de exemplo, não em tempo real).
const cotacoes = {
  USD: 5.4,
  EUR: 5.9,
  BRL: 1,
}

const valor = ref(100)
const de = ref('BRL')
const para = ref('USD')

// Converte primeiro para Real, depois para a moeda de destino.
const resultado = computed(() => {
  const valorNumero = Number(valor.value) || 0
  const emReais = valorNumero * cotacoes[de.value]
  const convertido = emReais / cotacoes[para.value]
  return convertido
})

function inverter() {
  const temp = de.value
  de.value = para.value
  para.value = temp
}
</script>

<template>
  <main class="painel">
    <h1 class="painel__titulo">💱 Conversor de Moedas</h1>

    <label class="painel__campo">
      Valor
      <input type="number" v-model="valor" min="0" />
    </label>

    <div class="painel__moedas">
      <label>
        De
        <select v-model="de">
          <option value="BRL">Real (BRL)</option>
          <option value="USD">Dólar (USD)</option>
          <option value="EUR">Euro (EUR)</option>
        </select>
      </label>

      <button class="painel__inverter" @click="inverter" title="Inverter">⇄</button>

      <label>
        Para
        <select v-model="para">
          <option value="BRL">Real (BRL)</option>
          <option value="USD">Dólar (USD)</option>
          <option value="EUR">Euro (EUR)</option>
        </select>
      </label>
    </div>

    <ResultadoConversao :valor="resultado" :moeda="para" />

    <p class="painel__aviso">*Cotações de exemplo, não são valores reais.</p>
  </main>
</template>

<style scoped>
.painel {
  background-color: var(--cor-card);
  padding: 2rem;
  border-radius: 16px;
  width: 100%;
  max-width: 400px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
}

.painel__titulo {
  text-align: center;
  font-size: 1.5rem;
  margin-bottom: 1.5rem;
}

.painel__campo {
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--cor-suave);
  margin-bottom: 1rem;
}

.painel__campo input {
  padding: 0.7rem;
  border: 2px solid var(--cor-borda);
  border-radius: 8px;
  font-size: 1.1rem;
  outline: none;
}

.painel__moedas {
  display: flex;
  align-items: flex-end;
  gap: 0.5rem;
}

.painel__moedas label {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--cor-suave);
}

.painel__moedas select {
  padding: 0.7rem;
  border: 2px solid var(--cor-borda);
  border-radius: 8px;
  font-size: 0.95rem;
  outline: none;
  cursor: pointer;
}

.painel__inverter {
  background-color: var(--cor-primaria);
  color: #fff;
  border: none;
  border-radius: 8px;
  width: 42px;
  height: 42px;
  font-size: 1.1rem;
  cursor: pointer;
  flex-shrink: 0;
}

.painel__aviso {
  margin-top: 1rem;
  font-size: 0.75rem;
  color: var(--cor-suave);
  text-align: center;
}
</style>
