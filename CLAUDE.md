# CLAUDE.md — Site Dra. Ana Opolski

> Atualizar este arquivo ao final de cada tarefa. Registre o que mudou, o que ficou pendente e qualquer padrão novo descoberto.

---

## Stack e arquitetura

- **HTML estático multi-página** (sem build tool, sem framework JS)
- **Tailwind CSS via CDN** (`https://cdn.tailwindcss.com`) — config inline em cada `.html`
- **Fontes:** Google Fonts — Cormorant Garamond (display/títulos) + DM Sans (corpo)
- **JS:** Inline em cada arquivo, apenas para navbar scroll e interações simples
- Todos os arquivos na raiz. Assets em `Assets/`.

---

## Arquivos do projeto

| Arquivo              | Status   | Descrição                                      |
|----------------------|----------|------------------------------------------------|
| `index.html`         | ✅ feito | Navbar + Hero + Cards chamada + FAQ + Footer   |
| `sobre.html`         | ✅ feito | Mini-hero + Trajetória + Expertise + Consulta  |
| `procedimentos.html` | ✅ feito | Mini-hero + 4 procedimentos alternados + CTA   |
| `contato.html`       | ✅ feito | Mini-hero + Info + Foto + Google Maps embed    |
| `briefing.md`        | —        | Conteúdo e identidade visual completos         |
| `SKILL.md`           | —        | Diretrizes técnicas originais                  |

---

## Design system

### Cores (Tailwind customizado — usar tokens, nunca HEX direto no HTML)

| Token           | HEX       | Uso                                      |
|-----------------|-----------|------------------------------------------|
| `pewter`        | `#86A5A8` | Acento principal, botões, destaques      |
| `jet`           | `#3B3939` | Texto, backgrounds escuros               |
| `linen`         | `#F0E4D8` | Fundos alternados de seção               |
| `pale-copper`   | `#D88366` | Detalhes muito discretos                 |
| `deep-chestnut` | `#B04F44` | Raramente — a médica prefere tons frios  |

A médica **prefere preto, cinza e azul frio**. Minimizar laranjas/cobre.

### Tipografia

```
font-display  →  Cormorant Garamond (títulos, letras grandes)
font-sans     →  DM Sans (corpo, labels, botões)
```

- Títulos grandes: `tracking-tight` ou `-0.03em`
- Corpo: `leading-relaxed` (1.7)

### Componentes padrão (já definidos em CSS inline nos arquivos)

- `.btn-primary` — botão sólido pewter
- `.btn-outline` — botão contorno jet
- `.nav-link` — link navbar com underline animado
- Navbar com efeito `#navbar.scrolled` (blur + sombra pewter ao rolar)

### Anti-padrões — NUNCA fazer

- `transition-all` → usar `transition-colors`, `transition-opacity` ou `transition-transform`
- `shadow-md` puro → usar sombra com tint de cor (ex: `shadow-[0_4px_20px_rgba(134,165,168,0.15)]`)
- Cores padrão Tailwind (`indigo-500`, `blue-600`, etc.) como cor primária

---

## Dados fixos (usar exatamente assim)

```
WhatsApp link: https://wa.me/5541998302323?text=Ol%C3%A1!%20Gostaria%20de%20marcar%20uma%20consulta%20com%20a%20Dra.%20Ana%20Opolski.%20Vim%20pelo%20site
Número:        5541998302323
CRM:           34967  |  RQE: 26861  |  Especialista SBD – SBCD
Endereço:      Clínica Tassi | Av. Visconde de Guarapuava, 4628, Sala 414 – DOC Batel | Curitiba-PR
Horário:       09h–18h, segunda a sexta-feira
Instagram:     @dermato.anaopolski
Lattes:        https://lattes.cnpq.br/5354681590896933
```

---

## Assets principais

```
Assets/Fotos - AO/Hero/vicleardini-anaopolski-90.jpg   ← foto principal
Assets/Logo principal/Logo 1.png                        ← navbar e hero
Assets/Logo principal/Logo 2.png                        ← footer
Assets/Monograma/logo pewter blue.png                   ← monograma preenchido
Assets/Monograma vazado/vazado pewter blue.png          ← monograma vazado
Assets/Fotos - AO/Consultório/recepcao-consultorio.png  ← consultório
```

---

## Restrições CFM (checar em toda edição de conteúdo)

- ❌ Preços, antes/depois, "melhor", "garantido", depoimentos de pacientes
- ✅ CRM e RQE visíveis, linguagem educativa e acolhedora, tom de "estratégia" e "naturalidade"

---

## Padrões de código recorrentes

### Config Tailwind (copiar em todo novo arquivo HTML)
```html
<script src="https://cdn.tailwindcss.com"></script>
<script>
  tailwind.config = {
    theme: {
      extend: {
        colors: {
          linen: '#F0E4D8', 'pale-copper': '#D88366',
          'deep-chestnut': '#B04F44', pewter: '#86A5A8', jet: '#3B3939',
        },
        fontFamily: {
          display: ['"Cormorant Garamond"', 'Georgia', 'serif'],
          sans: ['"DM Sans"', 'system-ui', 'sans-serif'],
        },
      }
    }
  }
</script>
```

### Navbar ativa (marcar página atual com `aria-current="page"` e cor pewter)
```html
<a href="sobre.html" class="nav-link" aria-current="page">Sobre</a>
```

### Mini-hero (padrão das páginas internas)
```html
<section class="bg-jet pt-32 pb-20 text-center">
  <p class="font-sans text-pewter text-xs tracking-[0.25em] uppercase mb-3">...</p>
  <h1 class="font-display text-white text-4xl md:text-6xl font-light">...</h1>
</section>
```

---

## Próximas tarefas possíveis

- Refinamentos visuais em qualquer página (fontes, espaçamentos, responsividade)
- SEO: meta tags, og:image, structured data (LocalBusiness)
- Performance: lazy loading de imagens, preload de fontes críticas
- Acessibilidade: aria-labels, contraste, foco visível
- Novos conteúdos conforme orientação da médica

---

## Histórico de mudanças relevantes

| Data       | O que foi feito                                              |
|------------|--------------------------------------------------------------|
| 2026-03-10 | Todos os 4 arquivos HTML criados e funcionais                |
| 2026-03-10 | Padronização de tamanhos de fonte em todo o site             |
| 2026-03-10 | Efeito de sobreposição entre seções (hero/cards/faq)         |
| 2026-03-10 | Ajustes responsivos na Hero section (mobile)                 |
| 2026-03-10 | Criado CLAUDE.md com contexto completo do projeto            |
