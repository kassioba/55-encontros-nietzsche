# site-gen-2026

Site do **55º Encontros Nietzsche — "Nietzsche e seus duplos: destruição e criação"**,
edição comemorativa dos **30 anos do GEN** (21/09 a 02/10/2026), realizada em
São Paulo, Rio de Janeiro, Brasília, Recife e Toledo.

Baseado na arquitetura do `congreso-rien-2022` (página única, roteamento por hash,
conteúdo em estruturas de dados JS), com identidade visual, paleta e componentes próprios.

## Como rodar

```bash
python3 -m http.server 4173 --directory .
```

Depois abra <http://localhost:4173>. Não há build nem dependências — é HTML/CSS/JS estático,
publicável em qualquer hospedagem (GitHub Pages, Netlify, servidor da universidade).

## Estrutura

```
index.html                  todo o site (CSS + dados + renderização)
assets/
  banners/                  cartazes das cidades e da programação
    cartaz-<cidade>.jpg       versão web
    cartaz-<cidade>-alta.jpg  versão para ampliar/baixar
    prog-<cidade>-<data>.jpg  cartazes de programação (+ -alta)
  livros/                   capas dos lançamentos e dos Cadernos Nietzsche
  brand/                    marca "30 anos", selo GEN, assinatura, andarilho, QR
docs/
  SITE-conteudo-original.docx   documento de origem dos textos
```

## Páginas

| Rota | Conteúdo |
|---|---|
| `#/` | Hero, roteiro do andarilho, texto dos Encontros, cards das 5 cidades |
| `#/o-gen` | Texto "Sobre o GEN", núcleos, texto dos Encontros Nietzsche |
| `#/programacao` | Índice das cidades |
| `#/programacao/<cidade>` | Cartaz, dados do local, cartazes de programação e **programação completa transcrita** |
| `#/lancamentos` | Livros, sinopses, Cadernos Nietzsche 47.2 e demais títulos |
| `#/cartazes` | Galeria de todas as artes, com download em alta |
| `#/contato` | Links oficiais, inscrições e locais de realização |

Cidades: `sao-paulo`, `rio-de-janeiro`, `brasilia`, `recife`, `toledo`.

## Onde editar

Tudo dentro de `index.html`, na seção `dados do evento`:

- `EVENTO` — título, tema, período e links oficiais
- `SOBRE` — textos institucionais e lista de núcleos
- `SP`, `RJ`, `BSB`, `REC`, `TOL` — uma constante por cidade (local, datas, cartazes, dias e mesas)
- `LIVROS` / `LIVROS_OUTROS` — lançamentos

Cada dia tem `sects` (blocos). Um bloco aceita:
`t` (horário), `h` (título), `m` (mediação/observação), `names` (nomes soltos),
`items` (lista de falas: `t`, `w` = quem, `a` = instituição, `ti` = título) e
`plain` / `brk` para intervalos e avisos.

## Recursos

- Tema claro/escuro (botão no topo; segue o sistema por padrão)
- Lightbox nos cartazes e capas, carregando a versão em alta
- Folha de estilo de impressão: a programação imprime limpa, sem cabeçalho/rodapé
- Layout responsivo (grades colapsam em telas estreitas)

## Pendências

- **Contato:** não havia e-mail ou telefone no material recebido. A página `#/contato`
  traz apenas links oficiais — preencher quando a informação chegar.
- **Inscrições:** só existe QR code para ouvintes em São Paulo. As demais sedes
  remetem ao núcleo local.
- **Lançamentos sem imagem:** os títulos de Vânia Dutra de Azeredo e Célia Machado
  Benvenho estão listados sem capa nem sinopse, conforme indicado no documento de origem.
- **Recife, 29/09:** o cartaz traz "19h55", "19h35" e "19h55" na Mesa 4. Foi transcrito
  como 19h15 / 19h35 / 19h55 (sequência coerente com as Questões às 20h15) —
  confirmar com a organização.
- **Links de editora:** faltam os de *Lições sobre os pré-platônicos* (Vozes) e
  *Filosofia como retórica* (CRV). Os links recebidos apontavam para a caixa
  Zaratustra da Autêntica, que não é dessas editoras, então o botão não foi
  aplicado nesses dois livros.
- **Rio, 25/09:** "Cartografias nietzschianas em Butler (GEN/UNIRIO)" foi transcrito
  do documento de alterações tal como veio — confirmar se é o nome de quem apresenta
  ou o título do trabalho.

## Histórico de alterações

**22/09/2026** — aplicadas as correções do documento `Alterações no site.docx`:
título da conferência de Vânia Dutra de Azeredo em São Paulo (21/09); salas distintas
por dia no Rio (Tércio Pacitti em 24/09, Sala 401 do CLA em 25/09); bloco das 9h30 do
dia 25/09 passou de "Conferências" para "Comunicações", com nova apresentação e link
da sala online. Na página de Lançamentos: botão "Página na editora" e reordenação
com o livro de Scarlett Marton em primeiro.
