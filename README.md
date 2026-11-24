# 99Food — redesign da experiência de delivery

Aplicação web responsiva para um projeto acadêmico de Interface Humano-Computador (IHC). O escopo é exclusivamente a experiência de quem pede comida: descobrir restaurantes, escolher itens, revisar a sacola, finalizar o pedido, acompanhar a entrega e conversar com o estabelecimento.

> **Importante:** este é um protótipo acadêmico independente, não um aplicativo oficial da 99. Restaurantes, preços, endereço, perfil, pagamentos, pedidos, status e mensagens são dados demonstrativos. Não há integração com a 99, restaurantes, entregadores, mapas, gateways de pagamento ou sistemas externos. Nenhuma compra, cobrança ou solicitação real é feita. Essa informação deve ser apresentada na explicação do trabalho, não como parte da interface de demonstração.

## Abrir e executar

Não há instalação, build ou dependências. Basta abrir `index.html` em um navegador moderno.

Para testar em um servidor local, na pasta do projeto execute:

```bash
python -m http.server 8000
```

Depois abra `http://localhost:8000`.

O projeto também está preparado para publicação no GitHub Pages: os arquivos do site ficam na raiz do repositório, há um arquivo `.nojekyll` e não é necessário processo de compilação.

## Fluxo funcional disponível

1. **Início:** pesquisa, categorias, restaurantes em destaque e pratos populares.
2. **Explorar:** pesquisa por nome de restaurante, categoria e também por pratos do cardápio; filtros e ordenação.
3. **Restaurante:** informações, avaliação, tempo de entrega, taxa, cardápio e inclusão de itens.
4. **Sacola:** quantidades, remoção de itens, observação para a loja, subtotal, entrega e total.
5. **Checkout:** endereço, complemento, referência, contato e seleção de forma de pagamento.
6. **Pedido:** confirmação, acompanhamento por etapas e atualização manual do status para fins de demonstração.
7. **Comprovante:** folha de pedido com código, data, restaurante, itens, valores, pagamento, endereço e observações.
8. **Chat com a loja:** conversa vinculada ao pedido, mensagens do usuário, respostas automáticas e perguntas rápidas.
9. **Ajuda da plataforma:** canal separado do chat do restaurante.
10. **Meus pedidos e Perfil:** histórico, dados da conta, endereços, pagamentos e suporte.

O carrinho, o pedido atual e as mensagens ficam no `localStorage` do navegador. Para recomeçar a demonstração, limpe os dados do site no navegador ou remova a chave `99food-redesign-state` do armazenamento local.

## Problema de IHC e objetivo

A motivação inicial relatada pelo integrante foi a dificuldade para localizar o chat de conversa com a loja durante o uso do 99Food. O projeto parte dessa experiência individual como um indício inicial, não como prova de que todos os usuários enfrentam o mesmo problema.

**Objetivo geral:** melhorar a encontrabilidade das funções essenciais do delivery e tornar o fluxo de compra e acompanhamento mais claro, previsível e acessível.

**Objetivos específicos:**

- reduzir o esforço para localizar restaurantes e itens;
- manter a sacola e o valor total visíveis antes da confirmação;
- organizar o checkout em etapas compreensíveis;
- apresentar o pedido como uma folha de comprovante fácil de consultar;
- deixar o canal de conversa com a loja visível no contexto do pedido;
- distinguir claramente contato com o restaurante e suporte da plataforma;
- tornar os rótulos, ícones, estados e controles mais consistentes.

## Decisões de redesign

