# 💱 Conversor de Moedas

## 📖 Descrição

Um conversor de moedas feito em **Vue.js** (Composition API), usando cotações fixas de exemplo (Real, Dólar e Euro). O resultado é calculado automaticamente conforme o usuário digita, sem precisar de botão. Ótimo para praticar `computed`, `v-model` e manipulação de dados.

> ⚠️ As cotações são valores de exemplo e não representam o câmbio real.

## ✨ Funcionalidades

- Converter entre Real, Dólar e Euro
- Cálculo automático em tempo real
- Botão para inverter as moedas
- Resultado formatado por moeda

## 🛠️ Tecnologias utilizadas

- Vue.js 3 (Composition API)
- Vite
- JavaScript
- CSS puro

## ▶️ Como executar localmente

```bash
npm install
npm run dev
```

Depois abra o endereço mostrado no terminal (geralmente `http://localhost:5173`).

## 📁 Estrutura básica do projeto

```
vue-conversor-moedas/
├── index.html
├── package.json
├── vite.config.js
└── src/
    ├── App.vue
    ├── main.js
    ├── style.css
    └── components/
        └── ResultadoConversao.vue
```

## 🚀 Melhorias futuras

- Buscar cotações reais de uma API pública
- Adicionar mais moedas
- Guardar a última conversão no LocalStorage

## 👤 Autor

**Desenvolvido por KWDev**
