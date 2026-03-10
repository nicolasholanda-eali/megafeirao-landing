# Spec — Landing Page Mega Feirão da Casa Própria

**Data:** 2026-03-10
**Status:** Aprovado
**Evento:** Mega Feirão da Casa Própria — 20, 21 e 22 de Março de 2026
**Local:** Mansão Realize-se · R. Maestro Inácio Stábile, 99 — Alto da Boa Vista, Ribeirão Preto
**Horário:** 8h às 22h
**Custo:** Gratuito
**CTA principal:** Grupo WhatsApp VIP (link a confirmar)

---

## Contexto

Refatoração da landing page existente em `https://megafeiraocasapropria.com.br/inicio`. A página atual tem estrutura funcional mas carece de prova social, credibilidade das empresas parceiras, e estrutura PAS (Problema-Agitação-Solução) adequada.

**Parceiros:** Top Life + Realize-se Imóveis

---

## Decisões de Design

| Decisão | Escolha |
|---------|---------|
| Estilo visual | Bold & Institucional — azul escuro + verde + amarelo |
| Cores principais | `#012e60` (azul) · `#9ac923` (verde) · `#fdc800` (amarelo) |
| Hero | Vídeo de fundo + conteúdo centralizado + countdown |
| Fonte | Inter (Google Fonts) |
| Stack | HTML único · Tailwind CDN · JS nativo |

---

## Estrutura — 11 Seções

### 1. Hero — Vídeo de Fundo + Countdown
- Navbar fixa transparente com logo + CTA "Participar"
- Vídeo MP4 como background com overlay azul escuro (`bg-dark-900/80`)
- Countdown regressivo até 20/03/2026 (dias · horas · minutos · segundos)
- Headline: *"A sua casa própria nunca esteve tão perto."*
- Subheadline: *"Em apenas 1 único dia, você faz todo o processo e sai mais perto de virar a chave da sua casa."*
- Data/local inline: "20-22 Mar · Ribeirão Preto"
- CTA pulsante: "QUERO PARTICIPAR GRÁTIS" → WhatsApp VIP
- **Asset pendente:** vídeo MP4 (placeholder: gradiente animado azul)

### 2. Números — Prova Social
- 4 cards horizontais com contadores animados (IntersectionObserver)
- Métricas placeholder (a confirmar): famílias atendidas · volume negociado · anos no mercado · taxa de aprovação
- Animação: contador de 0 até o valor em 2s ao entrar no viewport

### 3. Dor do Aluguel — PAS Problema *(adição recomendada)*
- 3 cards com ícone + headline emocional + copy curto
- Card 1: 💸 *"Você paga aluguel há anos e não tem nada seu"*
- Card 2: 📈 *"O aluguel sobe todo ano. Seu salário não acompanha."*
- Card 3: 😔 *"Sem patrimônio, sem segurança, sem lugar fixo pra chamar de lar."*
- Hover: blur nos cards irmãos, destaque no card ativo

### 4. O Evento — O que é o Mega Feirão
- Headline de seção + parágrafo explicativo
- Logos das empresas parceiras (Top Life + Realize-se Imóveis)
- Descrição: evento híbrido (WhatsApp + presencial) onde o visitante resolve tudo em 1 dia
- **Asset pendente:** logos das empresas (PNG transparente)

### 5. Benefícios Concretos
- 3 cards com ícone, número em destaque e descrição:
  - 🏠 Entrada parcelada em até **100x** sem juros
  - 💰 Prestação **menor que o aluguel** que você paga hoje
  - ✅ Financiamento via **Minha Casa Minha Vida (MCMV)**
- Animação fade-up staggered ao scroll

### 6. Como Funciona — Timeline 4 Passos
- Timeline vertical com linha conectora e ícones numerados
- ① Inscreva-se no grupo WhatsApp VIP
- ② Compareça ao evento (20-22/03)
- ③ Escolha seu imóvel com ajuda dos especialistas
- ④ Saia com a aprovação do financiamento no mesmo dia

### 7. Equipe — Top Life + Realize-se
- Cards com foto circular + nome + cargo
- Desktop: cursor card flutuante (movido para `document.body` via JS por causa do ghl-wrapper transform)
- Mobile: accordion — click expande, um item por vez
- **Asset pendente:** fotos e nomes dos responsáveis

### 8. Local, Data e Horário
- 3 cards informativos: 📅 20-22 Março 2026 · ⏰ 8h às 22h · 📍 Mansão Realize-se
- Endereço completo: R. Maestro Inácio Stábile, 99 — Alto da Boa Vista, Ribeirão Preto
- Mapa Google Maps embutido via iframe
- Badge "ENTRADA GRATUITA" em destaque verde

### 9. Documentos Necessários
- Grid 2×2 com cards: RG · CPF · Comprovante de renda · Comprovante de residência
- Ícone de documento + nome + dica curta em cada card
- Seção separada com badge "EVENTO GRATUITO — sem taxa de inscrição"

### 10. FAQ — Accordion
- 6 perguntas com animação de abertura (max-height transition)
- Tópicos: custo do evento · como funciona · elegibilidade MCMV · documentação · processo de aprovação · parcelamento da entrada
- Ícone +/× com swap ao abrir/fechar
- Um item aberto por vez

### 11. CTA Final + Footer
- Headline de urgência com countdown de dias restantes
- Copy: *"Vagas limitadas. O evento acontece em X dias."*
- CTA grande pulsante: "GARANTIR MINHA VAGA AGORA — É GRÁTIS"
- Footer: logos · endereço · redes sociais · copyright

---

## Stack Técnico

- **Arquivo:** `index.html` (HTML único, sem build tools)
- **CSS:** Tailwind CDN (`https://cdn.tailwindcss.com`)
- **Fonte:** Inter via Google Fonts
- **GHL Wrapper:** `.ghl-wrapper` com `100vw + translateX(-50%)` para full-width
- **Animações:** IntersectionObserver para fade-up, stagger delays, contador animado
- **Scroll:** smoothScrollTo custom 600ms easeInOutCubic
- **Countdown:** JS nativo, atualiza a cada segundo
- **Equipe cursor card:** movido para `document.body` via JS (evita bug de `transform` no pai)

---

## Assets Pendentes (a receber)

| Asset | Seção | Status |
|-------|-------|--------|
| Vídeo MP4 (hero background) | Hero | Pendente |
| Link do grupo WhatsApp VIP | Todos os CTAs | Pendente |
| Números reais (métricas) | Seção 2 | Pendente |
| Logos Top Life + Realize-se | Seção 4 | Pendente |
| Fotos + nomes da equipe | Seção 7 | Pendente |

---

## Critérios de Sucesso

- Funciona corretamente no GHL (full-width, sem bordas laterais)
- Vídeo com autoplay (muted, loop, playsinline — sem preload)
- Countdown correto até 20/03/2026 às 00:00
- Todos os CTAs apontam para o link do WhatsApp VIP
- Responsivo mobile-first
- Animações suaves ao scroll (fade-up, contadores, stagger)
