# Croqui de Moda PRO — loja do pack de croquis do Joel

Landing page / loja de venda do pack de croquis do Joel Coveero (@joelcoveero).
Site estático simples (HTML puro, sem build, sem backend) — feito para ser
barato de manter (hospedagem gratuita) e fácil de atualizar.

## Estrutura

- `index.html` — página única com todo o conteúdo e estilo (sem dependências externas).
- `assets/` — imagens do site, todas em WebP (ver "Imagens em WebP" abaixo).
- `privacidade.html`, `termos.html`, `legal.css` — páginas legais.


## Ordem das seções e conversão

A página foi reorganizada a partir da auditoria de conversão (agosto/2026).
São 10 seções, nesta ordem:

1. **Hero** — título, preço junto do botão (`.hero-price`) e a régua de números.
2. **`#pack`** — o que vem no pack.
3. **`#videos`** — "Veja o pack em ação". Era a oitava seção; subiu porque é a
   prova visual mais forte e quem chega de anúncio decide antes de rolar tudo.
4. **`#processo`** — do traço ao croqui pronto.
5. **`#tutoriais`** — mini curso.
6. **`#fluxo`** — trabalhe do seu jeito.
7. **`#joel`** — quem assina o pack. Junta as três seções que antes falavam da
   credibilidade do Joel em endereços separados (`#confianca`, `#joel` e
   `#traco`): foto, bio, colaborações e mural do portfólio agora vivem no mesmo
   bloco, com `h3` nos sub-blocos para manter um `h2` por seção.
8. **`#depoimentos`** — existe como modelo comentado no HTML, logo depois do
   `#joel`. **Descomentar só quando houver depoimento real.** A instrução de
   como conseguir está no próprio comentário.
9. **`#porque`** — quebra das objeções (IA e Pinterest), logo antes do preço.
10. **`#preco` → `#faq`**.

Há **4 CTAs no meio da página** (`.cta-inline`), um ao fim de cada bloco que
acaba de vencer uma objeção: depois de `#videos`, `#tutoriais`, `#joel` e
`#porque`. Antes existiam só dois botões no corpo inteiro — o do hero e o do
preço — com mais de dez mil pixels de distância entre eles.

O preço aparece em dois lugares além do card: junto do botão do hero e na
linha `.price-math` do card (`R$ 3,61 por modelo`). Preço visível cedo
qualifica: quem acha caro sai antes de consumir orçamento de anúncio.

### No mobile

O carrossel do hero virou uma faixa (`16/9` em vez de quadrado) e o parágrafo
longo desceu para depois do botão, via `order` no `.hero-copy`. Com isso o CTA
principal passou a caber na primeira tela — antes ele só aparecia 1,4 tela
abaixo da dobra.

## Imagens em WebP

Todas as imagens do site são `.webp` (convertidas com `sharp`, qualidade 88
para PNG e 80 para JPEG). O total saiu de **5,5 MB para 2,3 MB**, sem
diferença visível — os PNG do processo caíram até 90%.

A única exceção é `assets/hero-croqui.png`, mantida em PNG porque é a imagem
usada em `og:image` / `twitter:image`: nem todo robô de preview de link lê
WebP. Ela não é carregada pela página.

Tudo que fica abaixo da dobra tem `loading="lazy"` e `decoding="async"`. Se
precisar reconverter depois de trocar alguma imagem, o comando é
`npx sharp-cli --input <arquivo> --output <pasta> --format webp`.

## Páginas legais

- `privacidade.html` — política de privacidade (LGPD).
- `termos.html` — termos de uso, licença dos arquivos e garantia de 7 dias.
- `legal.css` — estilo compartilhado pelas duas.

**As duas têm campos em laranja para preencher** (nome/razão social, CPF ou
CNPJ, e-mail de contato, cidade/UF). Sem isso elas não cumprem a LGPD e não
servem para aprovar a conta de anúncios — a Meta exige política de privacidade
acessível, e o Pixel coleta dado pessoal.

