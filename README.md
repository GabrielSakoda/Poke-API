# Poke-API - Migração para Vue.js e Bootstrap

## 📋 Descrição
Este projeto foi migrado de JavaScript vanilla + CSS customizado para **Vue.js 2 + Bootstrap 5**, mantendo todas as funcionalidades originais.

## 🔄 Mudanças Realizadas

### Stack Anterior:
- HTML puro
- CSS customizado (estilos.css e reset.css)
- JavaScript vanilla (index.js)

### Stack Atual:
- **Vue.js 2.7.14** - Framework reativo
- **Bootstrap 5.3.3** - Framework CSS responsivo
- Google Fonts (Poppins)

## ✨ Funcionalidades Mantidas

1. **Exibição de 350 Pokémons** da PokeAPI
2. **Tema claro/escuro** com alternância
3. **Cards responsivos** com informações do Pokémon:
   - Nome
   - ID
   - Imagem animada (GIF)
   - Tipos (com cores específicas)
4. **Efeitos hover** nos cards
5. **Layout responsivo** com grid do Bootstrap

## 🎨 Melhorias com Bootstrap

- Sistema de grid responsivo (col-12, col-sm-6, col-md-4, col-lg-3)
- Classes utilitárias do Bootstrap
- Spinner de carregamento
- Layout mais adaptável a diferentes tamanhos de tela

## 🚀 Como Usar

Simplesmente abra o arquivo `index.html` em um navegador moderno. O projeto:
- Carrega automaticamente os 350 primeiros Pokémons
- Exibe um spinner durante o carregamento
- Permite alternar entre tema claro e escuro

## 📁 Estrutura de Arquivos

```
Poke-API/
├── index.html                    # Arquivo principal (agora com Vue.js)
├── index.js                      # Arquivo mantido para referência
├── index-vanilla.js.backup       # Backup do código JavaScript original
└── src/
    ├── css/
    │   ├── estilos.css          # CSS original (não mais usado)
    │   └── reset.css            # Reset CSS original (não mais usado)
    └── IMGS/
        ├── pokeball.png
        ├── pokemon-logo.png
        ├── sun.png
        └── moon.png
```

## 💡 Notas Técnicas

### Vue.js
- Usa Vue 2 para compatibilidade
- Reatividade automática
- Métodos: `fetchPokemons()`, `toggleTheme()`, `capitalize()`
- Lifecycle hook: `mounted()` para carregar dados

### CSS Integrado
Os estilos foram integrados diretamente no HTML para simplificar a estrutura, mantendo:
- Cores originais dos tipos de Pokémon
- Backgrounds temáticos (claro/escuro)
- Transições e efeitos hover
- Tipografia Poppins

### Bootstrap
- Grid system para responsividade
- Spacing utilities (g-4, mt-3, etc.)
- Componente Spinner para loading

## 🔗 APIs Utilizadas
- **PokeAPI**: https://pokeapi.co/api/v2/pokemon/
- **Sprites**: GitHub PokeAPI (versão animada Black/White)

## 🎯 Compatibilidade
- Navegadores modernos (Chrome, Firefox, Safari, Edge)
- Design responsivo para mobile, tablet e desktop

---

**Desenvolvido com Vue.js e Bootstrap** ❤️
