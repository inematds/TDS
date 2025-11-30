# TDS - Guia de Referência de Estilos e Layout

> **Transformação Digital e Social**
> Sistema de Design para Curso de Vendas, Redes Sociais e Negócios

**Versão:** 1.0 | **Data:** 2025-11-30 | **Autor:** TDS Team

---

## Índice Rápido

- [Visão Geral](#visão-geral)
- [Dark Mode](#dark-mode)
- [Identidade Visual](#identidade-visual)
- [Sistema de Cores por Trilha](#sistema-de-cores-por-trilha)
- [Tipografia](#tipografia)
- [Espaçamento e Grid](#espaçamento-e-grid)
- [Componentes](#componentes)
- [Animações](#animações)
- [Responsividade](#responsividade)
- [Código de Exemplo](#código-de-exemplo)

---

## Visão Geral

### Sobre o Projeto

**TDS** é um curso de **Transformação Digital** com 3 trilhas especializadas:
- **Vendas** - Estratégias e técnicas de venda digital
- **Redes Sociais** - Marketing e engajamento em plataformas sociais
- **Negócios** - Modelos de negócio, automação e escalabilidade

### Princípios de Design

1. **Clareza** - Interface limpa e fácil de navegar
2. **Identidade por Trilha** - Cada trilha tem sua cor distintiva
3. **Acessibilidade** - WCAG 2.1 AA compliant
4. **Performance** - Animações suaves
5. **Mobile-First** - Design responsivo

### Stack Tecnológico

```
Framework CSS:  Tailwind CSS 3.x (CDN)
JavaScript:     Vanilla JS
Fontes:         Google Fonts - Inter
Build:          HTML puro (sem build process)
Dark Mode:      Tailwind class-based (localStorage + system preference)
Deploy:         GitHub Pages
```

---

## Dark Mode

### Configuração

O projeto usa dark mode baseado em classes do Tailwind CSS:

```javascript
// Tailwind Config
tailwind.config = {
  darkMode: 'class',
  // ... rest of config
}
```

### Implementação

**Classes Dark em Todos os Componentes:**
- `dark:bg-neutral-900` - Background escuro principal
- `dark:bg-neutral-800` - Cards e containers
- `dark:bg-neutral-700` - Elementos interativos
- `dark:text-neutral-100` - Texto principal
- `dark:text-neutral-300` - Texto secundário
- `dark:border-neutral-700` - Bordas

**Botão Toggle:**
```html
<button id="theme-toggle" class="p-2 rounded-lg bg-neutral-100 dark:bg-neutral-700 hover:bg-neutral-200 dark:hover:bg-neutral-600">
  <svg id="theme-toggle-dark-icon" class="hidden w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
    <path d="M17.293 13.293A8 8 0 016.707 2.707a8.001 8.001 0 1010.586 10.586z"></path>
  </svg>
  <svg id="theme-toggle-light-icon" class="hidden w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
    <path d="M10 2a1 1 0 011 1v1a1 1 0 11-2 0V3a1 1 0 011-1zm4 8a4 4 0 11-8 0 4 4 0 018 0zm-.464 4.95l.707.707a1 1 0 001.414-1.414l-.707-.707a1 1 0 00-1.414 1.414zm2.12-10.607a1 1 0 010 1.414l-.706.707a1 1 0 11-1.414-1.414l.707-.707a1 1 0 011.414 0zM17 11a1 1 0 100-2h-1a1 1 0 100 2h1zm-7 4a1 1 0 011 1v1a1 1 0 11-2 0v-1a1 1 0 011-1zM5.05 6.464A1 1 0 106.465 5.05l-.708-.707a1 1 0 00-1.414 1.414l.707.707zm1.414 8.486l-.707.707a1 1 0 01-1.414-1.414l.707-.707a1 1 0 011.414 1.414zM4 11a1 1 0 100-2H3a1 1 0 000 2h1z" fill-rule="evenodd" clip-rule="evenodd"></path>
  </svg>
</button>
```

**JavaScript para Toggle:**
```javascript
const themeToggleBtn = document.getElementById('theme-toggle');
const themeToggleDarkIcon = document.getElementById('theme-toggle-dark-icon');
const themeToggleLightIcon = document.getElementById('theme-toggle-light-icon');

// Check for saved theme or system preference
if (localStorage.getItem('color-theme') === 'dark' ||
    (!('color-theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
  document.documentElement.classList.add('dark');
  themeToggleLightIcon.classList.remove('hidden');
} else {
  themeToggleDarkIcon.classList.remove('hidden');
}

themeToggleBtn.addEventListener('click', function() {
  themeToggleDarkIcon.classList.toggle('hidden');
  themeToggleLightIcon.classList.toggle('hidden');

  if (document.documentElement.classList.contains('dark')) {
    document.documentElement.classList.remove('dark');
    localStorage.setItem('color-theme', 'light');
  } else {
    document.documentElement.classList.add('dark');
    localStorage.setItem('color-theme', 'dark');
  }
});
```

### Paleta Dark Mode

```css
/* Light Mode */
--bg-primary:      #F5F5F5   /* neutral-100 */
--bg-card:         #FFFFFF   /* white */
--bg-interactive:  #F5F5F5   /* neutral-100 */
--text-primary:    #171717   /* neutral-900 */
--text-secondary:  #737373   /* neutral-500 */

/* Dark Mode */
--bg-primary:      #171717   /* neutral-900 */
--bg-card:         #262626   /* neutral-800 */
--bg-interactive:  #404040   /* neutral-700 */
--text-primary:    #FAFAFA   /* neutral-50 */
--text-secondary:  #D4D4D4   /* neutral-300 */
```

---

## Identidade Visual

### Logo e Marca

```
Nome:     TDS
Fonte:    Inter Bold (700)
Cor:      Gradiente (Emerald → Blue → Purple)
Tagline:  "Transformação Digital e Social"
```

### Personalidade

- **Tom**: Profissional, educacional, inspirador
- **Estilo**: Moderno, minimalista, energético
- **Emoção**: Confiança, crescimento, transformação

---

## Sistema de Cores por Trilha

### Cores Principais (CRÍTICO)

```css
/* 3 Trilhas de Aprendizado */
💰 Trilha Vendas:        #10B981  /* Verde Emerald 500 */
📱 Trilha Redes Sociais: #3B82F6  /* Azul Blue 500 */
🏢 Trilha Negócios:      #A855F7  /* Roxo Purple 500 */
```

### Paleta Completa por Trilha

#### Trilha Vendas (Emerald)
```css
--vendas-50:      #ECFDF5;  /* Backgrounds */
--vendas-100:     #D1FAE5;  /* Cards */
--vendas-200:     #A7F3D0;  /* Bordas leves */
--vendas-400:     #34D399;  /* Hover */
--vendas-500:     #10B981;  /* Principal */
--vendas-600:     #059669;  /* Botões hover */
--vendas-700:     #047857;  /* Texto escuro */
--vendas-900:     #064E3B;  /* Dark mode texto */
```

#### Trilha Redes Sociais (Blue)
```css
--social-50:      #EFF6FF;  /* Backgrounds */
--social-100:     #DBEAFE;  /* Cards */
--social-200:     #BFDBFE;  /* Bordas leves */
--social-400:     #60A5FA;  /* Hover */
--social-500:     #3B82F6;  /* Principal */
--social-600:     #2563EB;  /* Botões hover */
--social-700:     #1D4ED8;  /* Texto escuro */
--social-900:     #1E3A8A;  /* Dark mode texto */
```

#### Trilha Negócios (Purple)
```css
--negocios-50:    #FAF5FF;  /* Backgrounds */
--negocios-100:   #F3E8FF;  /* Cards */
--negocios-200:   #E9D5FF;  /* Bordas leves */
--negocios-400:   #C084FC;  /* Hover */
--negocios-500:   #A855F7;  /* Principal */
--negocios-600:   #9333EA;  /* Botões hover */
--negocios-700:   #7E22CE;  /* Texto escuro */
--negocios-900:   #581C87;  /* Dark mode texto */
```

### Gradientes

```css
/* Hero Section - Principal */
background: linear-gradient(to bottom right, #10B981, #3B82F6, #A855F7);
/* Emerald → Blue → Purple */

/* Hero Trilha Vendas */
background: linear-gradient(to bottom right, #10B981, #059669);
/* Emerald 500 → Emerald 600 */

/* Hero Trilha Redes Sociais */
background: linear-gradient(to bottom right, #3B82F6, #2563EB);
/* Blue 500 → Blue 600 */

/* Hero Trilha Negócios */
background: linear-gradient(to bottom right, #A855F7, #9333EA);
/* Purple 500 → Purple 600 */

/* Cards de Trilha */
.vendas-card {
  background: linear-gradient(to bottom right, #ECFDF5, #FFFFFF);
  /* from-emerald-50 to-white */
}

.social-card {
  background: linear-gradient(to bottom right, #EFF6FF, #FFFFFF);
  /* from-blue-50 to-white */
}

.negocios-card {
  background: linear-gradient(to bottom right, #FAF5FF, #FFFFFF);
  /* from-purple-50 to-white */
}
```

### Uso por Contexto

| Elemento | Vendas | Redes Sociais | Negócios |
|----------|--------|---------------|----------|
| **Badge** | `bg-emerald-500` | `bg-blue-500` | `bg-purple-500` |
| **Borda** | `border-emerald-200` | `border-blue-200` | `border-purple-200` |
| **Hover** | `border-emerald-400` | `border-blue-400` | `border-purple-400` |
| **Botão** | `bg-emerald-500` | `bg-blue-500` | `bg-purple-500` |
| **Texto Destaque** | `text-emerald-600` | `text-blue-600` | `text-purple-600` |
| **Check** | `text-emerald-500` | `text-blue-500` | `text-purple-500` |

---

## Tipografia

### Família de Fontes

```html
<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
```

```css
body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```

### Hierarquia Tipográfica

#### Desktop
```css
H1 (Hero):      4rem (64px) | font-weight: 700
H2 (Section):   2.5rem (40px) | font-weight: 700
H3 (Card):      1.875rem (30px) | font-weight: 700
H4 (Subtitle):  1.5rem (24px) | font-weight: 600
Body Large:     1.25rem (20px) | font-weight: 400
Body:           1rem (16px) | font-weight: 400
Small:          0.875rem (14px) | font-weight: 400
```

#### Mobile (< 640px)
```css
H1:  2rem (32px)
H2:  1.75rem (28px)
H3:  1.5rem (24px)
```

### Classes Tailwind

```html
<!-- Hero Title -->
<h1 class="text-4xl sm:text-6xl font-bold">Título</h1>

<!-- Section Title -->
<h2 class="text-3xl sm:text-4xl font-bold">Seção</h2>

<!-- Card Title -->
<h3 class="text-2xl font-bold">Card</h3>

<!-- Body Text -->
<p class="text-base text-neutral-700 dark:text-neutral-300">Texto</p>

<!-- Secondary Text -->
<p class="text-sm text-neutral-500 dark:text-neutral-400">Secundário</p>
```

---

## Espaçamento e Grid

### Sistema de Espaçamento (Base: 1rem = 16px)

```
xs:   0.25rem   (4px)   - Espaços mínimos
sm:   0.5rem    (8px)   - Gaps pequenos
md:   1rem      (16px)  - Padrão
lg:   1.5rem    (24px)  - Entre elementos
xl:   2rem      (32px)  - Entre seções
2xl:  3rem      (48px)  - Padding de seções
3xl:  4rem      (64px)  - Espaços grandes
```

### Container Padrão

```html
<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
  <!-- Conteúdo -->
</div>
```

**Comportamento:**
- Max width: 1280px
- Padding horizontal responsivo:
  - Mobile: 16px (`px-4`)
  - Tablet: 24px (`sm:px-6`)
  - Desktop: 32px (`lg:px-8`)

### Grids Responsivos

```html
<!-- 1 col → 3 cols (trilhas) -->
<div class="grid grid-cols-1 md:grid-cols-3 gap-8">

<!-- 1 col → 2 cols -->
<div class="grid grid-cols-1 lg:grid-cols-2 gap-6">

<!-- 2 cols → 4 cols (stats) -->
<div class="grid grid-cols-2 lg:grid-cols-4 gap-4">
```

### Breakpoints

```
sm:  640px   - Smartphone landscape
md:  768px   - Tablets
lg:  1024px  - Desktop
xl:  1280px  - Large desktop
```

---

## Componentes

### 1. Navegação

```html
<nav class="sticky top-0 z-50 bg-white dark:bg-neutral-900 shadow-sm">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="flex justify-between items-center h-16">
      <!-- Logo -->
      <a href="/" class="text-2xl font-bold bg-gradient-to-r from-emerald-500 via-blue-500 to-purple-500 bg-clip-text text-transparent">
        TDS
      </a>

      <!-- Desktop Menu -->
      <div class="hidden md:flex space-x-8">
        <a href="#" class="text-neutral-700 dark:text-neutral-300 hover:text-emerald-500">Vendas</a>
        <a href="#" class="text-neutral-700 dark:text-neutral-300 hover:text-blue-500">Redes Sociais</a>
        <a href="#" class="text-neutral-700 dark:text-neutral-300 hover:text-purple-500">Negócios</a>
      </div>

      <!-- Theme Toggle + Mobile Menu -->
      <div class="flex items-center gap-4">
        <button id="theme-toggle">...</button>
        <button class="md:hidden" id="mobile-menu-btn">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
          </svg>
        </button>
      </div>
    </div>
  </div>
</nav>
```

**Propriedades:**
- Posição: `sticky top-0`
- Z-index: `50`
- Altura: `h-16` (64px)
- Shadow: `shadow-sm`

---

### 2. Hero Section (Página Principal)

```html
<section class="bg-gradient-to-br from-emerald-500 via-blue-600 to-purple-600 py-20">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center text-white">
    <h1 class="text-4xl sm:text-6xl font-bold mb-6">
      Transformação Digital e Social
    </h1>
    <p class="text-xl sm:text-2xl mb-8 text-white/90">
      Domine Vendas, Redes Sociais e Negócios
    </p>
    <button class="bg-white text-emerald-600 px-8 py-4 rounded-lg font-bold text-lg hover:bg-neutral-100">
      Começar Agora
    </button>
  </div>
</section>
```

### 3. Hero Section (Trilha Individual)

```html
<!-- Exemplo: Trilha Vendas -->
<section class="bg-gradient-to-br from-emerald-500 to-emerald-600 py-16">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <a href="../" class="inline-flex items-center text-white/80 hover:text-white mb-6">
      <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path>
      </svg>
      Voltar para Trilhas
    </a>
    <div class="flex items-center mb-4">
      <span class="text-5xl mr-4">💰</span>
      <h1 class="text-4xl sm:text-5xl font-bold text-white">Trilha Vendas</h1>
    </div>
    <p class="text-xl text-white/90 max-w-2xl">
      Descrição da trilha
    </p>
  </div>
</section>
```

---

### 4. Cards de Trilha

```html
<div class="grid grid-cols-1 md:grid-cols-3 gap-8">

  <!-- Card Vendas -->
  <div class="group bg-gradient-to-br from-emerald-50 to-white dark:from-emerald-900/20 dark:to-neutral-800 border-2 border-emerald-200 dark:border-emerald-800 hover:border-emerald-400 dark:hover:border-emerald-600 rounded-2xl p-8 transition-all hover:-translate-y-1 hover:shadow-xl cursor-pointer">
    <div class="text-5xl mb-4">💰</div>
    <h3 class="text-2xl font-bold text-neutral-900 dark:text-neutral-100 mb-2">Vendas</h3>

    <!-- Badge -->
    <span class="inline-block px-3 py-1 bg-emerald-500 text-white text-sm font-semibold rounded-full mb-4">
      6 Módulos
    </span>

    <p class="text-neutral-600 dark:text-neutral-400 mb-6">
      Estratégias para vender mais
    </p>

    <!-- Lista de tópicos -->
    <ul class="space-y-2 mb-6">
      <li class="flex items-start">
        <span class="text-emerald-500 mr-2">✓</span>
        <span class="text-neutral-700 dark:text-neutral-300">Precificação</span>
      </li>
      <li class="flex items-start">
        <span class="text-emerald-500 mr-2">✓</span>
        <span class="text-neutral-700 dark:text-neutral-300">Técnicas de Fechamento</span>
      </li>
    </ul>

    <!-- Botão -->
    <button class="w-full bg-emerald-500 text-white py-3 rounded-lg font-semibold hover:bg-emerald-600 group-hover:shadow-lg transition-all">
      Acessar Trilha
    </button>
  </div>

  <!-- Repita para Redes Sociais (blue) e Negócios (purple) -->

</div>
```

**Efeitos:**
- Hover: `translateY(-4px)` + `shadow-xl`
- Transition: `0.3s ease`
- Border radius: `rounded-2xl`

---

### 5. Módulos (Cards de Módulo)

```html
<div class="module-card bg-white dark:bg-neutral-800 rounded-xl shadow-md overflow-hidden">
  <!-- Header do Módulo -->
  <div class="bg-emerald-500 px-6 py-4">
    <div class="flex items-center justify-between">
      <h2 class="text-xl font-bold text-white flex items-center">
        <span class="mr-3">📊</span>
        Módulo 1: Fundamentos
      </h2>
      <span class="bg-white/20 text-white text-sm px-3 py-1 rounded-full">
        5 tópicos
      </span>
    </div>
  </div>

  <!-- Lista de Tópicos -->
  <div class="p-6">
    <ul class="topics-list space-y-1">
      <li class="topic-item">
        <button class="topic-button w-full text-left px-4 py-3 bg-neutral-50 dark:bg-neutral-700 hover:bg-emerald-50 dark:hover:bg-emerald-900/20 rounded-lg transition-colors font-medium text-neutral-800 dark:text-neutral-200 flex items-center">
          <span class="text-emerald-500 mr-3">01</span>
          Nome do Tópico
          <svg class="w-5 h-5 ml-auto text-neutral-400 transform transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path>
          </svg>
        </button>

        <div class="topic-explanation hidden mt-2 p-4 bg-emerald-50 dark:bg-emerald-900/20 rounded-lg border-l-4 border-emerald-500">
          <p class="text-sm mb-2 text-neutral-700 dark:text-neutral-300">
            <strong class="text-emerald-600 dark:text-emerald-400">O que é:</strong> Explicação clara
          </p>
          <p class="text-sm mb-2 text-neutral-700 dark:text-neutral-300">
            <strong class="text-emerald-600 dark:text-emerald-400">Por que aprender:</strong> Benefícios
          </p>
          <p class="text-sm text-neutral-700 dark:text-neutral-300">
            <strong class="text-emerald-600 dark:text-emerald-400">Conceitos chave:</strong> Termos importantes
          </p>
        </div>
      </li>
    </ul>
  </div>
</div>
```

**JavaScript para Accordion:**
```javascript
document.addEventListener('click', function(e) {
  const topicButton = e.target.closest('.topic-button');

  if (topicButton) {
    const topicItem = topicButton.closest('.topic-item');
    const explanation = topicItem.querySelector('.topic-explanation');
    const chevron = topicButton.querySelector('svg');

    if (explanation) {
      // Fechar outros tópicos (accordion behavior)
      const moduleCard = topicItem.closest('.module-card');
      moduleCard.querySelectorAll('.topic-explanation').forEach(exp => {
        if (exp !== explanation) {
          exp.classList.add('hidden');
          exp.closest('.topic-item').querySelector('svg').classList.remove('rotate-180');
        }
      });

      // Toggle atual
      explanation.classList.toggle('hidden');
      chevron.classList.toggle('rotate-180');
    }
  }
});
```

---

### 6. Botões

```html
<!-- Primário (cor da trilha) -->
<button class="bg-emerald-500 text-white px-6 py-3 rounded-lg font-semibold hover:bg-emerald-600 transition-colors">
  Acessar
</button>

<!-- Secundário (outline) -->
<button class="bg-transparent border-2 border-emerald-500 text-emerald-500 dark:text-emerald-400 px-6 py-3 rounded-lg font-semibold hover:bg-emerald-50 dark:hover:bg-emerald-900/20 transition-colors">
  Ver Detalhes
</button>

<!-- Ghost (texto apenas) -->
<button class="text-emerald-600 dark:text-emerald-400 font-semibold hover:underline">
  Saiba mais →
</button>
```

---

### 7. Badges

```html
<!-- Vendas -->
<span class="inline-block px-3 py-1 bg-emerald-500 text-white text-sm font-semibold rounded-full">
  6 Módulos
</span>

<!-- Redes Sociais -->
<span class="inline-block px-3 py-1 bg-blue-500 text-white text-sm font-semibold rounded-full">
  8 Módulos
</span>

<!-- Negócios -->
<span class="inline-block px-3 py-1 bg-purple-500 text-white text-sm font-semibold rounded-full">
  8 Módulos
</span>

<!-- Badge Outline -->
<span class="inline-block px-3 py-1 border border-emerald-500 text-emerald-600 dark:text-emerald-400 text-sm font-semibold rounded-full">
  Novo
</span>
```

---

### 8. Modal

#### Estrutura Base do Modal

```html
<div id="modal-exemplo" class="modal">
  <div class="modal-content">
    <!-- Header -->
    <div class="modal-header dark:border-neutral-700">
      <h2 class="text-2xl font-bold text-neutral-900 dark:text-neutral-100">
        💰 Título do Modal
      </h2>
      <button class="close-modal">&times;</button>
    </div>

    <!-- Body -->
    <div class="modal-body">
      <!-- Conteúdo rico aqui -->
    </div>
  </div>
</div>
```

**CSS do Modal:**
```css
.modal {
  display: none;
  position: fixed;
  z-index: 100;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0,0,0,0.6);
  backdrop-filter: blur(4px);
}

.modal.active {
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal-content {
  background-color: white;
  margin: auto;
  padding: 0;
  width: 90%;
  max-width: 1000px;
  max-height: 90vh;
  border-radius: 1rem;
  overflow: hidden;
  box-shadow: 0 20px 25px rgba(0,0,0,0.3);
}

.dark .modal-content {
  background-color: #262626;
}

.modal-header {
  padding: 1.5rem 2rem;
  border-bottom: 1px solid #e5e7eb;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.dark .modal-header {
  border-bottom-color: #404040;
}

.modal-body {
  padding: 2rem;
  overflow-y: auto;
  max-height: calc(90vh - 80px);
}

.close-modal {
  color: #9ca3af;
  font-size: 2rem;
  font-weight: 700;
  cursor: pointer;
  transition: color 0.2s;
}

.close-modal:hover {
  color: #ef4444;
}
```

**JavaScript do Modal:**
```javascript
function openModal(modalId) {
  const modal = document.getElementById(modalId);
  modal.classList.add('active');
  document.body.style.overflow = 'hidden';
}

function closeModal(modalId) {
  const modal = document.getElementById(modalId);
  modal.classList.remove('active');
  document.body.style.overflow = 'auto';
}

document.addEventListener('click', function(e) {
  if (e.target.classList.contains('modal')) {
    e.target.classList.remove('active');
    document.body.style.overflow = 'auto';
  }

  if (e.target.classList.contains('close-modal')) {
    const modal = e.target.closest('.modal');
    modal.classList.remove('active');
    document.body.style.overflow = 'auto';
  }
});

document.addEventListener('keydown', function(e) {
  if (e.key === 'Escape') {
    const activeModals = document.querySelectorAll('.modal.active');
    activeModals.forEach(modal => {
      modal.classList.remove('active');
      document.body.style.overflow = 'auto';
    });
  }
});
```

---

### 9. Stats Section

```html
<section class="bg-neutral-900 dark:bg-neutral-950 py-16">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="grid grid-cols-2 lg:grid-cols-4 gap-8 text-center">
      <div>
        <div class="text-4xl font-bold text-emerald-400 mb-2">22+</div>
        <div class="text-neutral-400">Módulos</div>
      </div>
      <div>
        <div class="text-4xl font-bold text-blue-400 mb-2">100+</div>
        <div class="text-neutral-400">Tópicos</div>
      </div>
      <div>
        <div class="text-4xl font-bold text-purple-400 mb-2">3</div>
        <div class="text-neutral-400">Trilhas</div>
      </div>
      <div>
        <div class="text-4xl font-bold text-pink-400 mb-2">24/7</div>
        <div class="text-neutral-400">Acesso</div>
      </div>
    </div>
  </div>
</section>
```

---

### 10. Footer

```html
<footer class="bg-neutral-900 dark:bg-neutral-950 text-white py-12">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="grid grid-cols-1 md:grid-cols-4 gap-8">

      <!-- Coluna 1: Logo -->
      <div class="col-span-1 md:col-span-2">
        <h3 class="text-2xl font-bold bg-gradient-to-r from-emerald-400 via-blue-400 to-purple-400 bg-clip-text text-transparent mb-4">
          TDS
        </h3>
        <p class="text-neutral-400 text-sm max-w-md">
          Transformação Digital e Social - Seu caminho para dominar vendas, redes sociais e negócios digitais.
        </p>
      </div>

      <!-- Coluna 2: Trilhas -->
      <div>
        <h4 class="font-semibold mb-4">Trilhas</h4>
        <ul class="space-y-2 text-sm">
          <li><a href="vendas/" class="text-neutral-400 hover:text-emerald-400">💰 Vendas</a></li>
          <li><a href="redes-sociais/" class="text-neutral-400 hover:text-blue-400">📱 Redes Sociais</a></li>
          <li><a href="negocios/" class="text-neutral-400 hover:text-purple-400">🏢 Negócios</a></li>
        </ul>
      </div>

      <!-- Coluna 3: Contato -->
      <div>
        <h4 class="font-semibold mb-4">Contato</h4>
        <p class="text-neutral-400 text-sm">inematds@gmail.com</p>
        <div class="flex gap-4 mt-4">
          <a href="#" class="text-neutral-400 hover:text-white">
            <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">...</svg>
          </a>
        </div>
      </div>

    </div>

    <div class="border-t border-neutral-800 mt-8 pt-8 text-center text-sm text-neutral-500">
      <p>&copy; 2025 TDS - Transformação Digital e Social. Todos os direitos reservados.</p>
    </div>
  </div>
</footer>
```

---

## Animações

### Princípios

1. Usar apenas `transform` e `opacity` (performance)
2. Duração: 0.2s-0.8s
3. Easing: `ease-out` ou `cubic-bezier(0.4, 0, 0.2, 1)`
4. Respeitar `prefers-reduced-motion`

### Animações Definidas

```css
/* Fade In */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in {
  animation: fadeIn 0.8s ease-out;
}

/* Card Hover */
.card {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 20px 25px -5px rgba(0,0,0,0.1);
}

/* Button Active */
button:active {
  transform: scale(0.98);
}

/* Chevron Rotation */
.chevron {
  transition: transform 0.3s ease;
}

.chevron.rotate-180 {
  transform: rotate(180deg);
}
```

### Reduced Motion

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## Responsividade

### Estratégia: Mobile-First

```
Base (Mobile):     < 640px
Tablet (sm):       >= 640px
Desktop (md):      >= 768px
Large Desktop (lg): >= 1024px
XL Desktop (xl):   >= 1280px
```

### Padrões Comuns

```html
<!-- Texto responsivo -->
<h1 class="text-4xl lg:text-6xl">Título</h1>
<p class="text-base lg:text-lg">Texto</p>

<!-- Grid responsivo -->
<div class="grid grid-cols-1 md:grid-cols-3 gap-8">

<!-- Padding responsivo -->
<section class="py-12 lg:py-20">

<!-- Visibilidade -->
<div class="hidden md:block">Só desktop</div>
<div class="md:hidden">Só mobile</div>

<!-- Flex direction -->
<div class="flex flex-col sm:flex-row gap-4">
```

---

## Código de Exemplo Completo

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>TDS - Transformação Digital e Social</title>

  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      darkMode: 'class',
    }
  </script>

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">

  <style>
    body {
      font-family: 'Inter', sans-serif;
    }
  </style>
</head>
<body class="bg-neutral-100 dark:bg-neutral-900">

  <!-- Navegação -->
  <nav class="sticky top-0 z-50 bg-white dark:bg-neutral-900 shadow-sm">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-16">
        <a href="/" class="text-2xl font-bold bg-gradient-to-r from-emerald-500 via-blue-500 to-purple-500 bg-clip-text text-transparent">
          TDS
        </a>
        <div class="hidden md:flex space-x-8">
          <a href="vendas/" class="text-neutral-700 dark:text-neutral-300 hover:text-emerald-500">Vendas</a>
          <a href="redes-sociais/" class="text-neutral-700 dark:text-neutral-300 hover:text-blue-500">Redes Sociais</a>
          <a href="negocios/" class="text-neutral-700 dark:text-neutral-300 hover:text-purple-500">Negócios</a>
        </div>
      </div>
    </div>
  </nav>

  <!-- Hero -->
  <section class="bg-gradient-to-br from-emerald-500 via-blue-600 to-purple-600 py-20">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center text-white">
      <h1 class="text-4xl sm:text-6xl font-bold mb-6">
        Transformação Digital e Social
      </h1>
      <p class="text-xl sm:text-2xl mb-8 text-white/90">
        Domine Vendas, Redes Sociais e Negócios
      </p>
      <button class="bg-white text-emerald-600 px-8 py-4 rounded-lg font-bold hover:bg-neutral-100 transition-colors">
        Começar Agora
      </button>
    </div>
  </section>

  <!-- Cards de Trilha -->
  <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-20">
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8">

      <!-- Card Vendas -->
      <div class="bg-gradient-to-br from-emerald-50 to-white dark:from-emerald-900/20 dark:to-neutral-800 border-2 border-emerald-200 dark:border-emerald-800 hover:border-emerald-400 rounded-2xl p-8 transition-all hover:-translate-y-1 hover:shadow-xl">
        <div class="text-4xl mb-4">💰</div>
        <h3 class="text-2xl font-bold text-neutral-900 dark:text-neutral-100 mb-2">Vendas</h3>
        <span class="inline-block px-3 py-1 bg-emerald-500 text-white text-sm font-semibold rounded-full mb-4">
          6 Módulos
        </span>
        <p class="text-neutral-600 dark:text-neutral-400 mb-6">Estratégias de vendas digitais</p>
        <button class="w-full bg-emerald-500 text-white py-3 rounded-lg font-semibold hover:bg-emerald-600 transition-colors">
          Acessar
        </button>
      </div>

      <!-- Card Redes Sociais -->
      <div class="bg-gradient-to-br from-blue-50 to-white dark:from-blue-900/20 dark:to-neutral-800 border-2 border-blue-200 dark:border-blue-800 hover:border-blue-400 rounded-2xl p-8 transition-all hover:-translate-y-1 hover:shadow-xl">
        <div class="text-4xl mb-4">📱</div>
        <h3 class="text-2xl font-bold text-neutral-900 dark:text-neutral-100 mb-2">Redes Sociais</h3>
        <span class="inline-block px-3 py-1 bg-blue-500 text-white text-sm font-semibold rounded-full mb-4">
          8 Módulos
        </span>
        <p class="text-neutral-600 dark:text-neutral-400 mb-6">Marketing e engajamento</p>
        <button class="w-full bg-blue-500 text-white py-3 rounded-lg font-semibold hover:bg-blue-600 transition-colors">
          Acessar
        </button>
      </div>

      <!-- Card Negócios -->
      <div class="bg-gradient-to-br from-purple-50 to-white dark:from-purple-900/20 dark:to-neutral-800 border-2 border-purple-200 dark:border-purple-800 hover:border-purple-400 rounded-2xl p-8 transition-all hover:-translate-y-1 hover:shadow-xl">
        <div class="text-4xl mb-4">🏢</div>
        <h3 class="text-2xl font-bold text-neutral-900 dark:text-neutral-100 mb-2">Negócios</h3>
        <span class="inline-block px-3 py-1 bg-purple-500 text-white text-sm font-semibold rounded-full mb-4">
          8 Módulos
        </span>
        <p class="text-neutral-600 dark:text-neutral-400 mb-6">Automação e escalabilidade</p>
        <button class="w-full bg-purple-500 text-white py-3 rounded-lg font-semibold hover:bg-purple-600 transition-colors">
          Acessar
        </button>
      </div>

    </div>
  </section>

  <!-- Footer -->
  <footer class="bg-neutral-900 text-white py-12">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
      <p class="text-neutral-400">&copy; 2025 TDS</p>
    </div>
  </footer>

</body>
</html>
```

---

## Quick Reference

### Classes Mais Usadas

```css
/* Containers */
.container       → max-w-7xl mx-auto px-4 sm:px-6 lg:px-8

/* Cards */
.card            → bg-white dark:bg-neutral-800 rounded-xl shadow-md p-6

/* Buttons por Trilha */
.btn-vendas      → bg-emerald-500 text-white px-6 py-3 rounded-lg hover:bg-emerald-600
.btn-social      → bg-blue-500 text-white px-6 py-3 rounded-lg hover:bg-blue-600
.btn-negocios    → bg-purple-500 text-white px-6 py-3 rounded-lg hover:bg-purple-600

/* Text */
.title           → text-4xl lg:text-6xl font-bold
.subtitle        → text-xl lg:text-2xl text-neutral-600 dark:text-neutral-400

/* Spacing */
.section-padding → py-12 lg:py-20
.card-gap        → gap-6 lg:gap-8
```

---

## Checklist de Implementação

- [ ] Incluir Tailwind CSS CDN com darkMode: 'class'
- [ ] Incluir Google Fonts (Inter)
- [ ] Usar cores corretas por trilha (emerald/blue/purple)
- [ ] Aplicar espaçamento consistente
- [ ] Testar responsividade (mobile, tablet, desktop)
- [ ] Implementar dark mode em todos os componentes
- [ ] Adicionar animações suaves
- [ ] Implementar acessibilidade (ARIA, focus)
- [ ] Testar com prefers-reduced-motion
- [ ] Validar contraste de cores (WCAG AA)

---

## Estrutura de Arquivos

```
curso/
├── index.html              # Página principal com 3 trilhas
├── vendas/
│   └── index.html          # Trilha Vendas (6 módulos)
├── redes-sociais/
│   └── index.html          # Trilha Redes Sociais (8 módulos)
├── negocios/
│   └── index.html          # Trilha Negócios (8 módulos)
└── assets/
    ├── css/                # Estilos customizados (se necessário)
    ├── js/                 # Scripts customizados (se necessário)
    └── img/                # Imagens e ícones
```

---

**Última atualização:** 2025-11-30
**Versão:** 1.0
**Autor:** TDS Team
**Repositório:** https://github.com/inematds/TDS

---