A seção de licença do `termos.html` merece leitura atenta: é ela que separa
"o cliente pode usar nos trabalhos dele" de "o cliente pode revender o pack".
## O que falta preencher antes de divulgar

1. **Seção "Do traço ao croqui pronto"** (`#processo`) — galeria em acordeão
   com as 5 fotos isoladas (sem legenda) que o Lindberg enviou pra pasta
   "passo a passo" do Drive (`assets/process-1.webp` a `process-5.webp`, fundo
   branco removido via chroma-key). Passe o mouse (ou toque) numa etapa e
   ela expande, ganha cor e mostra a legenda; as outras ficam estreitas,
   em preto e branco e levemente inclinadas em 3D. No mobile vira um
   acordeão vertical. Ver seção "Dependência externa: GSAP" abaixo.
2. **Foto do Joel** (seção `#joel`) — trocada para `assets/joel-foto.webp`,
   a foto confirmada pelo Lindberg (com o Sonic, na pasta `JOEL FOTOS` do
   Drive, arquivo `IMG_0911.JPG`).
3. **"Texturas de papel"** (card na seção `#pack` e item no `#preco`) — copy
   nova descrevendo texturas de papel/tecido incluídas no pack. Ainda não
   recebi os arquivos de exemplo, então confirmem se esse conteúdo já existe
   e bate com a descrição antes de divulgar.
4. **Botão de compra** (seção `#preco`, `id="checkout-btn"`) — hoje ele abre o
   WhatsApp para lista de espera. Quando o pack estiver pronto e cadastrado
   numa plataforma de checkout, troque o `href` pelo link real de pagamento.
5. Revisar preço, texto do pack e da bio do Joel — o texto atual foi montado
   a partir do Instagram público, confirme os detalhes com ele.
6. **Imagens do hero** (`#hero-carousel`) — carrossel com crossfade automático
   (troca a cada 3,5s) usando 5 bases reais do pack (`assets/hero-base-1.webp`
   a `hero-base-5.webp`), enviadas pelo Lindberg pra pasta
   `1e2M9CP5kKTX14Oie5VWbsuBtau1I6_As` do Drive.
7. **Seção "O traço do Joel"** (`#traco`) — virou um mural 3D em movimento
   (DriftWall) com 16 imagens da pasta `1msNQdJ4eAAyXe42uZWKG7Bu8AEwN9K_g`
   do Drive, em `assets/wall/wall-01.webp` a `wall-16.webp` (redimensionadas
   pra 700px, ~930 KB no total). A pasta tinha 3 vídeos `.MOV` que ignorei —
   o componente é só de imagens. Pra trocar/adicionar imagens, coloque os
   arquivos em `assets/wall/` e atualize a lista `IMAGES` no script do
   DriftWall, no fim do `index.html`.
8. **Domínio no `<head>`** — `canonical`, `og:url` e `og:image` estão
   apontando para `https://croquidemodapro.com.br/`, um domínio placeholder
   que ainda não existe. Troque pelas URLs reais assim que vocês registrarem
   o domínio e definirem onde o site vai ficar publicado.
9. **Seção "Trusted By"** (`#confianca`) — os avatares de Ludmilla, KATSEYE e
   ssjheni são só as iniciais (L/K/S) coloridas, não as fotos reais deles.
   Preferi não puxar as fotos de perfil de terceiros sem autorização deles
   pra usar num site comercial; se quiserem trocar por fotos/logos reais,
   é só substituir o conteúdo de `.trust-avatar` em cada card.
10. **Seção "Veja o pack em ação"** (`#videos`) — os embeds do Instagram
   foram substituídos pela CircularGallery com 15 imagens da pasta
   `1QZpiyF5W7i7i2SM3484b3EIsfsRIb8Tk` do Drive, em `assets/carrossel/`
   (`g01.webp` a `g15.webp`, ~660 KB no total). Elas mostram o croqui ao lado
   da peça já executada, que é a prova mais forte do produto.
   - **Atenção**: dois arquivos originais (`IMG_7668.JPG` e `IMG_7946.JPG`)
     têm resolução muito baixa (175x219 e 179x224 px, 13 KB e 20 KB) e
     aparecem borrados na galeria. Se tiverem as versões em tamanho cheio,
     é só substituir `g09.webp` e `g12.webp`.
   - As legendas estão como "Look 01"… "Look 15" por não sabermos o nome
     de cada peça. Se quiserem nomes reais, me mandem a lista.