| Necessidade / ponto de atenção | Decisão aplicada |
|---|---|
| A pessoa precisa entender para onde ir | Navegação principal com ícones convencionais e rótulos textuais: Início, Explorar, Pedidos e Perfil |
| O carrinho precisa ser fácil de encontrar | Ação Sacola persistente no cabeçalho e contador de itens |
| A pessoa precisa avaliar o pedido antes de pagar | Sacola com quantidades, observação, subtotal, taxa e total |
| O checkout deve evitar surpresas | Endereço, contato e pagamento organizados; total repetido antes de confirmar |
| O usuário precisa entender o estado do pedido | Linha do tempo e indicador de progresso com rótulos por etapa |
| O comprovante precisa parecer um documento de pedido | Folha de pedido com código, data, restaurante, itens, valores, pagamento e endereço |
| A conversa com a loja era difícil de localizar | Botão “Conversar com a loja” na tela do pedido |
| Loja e plataforma não são o mesmo canal | “Conversar com a loja” e “Ajuda da 99” em ações distintas, com ícones e descrições |
| O perfil precisa ser reconhecível | Ícone de pessoa, rótulo “Perfil” e título “Meu perfil” |
| A busca deve ser útil | Pesquisa por restaurante, categoria, pratos e descrições do cardápio |

## Heurísticas de Nielsen consideradas

1. **Visibilidade do estado do sistema:** confirmação do pedido, etapa atual, progresso e histórico.
2. **Correspondência entre sistema e mundo real:** termos familiares como restaurante, sacola, pedido, preparo, entrega e comprovante.
3. **Controle e liberdade do usuário:** alterar quantidades, remover itens e voltar entre sacola e checkout.
4. **Consistência e padrões:** ícones reconhecíveis acompanhados por texto; navegação e ações principais em posições previsíveis.
5. **Prevenção de erros:** revisão do carrinho, validação de campos essenciais e total antes de confirmar.
6. **Reconhecimento em vez de memorização:** acesso ao chat no próprio pedido e rótulos explícitos nas áreas principais.
7. **Flexibilidade e eficiência de uso:** busca, categorias, filtros, ordenação e atalhos para itens populares.
8. **Design estético e minimalista:** hierarquia visual, espaçamento e redução de conteúdo explicativo dentro do fluxo de compra.
9. **Ajudar a reconhecer e recuperar erros:** mensagens de validação e estados vazios com uma próxima ação clara.
10. **Ajuda e documentação:** suporte da plataforma acessível e separado do contato com o restaurante.

## Acessibilidade considerada

- contraste de texto e foco de teclado visível;
- ícones acompanhados por rótulos, evitando depender apenas de símbolos;
- botões com nomes acessíveis (`aria-label`) quando o texto visual não é suficiente;
- campos com rótulos associados;
- mensagens de status anunciadas por região `aria-live`;
- estados comunicados por texto além de cor;
- layout responsivo para desktop e celular;
- respeito à preferência de movimento reduzido (`prefers-reduced-motion`).

Essas decisões são cuidados de projeto, não uma certificação formal de conformidade WCAG. Uma avaliação com tecnologia assistiva ainda é recomendada.

## Persona provisória

**Alex, 27 anos** — pessoa que trabalha em horário comercial e costuma pedir refeições pelo celular. Tem pouco tempo para procurar opções, quer saber quanto vai pagar antes de confirmar e espera acompanhar o pedido sem precisar navegar por vários menus. Se tiver uma dúvida sobre ingredientes, preparo ou observação, espera encontrar a conversa com o restaurante na tela do pedido.

- **Objetivos:** pedir com rapidez, entender o valor final e acompanhar o pedido.
- **Dores:** caminhos pouco evidentes, excesso de etapas, incerteza sobre o status e confusão entre loja e suporte.
- **Necessidades:** busca clara, sacola persistente, comprovante legível e contato com a loja fácil de encontrar.

A persona é uma hipótese inicial de projeto. Deve ser revisada conforme entrevistas e observações dos participantes.

## Teste de usabilidade — realizar com pessoas reais

O roteiro abaixo está pronto para ser aplicado a pelo menos duas pessoas que não façam parte do grupo. Não foram incluídos resultados inventados.

### Tarefas

