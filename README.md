# Croqui de Moda PRO — loja do pack de croquis do Joel

Landing page / loja de venda do pack de croquis do Joel Coveero (@joelcoveero).
Site estático simples (HTML puro, sem build, sem backend) — feito para ser
barato de manter (hospedagem gratuita) e fácil de atualizar.

## Estrutura

- `index.html` — página única com todo o conteúdo e estilo (sem dependências externas).
- `assets/` — pasta para colocar as imagens reais (fotos do Joel, croquis, mockups).

## O que falta preencher antes de divulgar

0. **Seção "Do traço ao croqui pronto"** (`#processo`) — as 5 imagens
   (`assets/process-1.jpg` a `process-5.jpg`) são recortes de uma arte de
   carrossel do Instagram que o Lindberg enviou (imagem "asdasd.jpg" no
   Drive), mostrando um croqui de exemplo evoluindo até a peça final. Os
   recortes têm um pouco de "sangria" das legendas vizinhas nas bordas
   (inevitável, o arquivo original já tinha os slides colados lado a lado)
   — se incomodar, me mandem os slides originais separados que eu troco.
1. **Foto do Joel** (seção `#joel`) — usei `assets/joel-foto.jpg`, uma selfie
   solo puxada da pasta `JOEL FOTOS` do Drive porque era a única com uma
   pessoa só (as outras fotos têm mais gente e eu não tinha como confirmar
   quem era quem). Confirmem com o Joel se é essa a foto que ele quer usar
   publicamente, ou troquem pela que preferirem.
2. **Botão de compra** (seção `#preco`, `id="checkout-btn"`) — hoje ele abre o
   WhatsApp para lista de espera. Quando o pack estiver pronto e cadastrado
   numa plataforma de checkout, troque o `href` pelo link real de pagamento.
3. Revisar preço, texto do pack e da bio do Joel — o texto atual foi montado
   a partir do Instagram público, confirme os detalhes com ele.
4. **Imagens do hero** (`#hero-carousel`) — carrossel com crossfade automático
   (troca a cada 3,5s) usando 5 bases reais do pack (`assets/hero-base-1.png`
   a `hero-base-5.png`), enviadas pelo Lindberg pra pasta
   `1e2M9CP5kKTX14Oie5VWbsuBtau1I6_As` do Drive. As imagens da galeria
   (`#traco`) continuam sendo peças do portfólio pessoal do Joel, puxadas da
   pasta `CROQUIS/PNG` — troque por artes oficiais do pack quando ele fechar.
5. **Domínio no `<head>`** — `canonical`, `og:url` e `og:image` estão
   apontando para `https://croquidemodapro.com.br/`, um domínio placeholder
   que ainda não existe. Troque pelas URLs reais assim que vocês registrarem
   o domínio e definirem onde o site vai ficar publicado.
6. **Seção "Trusted By"** (`#confianca`) — os avatares de Ludmilla, KATSEYE e
   ssjheni são só as iniciais (L/K/S) coloridas, não as fotos reais deles.
   Preferi não puxar as fotos de perfil de terceiros sem autorização deles
   pra usar num site comercial; se quiserem trocar por fotos/logos reais,
   é só substituir o conteúdo de `.trust-avatar` em cada card.
7. **Vídeos do Instagram** (`#videos`) — carrossel automático (troca a cada
   5s, clique num card lateral pra trazê-lo pra frente) com 3 posts reais
   do Joel usando o pack (`DQ4XvT-jpb1`, `DYZqfMhjV5a`, `DUvudSEDnxR`). Se
   quiserem trocar os posts, me mandem os links de `instagram.com/p/...` ou
   `/reel/...`.
   - **Cabeçalho/rodapé em dark mode**: o Instagram não oferece um modo
     escuro pro embed, e por ser um iframe de outro domínio não dá pra
     restilizar o header/footer originais dele. A solução foi cortar o
     header/footer BRANCOS do Instagram pra fora da área visível (via JS,
     ajustando `HEADER_H`/`FOOTER_H` no script no fim do `index.html`,
     que mostra só a mídia) e desenhar um cabeçalho/rodapé **nossos**, em
     HTML/CSS, no tema escuro do site: avatar do Joel + "joelcoveero" +
     selo verificado no topo, e ícones de curtir/comentar/compartilhar/
     salvar (sem número de curtidas/comentários) embaixo — tudo decorativo,
     não conectado à API do Instagram de verdade.
   - O corte do `HEADER_H`/`FOOTER_H` é uma estimativa visual calibrada nos
     3 posts atuais. Se trocarem os posts e sobrar uma tarja branca (ou
     cortar demais a imagem), me avisem que reajusto os números.
   - **Limitação**: quando o post embutido é do tipo carrossel (várias fotos,
     ex. `?img_index=1`), o Instagram não deixa esse carrossel interno trocar
     de foto sozinho — só com clique manual nas setinhas. Isso é controlado
     inteiramente pelo iframe do Instagram (outro domínio), não temos como
     automatizar isso pelo nosso lado.
8. **Seção "Tutoriais"** (`#tutoriais`) — os 4 cards (estampas com IA,
   coleções consistentes com IA, como importar/usar, como imprimir) ainda são
   só capa + "em breve"/"mini curso incluso", sem vídeo de verdade (procurem
   o comentário `TODO` no `index.html`). Quando gravarem,
   subam no YouTube (pode ser "não listado") e troquem o `.tut-thumb` de cada
   card pelo iframe de embed do YouTube — é só me mandar os links que eu faço.

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
