# Croqui de Moda PRO — loja do pack de croquis do Joel

Landing page / loja de venda do pack de croquis do Joel Coveero (@joelcoveero).
Site estático simples (HTML puro, sem build, sem backend) — feito para ser
barato de manter (hospedagem gratuita) e fácil de atualizar.

## Estrutura

- `index.html` — página única com todo o conteúdo e estilo (sem dependências externas).
- `assets/` — pasta para colocar as imagens reais (fotos do Joel, croquis, mockups).

## O que falta preencher antes de divulgar

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
4. As imagens de croqui (hero e galeria) são peças do portfólio pessoal do
   Joel puxadas da pasta `CROQUIS/PNG` do Drive — troque por artes oficiais
   do pack assim que ele estiver fechado.
5. **Domínio no `<head>`** — `canonical`, `og:url` e `og:image` estão
   apontando para `https://croquidemodapro.com.br/`, um domínio placeholder
   que ainda não existe. Troque pelas URLs reais assim que vocês registrarem
   o domínio e definirem onde o site vai ficar publicado.
6. **Seção "Trusted By"** (`#confianca`) — os avatares de Ludmilla, KATSEYE e
   ssjheni são só as iniciais (L/K/S) coloridas, não as fotos reais deles.
   Preferi não puxar as fotos de perfil de terceiros sem autorização deles
   pra usar num site comercial; se quiserem trocar por fotos/logos reais,
   é só substituir o conteúdo de `.trust-avatar` em cada card.
7. **Vídeos do Instagram** (`#videos`) — os 3 posts embutidos foram escolhidos
   pelos que têm mais curtidas no portfólio do Joel (81,7 mil / 21,4 mil /
   11,4 mil). Se vocês quiserem posts específicos, me mandem os links de
   `instagram.com/p/...` ou `/reel/...` que eu troco.
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
