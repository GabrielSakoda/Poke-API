# 📦 Axios - Implementação no Projeto Poke-API

## O que é Axios?

Axios é uma biblioteca JavaScript baseada em Promises para fazer requisições HTTP. É uma alternativa mais poderosa ao `fetch` nativo.

## 🆚 Comparação: Fetch vs Axios

### **Com Fetch (Antes):**
```javascript
const listResponse = await fetch(`https://pokeapi.co/api/v2/pokemon?limit=350`);
const listData = await listResponse.json(); // Precisa converter manualmente

const batchPromises = batch.map(pokemon => 
  fetch(pokemon.url).then(response => response.json()) // Duas etapas
);
```

### **Com Axios (Agora):**
```javascript
const { data: listData } = await axios.get(`https://pokeapi.co/api/v2/pokemon?limit=350`, {
  timeout: 10000 // Timeout automático!
});

const batchPromises = batch.map(pokemon => 
  axios.get(pokemon.url, { timeout: 5000 })
    .then(response => response.data) // Já vem em JSON!
);
```

## ✨ Vantagens Implementadas

### 1. **Sintaxe Mais Limpa**
- ❌ Fetch: `fetch().then(res => res.json())`
- ✅ Axios: `axios.get()` → já retorna `response.data` em JSON

### 2. **Timeout Automático**
```javascript
axios.get(url, { timeout: 5000 }) // Cancela após 5 segundos
```
- Evita requisições infinitas
- Melhor controle de performance
- Detecção de erros: `error.code === 'ECONNABORTED'`

### 3. **Melhor Tratamento de Erros**
```javascript
catch (error) {
  if (error.code === 'ECONNABORTED') {
    console.error('Timeout: A requisição demorou muito');
  }
  if (error.response) {
    // Erro do servidor (4xx, 5xx)
    console.error('Status:', error.response.status);
  } else if (error.request) {
    // Requisição foi feita mas sem resposta
    console.error('Sem resposta do servidor');
  } else {
    // Erro na configuração
    console.error('Erro:', error.message);
  }
}
```

### 4. **Desestruturação Simplificada**
```javascript
const { data } = await axios.get(url); // Já extrai os dados
```

## 🚀 Recursos Avançados do Axios (Não Implementados Ainda)

### **Interceptors** - Modificar todas as requisições/respostas
```javascript
axios.interceptors.request.use(config => {
  console.log('Fazendo requisição para:', config.url);
  return config;
});
```

### **Cancelamento de Requisições**
```javascript
const source = axios.CancelToken.source();
axios.get(url, { cancelToken: source.token });
source.cancel('Operação cancelada pelo usuário');
```

### **Configuração Global**
```javascript
axios.defaults.baseURL = 'https://pokeapi.co/api/v2';
axios.defaults.timeout = 5000;
```

### **Transformação de Dados**
```javascript
axios.get(url, {
  transformResponse: [(data) => {
    // Modificar dados antes de retornar
    return JSON.parse(data).results;
  }]
});
```

## 📊 Performance

| Recurso | Fetch | Axios |
|---------|-------|-------|
| Conversão JSON | Manual (`.json()`) | Automático |
| Timeout | Precisa implementar | Nativo (`timeout`) |
| Cancelamento | AbortController | CancelToken |
| Interceptors | ❌ | ✅ |
| Tamanho | 0kb (nativo) | ~13kb |

## 🎯 Conclusão

Axios foi implementado no projeto oferecendo:
- ✅ Código mais limpo e legível
- ✅ Timeout automático (10s para lista, 5s por pokémon)
- ✅ Melhor tratamento de erros
- ✅ Mesma funcionalidade, código mais robusto

O projeto continua funcionando exatamente igual, mas agora com uma base mais sólida para futuras melhorias!