11. **Seção "Tutoriais"** (`#tutoriais`) — as 4 aulas (estampas com IA,
   coleções consistentes com IA, como importar/usar, como imprimir) empilham
   conforme a página rola (ScrollStack), mas ainda são só capa + "em breve"/
   "mini curso incluso", sem vídeo de verdade (procurem o comentário `TODO`
   no `index.html`). Quando gravarem, subam no YouTube (pode ser "não
   listado") e troquem o `.tut-thumb` de cada card pelo iframe de embed do
   YouTube — é só me mandar os links que eu faço.
12. **Contadores de conteúdo** — o hero anuncia **4 aulas, 15 texturas e 20
   brushes**, números passados pelo Lindberg. Ainda não vi esses arquivos, e
   as aulas ainda não foram gravadas — confiram se os números batem com o
   pack final antes de anunciar. Eles aparecem em três lugares: o
   `stat-strip` do hero, os cards da seção `#pack` e a lista do `#preco`.

## SEO e copy

Título, meta descrição, textos de venda e a estrutura de "O que vem no pack"
vieram de um briefing que vocês já tinham montado com o ChatGPT (diferenciais
e conteúdo real: 27 modelos × 3 versões = 77 arquivos). Nome do produto:
**Croqui de Moda PRO** — trocado de "Fashion Croqui PRO" porque "croqui de
moda" é o termo que as pessoas de fato buscam no Google; como o produto ainda
não tinha sido lançado/divulgado, trocar o nome agora não tem custo de marca.

Ajustes feitos para SEO/atrair estudante de moda:
- H1 e brand agora contêm a frase "croqui de moda" (antes o H1 não tinha
  nenhuma palavra-chave, só a copy de persuasão);
- o parágrafo do hero menciona explicitamente **TCC, portfólio e trabalhos
  da faculdade** — os momentos reais em que um estudante de moda procura isso;
- adicionei um segundo JSON-LD (`FAQPage`, no `<head>`) reaproveitando as
  perguntas da seção `#faq`, pra tentar ganhar rich snippet no Google.

Vale ter expectativa realista: página única, sem backlinks, dificilmente
rankeia organicamente para um termo concorrido como "croqui de moda" — o SEO
aqui ajuda mais em busca de marca (quem viu o anúncio no Instagram e busca
"croqui de moda pro" no Google) e no preview ao compartilhar o link. O canal
de crescimento principal continua sendo o Instagram pago, como já planejado.

Se o preço, nome final ou conteúdo do pack mudar, atualize também:
- `<title>`, `meta description`, tags `og:*`/`twitter:*` e os dois JSON-LD no
  `<head>` do `index.html`;
- a seção `#preco` (preço e itens inclusos).

## Recomendação de checkout (produto digital, público brasileiro)

Em vez de construir um checkout/pagamento do zero (caro e trabalhoso de manter
com segurança), use uma plataforma pronta de produto digital:

- **Kiwify**, **Hotmart** ou **Eduzz** — sem mensalidade, cobram só uma taxa
  por venda (Pix, cartão, boleto), cuidam de nota fiscal, entrega automática
  do arquivo por e-mail e (se quiser) programa de afiliados.
- Passo a passo: criar conta na plataforma escolhida → cadastrar o "Croqui
  PRO" como produto digital → subir o arquivo final do pack → copiar o link
  de checkout → colar no `href` do botão `#checkout-btn` no `index.html`.

## Componentes do React Bits portados para JS puro

Treze componentes do [React Bits](https://reactbits.dev) estão em uso:

| Componente | Onde |
|---|---|
| **AccordionGallery** | `#processo` — etapas do processo |
| **DriftWall** | `#traco` — mural 3D de trabalhos |
| **SplitText** | todos os títulos de seção (`<h2>`) |
| **Strands** | fundo animado do `#preco` |
| **SpecularButton** | botões primários (`.btn`, exceto os `.ghost`) |
| **StarBorder** | moldura do card de preço |
| **CircularGallery** | `#videos` — croquis ao lado das peças reais |
| **TiltedCard** | foto do Joel em `#joel` |
| **CountUp** | números do hero e de seguidores |
| **LogoLoop** | marquee das tags "Ideal para" |
| **ScrollStack** | aulas do mini curso em `#tutoriais` |
| **StaggeredMenu** | menu sanduíche do topo (mobile) |
| **BorderGlow** | bordas dos cards de `#fluxo` e `#preco` |

Os originais são React, e este site é HTML/CSS/JS estático sem build; adotar
React só por causa deles significaria reescrever o site inteiro. Então todos
foram portados para JS puro, mantendo comportamento, estrutura de classes e
parâmetros dos originais.

O **Strands** e o **SpecularButton** rodam em WebGL e usam a biblioteca
[ogl](https://github.com/oframe/ogl), carregada via CDN. Os shaders são os
mesmos dos componentes originais. Ambos degradam em silêncio: sem WebGL2 ou
sem CDN, o fundo do preço fica vazio e os botões seguem com o gradiente
normal — nada quebra. Os dois também param de renderizar quando saem da
tela, pra não gastar GPU à toa.

No **SpecularButton**, o gradiente rosa→violeta dos botões foi mantido: o
canvas só desenha o realce que corre pela borda, por cima do fundo atual.

O **StarBorder** não usa biblioteca nenhuma — é só CSS. Envolve o card de
preço e faz dois brilhos (violeta em cima, rosa embaixo) correrem pelas
bordas. Parâmetros no `style` inline dos `.border-gradient-*`.

A **CircularGallery** também roda em `ogl` (mesmo CDN). Mostra os 15 arquivos
de `assets/carrossel/` numa curva 3D; arraste com o mouse/dedo ou use as
setas do teclado. Ela deriva sozinha bem devagar pra deixar claro que é
interativa. **Diferença em relação ao original:** o componente do React Bits
captura a roda do mouse da página inteira pra girar a galeria; aqui isso foi
removido, senão rolar a página perto dessa seção viraria "girar o carrossel"
em vez de descer o site. Só arrasto, toque e teclado movem a galeria.

**TiltedCard**, **CountUp** e **LogoLoop** não precisaram de dependência: os
originais usam a biblioteca `motion`, e aqui a mesma sensação foi obtida com
transição CSS (TiltedCard), uma curva de easing (CountUp) e um loop de
`requestAnimationFrame` (LogoLoop).

O **ScrollStack** empilha as aulas do mini curso conforme a página rola.
**Diferença em relação ao original:** ele depende do Lenis, uma biblioteca de
scroll suave que assume o controle da rolagem da página inteira — isso
brigaria com todos os outros efeitos de scroll do site (títulos, contadores,
mural, galeria). Então foi usado o caminho `useWindowScroll` do próprio
componente, com o scroll nativo: mesmos cálculos de empilhamento, sem
sequestrar a rolagem e sem dependência nova.

O **SplitText** quebra cada `<h2>` (ou seja, todo título depois do hero) em
caracteres que sobem e aparecem um após o outro quando o título entra na
tela. O componente original usa o plugin SplitText do GSAP, que é pago —
aqui a quebra é feita na mão e o movimento roda em transição CSS, sem
plugin nenhum. Parâmetros no topo do script (`DELAY` entre caracteres,
`THRESHOLD` e `ROOT_MARGIN` do gatilho de scroll).

O **StaggeredMenu** é o menu sanduíche que aparece só no mobile (até 820px);
no desktop o menu horizontal continua igual. O botão "Quero o meu" fica no
topo nas duas versões — no mobile a marca e o botão encolhem e o menu vira
só o ícone pra caberem os três na mesma linha. **Diferença em relação ao
original:** ele anima com timelines do GSAP; aqui as mesmas entradas em
cascata (as duas camadas coloridas, o painel e cada item subindo um depois
do outro) são feitas com `transition-delay` em CSS, disparadas pela classe
`.sm-open` no `<body>`. Fecha com Esc, clique fora, clique num item ou ao
passar pra largura de desktop, e trava a rolagem do fundo enquanto aberto.

O **BorderGlow** acende a borda dos cards de "Trabalhe do seu jeito" e
"Garanta o seu" conforme o mouse chega perto das bordas: a distância até a
borda vira `--edge-proximity` e o ângulo em volta do centro vira
`--cursor-angle`; o resto é CSS (borda em mesh gradient, preenchimento
interno e o brilho externo em `plus-lighter`). As cores são as do site
(violeta, rosa e lime) e o glow é rosa, na tonalidade da marca. **Diferenças
em relação ao original:** as props viraram custom properties na própria
folha de estilo, o `.border-glow-inner` recorta (`overflow:hidden`) pra
segurar os brilhos do StarBorder dentro do card de preço, e o `animated`
(varredura de apresentação) roda na primeira vez que o card entra na tela,
em vez de na montagem — e não roda com `prefers-reduced-motion`. Em telas de
toque, sem cursor, o card fica no estado de repouso.

Dois cuidados no port: o `overflow:hidden` que mascara os caracteres antes
de subirem é removido ao fim da animação, pra nunca cortar acento ou descida
de letra no estado final; e há uma verificação de scroll como rede de
segurança, caso o `IntersectionObserver` seja suspenso e algum título fique
invisível. Quem usa "reduzir movimento" vê os títulos já prontos.

O **DriftWall** (mural 3D em movimento, no fim do `index.html`) não precisa
de biblioteca nenhuma — roda em `requestAnimationFrame` + CSS. As colunas
sobem/descem em velocidades levemente diferentes, o mural inclina seguindo
o mouse, e passar o cursor num quadro o traz pra frente, devolve a cor e
pausa a coluna dele. Parâmetros no topo do script (`COLUMNS`, `SPEED`,
`TILT`, `TURN`, `PARALLAX`, etc.). Quem usa "reduzir movimento" no sistema
vê o mural parado.


## Acessibilidade

O que já está no site:

- `lang="pt-BR"`, um `<h1>` único e hierarquia de títulos em ordem.
- Todas as imagens com `alt`; elementos decorativos (canvas de fundo, ícones
  de play, cópias do marquee) com `aria-hidden`.
- Link "Pular para o conteúdo", visível ao chegar pelo teclado.
- Anel de foco próprio em todo link, botão e elemento focável — o padrão do
  navegador some no fundo escuro em vários deles.
- Galeria e etapas do processo navegáveis por teclado, com `aria-label`.
- Menu sanduíche: fecha com Esc, devolve o foco pro botão e deixa o resto da
  página `inert` enquanto está aberto.
- `prefers-reduced-motion` respeitado em todos os componentes — inclusive o
  scroll suave, o empilhamento das aulas e as animações WebGL.
- Contraste: `--ink-faint` passou de `#786e93` (4,2:1) para `#8b80a8`
  (~5,2:1), acima do mínimo AA de 4,5:1 para texto normal.

O que ainda vale fazer:

1. **Botão de pausar animações.** A galeria gira sozinha e o marquee das tags
   corre continuamente. A WCAG 2.2.2 pede um jeito de parar movimento
   automático que dure mais de 5s. Hoje o marquee para no hover e a galeria
   para no arrasto, mas quem navega por teclado não tem como parar — um botão
   "pausar animações" no rodapé, gravado no `localStorage`, resolveria.
2. **Legendas e transcrição nos vídeos do mini curso.** Quando os vídeos
   subirem, legenda é requisito (WCAG 1.2.2) e ajuda também quem assiste sem
   som — que é a maioria no Instagram.
3. **Teste com leitor de tela de verdade.** NVDA no Windows ou VoiceOver no
   iPhone, percorrendo a página do topo até o checkout.
4. **Checkout.** A plataforma escolhida (Kiwify/Hotmart/Eduzz) tem a
   acessibilidade dela, fora do nosso controle — vale testar o fluxo de compra
   por teclado antes de anunciar.
## Dependência externa: GSAP (galeria em acordeão)

A seção `#processo` usa o componente **AccordionGallery** do
[React Bits](https://reactbits.dev), mas **portado para JS puro**: o
componente original é React, e este site é HTML/CSS/JS estático sem build
— adotar React só por causa dele significaria reescrever o site inteiro.
O comportamento, a estrutura de classes (`.accordion-gallery`, `.ag-panel`,
`.ag-panel__media`…) e os parâmetros (`expandRatio`, `tilt`, `parallax`,
`stagger`…) seguem os mesmos do original.

A biblioteca [GSAP](https://gsap.com) é carregada via CDN (`jsdelivr`) e
faz as transições. Se o CDN falhar, o script marca a galeria com a classe
`no-gsap` e as transições passam a rodar em CSS puro — a galeria continua
funcionando, só com um movimento mais simples.

Para ajustar o comportamento, os parâmetros estão no topo do script no fim
do `index.html` (`DEFAULT_INDEX`, `EXPAND_RATIO`, `DURATION`, `TILT`, etc.).

## Dependência externa: animações com Motion

Os elementos com `class="reveal"` (cards, seções, o hero) fazem um fade +
leve deslize pra cima quando entram na tela, usando a biblioteca
[Motion](https://motion.dev), carregada via CDN (`jsdelivr`) num `<script
type="module">` no fim do `index.html` — sem build, sem instalar nada.

A animação em si roda em CSS puro (transição na classe `.reveal` /
`.reveal.is-visible`, no `<style>`); a Motion só é usada pro `inView()`
detectar quando cada elemento entra na tela. Isso evita depender de JS pra
renderizar a animação — mais previsível e mais fácil de debugar.

Rede de segurança: se o CDN falhar, o script mostra tudo imediatamente (não
deixa conteúdo invisível numa página de vendas). Quem usa "reduzir
movimento" no sistema não recebe a animação — o conteúdo já aparece visível.

Segunda rede de segurança: além da Motion, o script também checa a posição
de cada elemento "na mão" (sem depender do `IntersectionObserver`) toda vez
que a página rola — cobre navegadores/extensões que atrasam ou suspendem o
observer, e garante que o que já está na tela no carregamento aparece na
hora, mesmo se a Motion demorar pra responder.

## Dependência externa: embeds do Instagram

A seção `#videos` usa o widget oficial de embed do Instagram
(`instagram.com/embed.js`, carregado no fim do `index.html`). Isso significa:
- não baixamos/hospedamos nenhum vídeo — o Instagram serve o player direto
  pelos servidores dele, então continua "grátis" de manter;
- o vídeo só aparece se o script do Instagram carregar no navegador de quem
  visita (pode demorar um instante, ou não carregar se a pessoa estiver com
  bloqueador de rastreadores/anúncios muito agressivo) — por isso cada
  embed tem um link de fallback ("Ver publicação no Instagram") caso o
  player não carregue;
- se o post original for apagado ou ficar privado, o embed para de funcionar.

## Como publicar (gratuito)

Qualquer uma destas opções serve para hospedar de graça, sem servidor:

**GitHub Pages**
```bash
git remote add origin <url-do-seu-repositorio-no-github>
git push -u origin main
```
Depois, em Settings → Pages do repositório, ativar Pages na branch `main`.

**Netlify / Vercel**
Arrastar a pasta do projeto no painel do Netlify ("Deploy manually") ou
conectar o repositório do GitHub — ambos têm plano gratuito suficiente para
este site.

## Rodar localmente

Não precisa de servidor nem instalação — é só abrir o `index.html` direto no
navegador, ou rodar um servidor simples:

```bash
python -m http.server 8000
```