1. Encontre um restaurante que venda hambúrguer e abra seu cardápio.
2. Adicione um prato e uma bebida à sacola; altere a quantidade de um dos itens.
3. Finalize o pedido escolhendo uma forma de pagamento.
4. No acompanhamento, encontre o comprovante e diga qual é o valor total.
5. Encontre a conversa com a loja e envie uma pergunta sobre a previsão.
6. Explique a diferença entre conversar com a loja e usar a Ajuda da 99.
7. Encontre a área Perfil e localize seus endereços.

### O que registrar

- participante (P1, P2; sem nome completo);
- tarefa concluída ou não concluída;
- tempo aproximado;
- hesitações, erros e caminhos inesperados;
- pedidos de ajuda;
- comentários espontâneos;
- avaliação de facilidade de 1 a 5.

### Folha de registro

| Tarefa | P1 | P2 | Observações |
|---|---|---|---|
| Encontrar restaurante e cardápio | A preencher | A preencher | A preencher |
| Adicionar e ajustar itens na sacola | A preencher | A preencher | A preencher |
| Finalizar pedido | A preencher | A preencher | A preencher |
| Encontrar comprovante e valor total | A preencher | A preencher | A preencher |
| Localizar e usar o chat | A preencher | A preencher | A preencher |
| Diferenciar loja e suporte | A preencher | A preencher | A preencher |
| Encontrar Perfil e endereços | A preencher | A preencher | A preencher |

Depois dos testes, priorize uma dificuldade observada, implemente uma mudança e registre a comparação antes/depois. A melhoria final deve ser baseada no que os participantes realmente fizeram e relataram.

## Organização dos arquivos

```text
99food-redesign-funcional/
├── index.html              # Estrutura das telas
├── styles.css              # Estilos e responsividade
├── app.js                  # Dados, navegação e interações
├── manifest.webmanifest    # Metadados para instalação
├── assets/
│   └── favicon.svg         # Ícone de fallback do projeto
├── README.md               # Contexto, decisões de IHC e roteiro de teste
├── LICENSE
├── .gitignore
└── .nojekyll
```

## Ícone da aba do navegador

A aba usa o ícone de hambúrguer da coleção Font Awesome Free Solid, servido pelo jsDelivr. Foi escolhido por ser um símbolo universalmente associado a comida e delivery. Há um favicon SVG local como alternativa caso o CDN não carregue. Referência: [Font Awesome — Burger](https://fontawesome.com/icons/burger). Licença dos ícones Font Awesome Free: CC BY 4.0; consulte os termos da biblioteca antes de redistribuir o ícone isoladamente.

## Publicação no GitHub Pages

1. Crie um repositório público chamado `99food-delivery-redesign`.
2. Envie todos os arquivos desta pasta para a raiz do repositório.
3. No GitHub, abra **Settings → Pages**.
4. Em **Build and deployment**, selecione **Deploy from a branch**.
5. Escolha a branch `main` e a pasta `/ (root)`; salve.
6. Aguarde a publicação e use o endereço informado em Settings → Pages para convidar os participantes.

Como o site é estático, não precisa de servidor de aplicação nem banco de dados. Cada participante mantém seu próprio estado local no navegador.

### Publicar automaticamente com GitHub Actions

O repositório inclui `.github/workflows/pages.yml`. Depois de enviar a branch `main`, abra **Settings → Pages**, escolha **GitHub Actions** como fonte de publicação e aguarde a execução do workflow na aba **Actions**. O endereço público ficará disponível em **Settings → Pages** e no resumo do workflow concluído.


## Caixa de entrada de Mensagens

A navegação inferior e o Perfil oferecem acesso direto à caixa de entrada. A tela reúne atalhos de conversa com a loja, acompanhamento do pedido e Ajuda da 99, com filtros por Todas, Lojas, Pedidos e Ajuda. Os canais continuam separados e reutilizam as telas e os dados demonstrativos já existentes no protótipo.
