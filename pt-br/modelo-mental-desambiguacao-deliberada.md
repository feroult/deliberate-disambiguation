# Do Deliberate Discovery à Desambiguação Deliberada
## Um modelo mental para desenvolvimento de software

---

## Resumo

Desenvolver software é navegar território que ainda não está completamente mapeado. O mecanismo dessa navegação é a tradução: mover intenção de linguagem natural para linguagem formal. Esse processo sempre carregou duas fontes de ambiguidade: a ignorância sobre o mundo (hipóteses não validadas, domínio não compreendido, comportamento de usuários desconhecido) e a imprecisão inerente à linguagem natural, que só se manifesta quando você tenta ser preciso o suficiente para uma máquina executar. O Deliberate Discovery de Dan North nomeou a primeira com clareza. A segunda sempre esteve presente, mas era gerenciada implicitamente pelo programador humano: o agente de formalização que também detectava imprecisão e sabia pausar para resolvê-la. Quando o custo de formalização colapsa, como aconteceu com a inteligência artificial, ambas tornam-se impossíveis de ignorar. Este documento propõe um modelo mental que completa o modelo original: desambiguação deliberada como output de cada ciclo, aprendizado como outcome acumulado, nas duas dimensões. O colapso do custo de formalização amplifica a ambiguidade do mundo, não a resolve. O humano que sabe desambiguar deliberadamente nas duas dimensões não se torna menos necessário nesse contexto: torna-se o fator limitante.

---

## 1. O que você aprendeu no último projeto

Feche os olhos. Pense no último projeto que você terminou. Agora imagine que você pode voltar ao início, apagar todos os artefatos, o código, a documentação, os deploys, mas manter tudo que você aprendeu ao longo do caminho.

O que você faria igual?

O que você faria diferente?

A segunda lista é o conhecimento que o projeto gerou. Não o código entregue, não as features deployadas: o conhecimento que, se você tivesse no início, teria mudado o que você construiu ou como você construiu. Essa lista é a medida real do que este projeto revelou.

A primeira lista é o que você trouxe com você. Padrões que já funcionavam, domínio que já estava mapeado, decisões que já haviam sido testadas. Esse conhecimento faz parte de qualquer execução competente, mas estava disponível antes do projeto começar.

Desenvolvimento de software, no sentido pleno da palavra, é o processo que produz a segunda lista. É navegar território que você ainda não conhecia completamente ao entrar, e sair sabendo mais sobre ele do que quando chegou.

O que torna esse processo difícil de gerenciar é que a segunda lista só fica completamente visível ao final. O que você teria feito diferente raramente é claro enquanto você ainda está fazendo. E quando fica claro, ao fim de um sprint, de um release, de um projeto, o custo de agir sobre ela já mudou. Decisões tomadas, arquitetura comprometida, deploy feito. O retrabalho que ninguém consegue nomear começa antes do código. Começa numa ambiguidade que estava no mundo ou na intenção, e que só ficou visível quando já havia custo.

O que acontece quando você consegue fazer essa lista aparecer mais cedo, com mais deliberação?

---

## 2. A tese fundacional: tradução como processo

Desenvolvimento, como vimos, é navegar território desconhecido. Navegar exige um mecanismo, e no desenvolvimento de software esse mecanismo tem uma forma específica que, uma vez nomeada, torna visível o que está em jogo a cada passo e o que muda quando o custo de percorrê-lo muda.

Existe um espectro entre dois mundos:

```
LINGUAGEM NATURAL                              LINGUAGEM FORMAL
Ambígua, rica, implícita    ◄──────────────►  Precisa, executável, literal

  Conversa → Documento → Decisão → Teste → Código
```

Linguagem natural é o mundo das intenções humanas. É rica porque é ambígua: uma mesma frase pode significar coisas diferentes para pessoas diferentes, e essa polissemia é funcional na comunicação humana. Nós navegamos ambiguidade o tempo todo com contexto, tom, histórico compartilhado e interpretação tácita.

Linguagem formal é o mundo das máquinas. Código não interpreta. Executa. Um sistema não infere o que você quis dizer. Faz exatamente o que foi especificado. A precisão que parece uma limitação da linguagem formal é também a sua razão de existir: é o que permite que software seja verificável, previsível e confiável.

Desenvolver software é mover intenção ao longo desse espectro, da esquerda para a direita. Cada passo nessa direção exige que uma ambiguidade seja resolvida. Você não pode formalizar algo que ainda tem duas interpretações possíveis sem escolher uma. E toda escolha elimina possibilidades. Formalização é, por definição, um processo de redução: de muitos significados possíveis para um único significado preciso.

Esse processo sempre existiu. O que variou, ao longo da história do desenvolvimento de software, foi o custo de cada passo, a velocidade com que os erros de formalização se tornavam visíveis, e as práticas que as comunidades desenvolveram para gerenciar essa tradução. A escolha da lente, enxergar desenvolvimento como tradução, é o que torna visíveis as duas fontes de ambiguidade que esse processo carrega.

---

## 3. O que Dan North nomeou: a primeira dimensão

Em 2011, escrevi para o InfoQ Brasil sobre uma ideia que Dan North acabara de articular, e que me parecia capturar algo que eu via em projetos mas não conseguia nomear com precisão. Quinze anos depois, ao observar o que a era da AI está fazendo com os times de desenvolvimento, percebo que a ideia estava mais certa do que eu imaginava então. E que havia algo nela que ainda faltava completar.

O que North nomeou foi isso: projetos falham não por falta de competência técnica, mas por falta de conhecimento sobre o que estão construindo. A verdadeira restrição não é velocidade de execução.

Era capacidade de aprender.

O Deliberate Discovery parte de uma constatação incômoda: a maior parte do risco em projetos de software vem do que os times *não sabem que não sabem*. Não das incertezas que estão na lista: aquelas podem ser planejadas, mitigadas, atacadas. O risco real vem da ignorância que ainda não foi reconhecida como tal.

Essa ignorância tem estrutura:

```
Não sei o que não sei     →   ignorância de 2ª ordem   (invisível, perigosa)
Sei que não sei X         →   ignorância de 1ª ordem   (visível, atacável)
Sei X                     →   conhecimento
```

O aprendizado acontece em dois movimentos distintos. O primeiro, **tornar a ignorância visível**, é o mais valioso e o mais raramente praticado com intenção: reconhecer que existe algo que você não sabia que não sabia, converter ignorância de segunda ordem em primeira. O segundo, **resolver a ignorância**, é atacar o que agora você sabe que não sabe: conversar com usuários reais, rodar um experimento de negócio, colocar algo em produção, validar uma hipótese com dados.

Essa ignorância, a primeira dimensão da ambiguidade, se distribui por múltiplos eixos em qualquer projeto: hipóteses de negócio não validadas, comportamento real de usuários desconhecido, domínio não completamente compreendido, restrições técnicas não mapeadas, capacidade de entrega do time não testada. Nenhum desses eixos se resolve numa reunião de alinhamento. A maioria só se revela no contato com a realidade.

A prática do Deliberate Discovery era projetar o trabalho para provocar esse primeiro movimento: revelar a ignorância de segunda ordem antes que ela se materializasse como custo. A metáfora é a névoa de guerra: o mapa começa coberto, e só se revela onde suas unidades chegaram. A resposta não é esperar o território se revelar sozinho. É enviar um scout. Uma unidade barata, rápida, cujo propósito não é conquistar território, mas remover névoa. O scout não resolve o problema. Ele revela o que você não sabia que precisava saber para avançar.

Dan North provocava times com uma instância concreta disso: *coloque um hello world em produção antes de qualquer outra coisa*. Não porque entrega valor, mas porque revela tudo que você não sabia que não sabia: o pipeline de deploy, as credenciais de ambiente, os bloqueios de aprovação, os pontos de fricção entre times. Nenhuma dessas coisas está no backlog. Todas aparecem quando você tenta entregar de verdade. O hello world as faz aparecer cedo, com custo baixo.

Outra forma que ele usava era mais direta: imagine que você pode refazer o último projeto com tudo que aprendeu. O que faria diferente? Essa lista, o que você faria diferente, é o que o projeto produziu de mais valioso. Não o código. O conhecimento que mudaria o que você construiria se pudesse começar de novo.

Esse modelo estava certo. E permanece fundacional. Mas havia algo que ele não nomeou completamente.

---

## 4. O que faltava nomear: a segunda dimensão

O Deliberate Discovery focou na ignorância sobre o mundo: coisas que existem na realidade e que você ainda não encontrou. Mas há uma segunda fonte de ambiguidade no processo de desenvolvimento que opera de forma diferente: a imprecisão inerente à linguagem natural, que só se manifesta quando você tenta tornar algo preciso o suficiente para ser executado.

Considere uma situação comum. Toda a equipe está alinhada: "o administrador pode apagar um usuário". Não há ignorância sobre o negócio. Ninguém está em dúvida sobre se isso é a coisa certa a construir. O domínio é conhecido, a permissão faz sentido. E ainda assim, quando você senta para formalizar essa intenção, perguntas emergem que a conversa nunca precisou responder: apagar significa remover permanentemente ou marcar como inativo? O que acontece com o conteúdo que ele criou? Com os pedidos em aberto? Com os registros de auditoria? O usuário é notificado? Pode ser reativado? Por quanto tempo os dados precisam ser retidos?

Essas perguntas não existiam como ignorância sobre o mundo. A frase "o administrador pode apagar um usuário" era perfeitamente compreensível para todos na sala, e o era justamente porque a linguagem natural tolerava múltiplas interpretações simultaneamente, sem que ninguém precisasse escolher entre elas. A ambiguidade estava *embutida na imprecisão da linguagem*, funcional enquanto a conversa durou. Só se tornou problema quando a formalização exigiu escolhas que a conversa nunca fez.

Isso acontece em todo projeto, em todo nível. Em regras de negócio que "todo mundo sabe" mas que nunca foram escritas de forma a resistir a um caso de borda. Em contratos de API onde o comportamento de erro foi descrito em linguagem natural e nunca especificado. Em definições de domínio onde dois times usam a mesma palavra com sentidos ligeiramente diferentes e só descobrem isso quando os sistemas precisam se comunicar.

A diferença entre as duas dimensões é fundamental:

| | Dimensão 1: Ignorância | Dimensão 2: Imprecisão |
|---|---|---|
| **Fonte** | Realidade não encontrada ainda | Linguagem natural tolerando múltiplas interpretações |
| **Revelada por** | Contato com o mundo real | Tentativa de formalização |
| **Resolvida por** | Exploração, experimento, validação | Especificação, escolha explícita, precisão |
| **Metáfora** | Névoa de guerra sobre o território | Instrução que todos entenderam, cada um à sua maneira |

A Dimensão 2 sempre esteve presente. O que a tornava gerenciável, antes, não era apenas a lentidão do processo: era o **programador humano como intermediário**. Quando um humano escrevia o código, ele era simultaneamente o agente de formalização e o detector de ambiguidade: encontrava uma imprecisão na especificação, pausava, perguntava, resolvia. Esse humano estava, inadvertidamente, operando como um filtro contínuo de Dimensão 2 embutido no próprio ato de construir.

A inteligência artificial substituiu esse intermediário por uma máquina que não tem esse mecanismo. A máquina não detecta ambiguidade: escolhe a interpretação mais provável e executa, sem saber se é a correta para o seu domínio. Não pausa para perguntar "o que você quis dizer com isso?". Produz código. A imprecisão que antes encontrava um humano capaz de reconhecê-la e suspender o processo agora encontra uma máquina que a formaliza silenciosamente.

---

## 5. Quando o custo de formalização colapsa

O que as ferramentas de geração de código tornaram visível não é que a máquina pode escrever código. É o que acontece quando o custo de cada ciclo de formalização colapsa para perto de zero. Transformar intenção em código verificável, que antes levava horas ou dias, passa a levar minutos.

Esse colapso expõe as duas dimensões simultaneamente. Para a Dimensão 1, o risco é o mesmo de sempre, só mais rápido: ignorância sobre o domínio, os usuários ou a hipótese de negócio se formaliza em sistema em minutos, não em semanas. Para a Dimensão 2, o risco se aprofunda: o programador humano, que antes detectava imprecisão durante a implementação e pausava para resolver, foi substituído por uma máquina que não reconhece ambiguidade, apenas escolhe uma interpretação e executa. O que antes encontrava um humano capaz de suspender o processo agora encontra uma máquina que o acelera.

**O output inesperado é um scout.**

Mas só quando tratado como tal: não como erro a corrigir, mas como evidência a interpretar. A lógica do scout que a seção anterior descreveu, ação barata cujo propósito é revelar e não conquistar, se estende para as duas dimensões, mas por caminhos distintos.

Para a Dimensão 1, o scout funciona de forma análoga ao hello world: ao tentar formalizar algo, o resultado revela ignorância sobre o mundo que estava oculta. A feature que parecia óbvia, quando implementada, mostra que o domínio funcionava de forma diferente do que o time assumia.

Para a Dimensão 2, o scout é mais sutil: a divergência entre o que você descreveu e o que a máquina entendeu é a imprecisão da linguagem se tornando visível. A máquina escolheu uma das interpretações válidas da sua frase, e ao fazê-lo revelou que havia mais de uma. O output "errado" não é falha. É a ambiguidade semântica que estava tolerada na linguagem natural emergindo como evidência.

```
Scout DD        →  ação barata revela ignorância sobre o mundo (Dimensão 1)
Scout formal    →  formalização barata revela imprecisão da intenção (Dimensão 2)
```

A reação certa ao output inesperado não é ajustar a instrução e tentar de novo. É fazer uma pergunta diagnóstica: *qual dimensão esse gap está revelando?* É ignorância sobre o mundo, e precisa de exploração? Ou é imprecisão na linguagem da intenção, e precisa de especificação? A resposta muda completamente o próximo passo.

---

## 6. Desambiguação Deliberada

O modelo mental da Desambiguação Deliberada herda a premissa central do Deliberate Discovery, que a capacidade de aprender é a verdadeira restrição, e a completa com a segunda dimensão que o processo de tradução sempre carregou.

**Desambiguar não é o mesmo que aprender.**

Desambiguar é mover de múltiplas interpretações possíveis para uma só: uma operação sobre linguagem e intenção. Aprender é atualizar o modelo de mundo. Isso exige realidade. A relação entre as duas operações depende da dimensão.

Para a Dimensão 2, elas quase coincidem: resolver a imprecisão da linguagem produz diretamente o conhecimento que faltava. Quando você decide que "apagar" significa soft delete, você simultaneamente desambiguou e aprendeu algo sobre o domínio.

Para a Dimensão 1, desambiguar é necessário mas não suficiente. Nomear com precisão o que você não sabe sobre os usuários não é aprender sobre os usuários. É o primeiro passo para poder aprender. O aprendizado ainda exige ir ao mundo.

O que é igual nas duas: sem desambiguação suficiente, a formalização codifica o que estava impreciso ou desconhecido. O que o ciclo produz não é aprendizado: é ilusão de progresso.

**Output de cada ciclo: uma desambiguação nomeável.**

O teste de um ciclo bem-feito não é a sensação de progresso. É conseguir completar uma dessas frases:

*"Descobrimos que os usuários não fazem X como assumíamos"*

Dimensão 1: foi ao mundo, atualizou o modelo de mundo.

*"Decidimos que 'busca' significa correspondência parcial, sem distinção de maiúsculas"*

Dimensão 2: precisou a intenção, eliminou a interpretação aberta.

Se ao fim de um ciclo você não consegue completar nenhuma das duas, o ciclo produziu artefatos. Não aprendizado.

O código é o artefato. O que permanece é o que ele materializou: a escolha feita, a ignorância revelada e endereçada.

**Outcome acumulado: aprendizado.**

O acúmulo de ciclos bem-feitos vive no software que roda. Cada comportamento do sistema é uma desambiguação que completou o ciclo, da intenção imprecisa ao artefato executável. Cada decisão de produto que mudou porque a realidade contrariou a hipótese está expressa no que o sistema faz, não no que alguém lembra. O conhecimento que ficou só nas cabeças é o que ainda não terminou de virar formal. Desambiguação incompleta não acumula.

O que acumula não é uma soma de decisões: é um sistema coerente, onde cada nova formalização precisa ser consistente com tudo que veio antes. Essa coerência é, ao mesmo tempo, evidência de que a desambiguação foi real e condição para o que ainda pode ser aprendido.

**A relação causal:**

```
Desambiguação bem-feita    →   aprendizado real
Desambiguação mal-feita    →   ilusão de progresso
Sem desambiguação          →   aprendizado impossível
```

**O movimento natural de quem pensa assim:**

```
Intenção em linguagem natural
           ↓
  ┌─ Ambiguidade identificada? ──────────────────────┐
  │                                                   │
  │  SIM → qual dimensão?                             │  NÃO
  │  ├─ Dim 1: ignorância sobre o mundo               │  → formalizar como scout
  │  │   → explorar, validar com realidade            │    (para revelar a ambiguidade)
  │  └─ Dim 2: imprecisão da linguagem                │
  │      → especificar, tornar preciso                │
  └───────────────────────┬───────────────────────────┘
                          ↓
                     Formalizar
                          ↓
              Output divergiu do esperado?
              ├─ NÃO → registrar e avançar
              └─ SIM → diagnóstico: qual dimensão esse gap revelou?
                        ├─ Dim 1 → explorar
                        └─ Dim 2 → especificar
                        → retornar ao início com a dimensão identificada
                          ↓
               Registrar o conhecimento gerado
                          ↓
                  Próxima ambiguidade
```

Esse movimento tem dois pontos de entrada, e isso reflete a realidade do processo. No caminho ideal, você identifica a ambiguidade e sua dimensão *antes* de formalizar, e age de forma diferente dependendo do tipo. No caminho mais comum, você não sabe ao certo qual ambiguidade está presente, usa a formalização como scout deliberado, e o output divergente é o que revela a dimensão. Em ambos os casos, o ciclo termina no mesmo lugar: conhecimento registrado, ambiguidade reduzida.

A distinção importa porque muda o custo: quando você formaliza como scout intencionalmente, a divergência é informação. Quando você formaliza como executor sem ter identificado a ambiguidade, a divergência é retrabalho. A diferença entre os dois não está no output. Está na intenção de quem formula a instrução.

Três implicações desse modelo mental:

**Primeiro: a dimensão determina o próximo passo.** Ambiguidade de Dimensão 1 exige ir ao mundo buscar a resposta. Não se resolve especificando melhor. Ambiguidade de Dimensão 2 exige precisão na descrição da intenção. Não se resolve experimentando com usuários. Você nem sempre sabe qual dimensão está presente antes de tentar, e tudo bem: é para isso que o caminho do scout existe. O que não é aceitável é confundir as duas depois de identificadas: times que tentam especificar melhor o que ainda não sabem, ou que saem para explorar o que precisava apenas de maior precisão, perdem ciclos sem aprender.

**Segundo: o output inesperado é diagnóstico, não falha.** A pergunta não é "como ajusto a instrução?": é "qual dimensão essa divergência está revelando?" A resposta muda o próximo passo: Dimensão 1 pede exploração, Dimensão 2 pede especificação.

**Terceiro: o registro é parte do ciclo, não burocracia posterior.** A desambiguação que não é registrada, seja a descoberta sobre o mundo, seja a escolha de interpretação, terá que ser refeita. Times que registram acumulam; times que não registram recomeçam sempre.

---

## 7. O que muda na prática

**Muda a pergunta de diagnóstico.** Antes: "o que entregamos?" Agora: "o que desambiguamos, e em qual dimensão?" Um ciclo que não produziu nenhuma redução de ambiguidade identificável produziu artefatos mas não aprendizado. Isso não é sempre um erro. Execução pura tem valor. Mas é informação sobre o que está sendo otimizado.

**Muda o papel da ferramenta de formalização no fluxo.** Ela tem dois usos legítimos e distintos: como **scout** (formalizar para revelar ambiguidade que ainda não foi identificada) e como **executor** (formalizar uma intenção já suficientemente clara). O erro é usar como executor quando a ambiguidade ainda não foi tratada. A instrução que você passa, a um programador, a uma ferramenta, a um agente, não é o início do processo de pensar. É o registro de uma intenção que já passou por desambiguação suficiente.

**Muda o que se espera de um bom engenheiro.** O skill mais valioso não é operar bem a ferramenta de formalização: é reconhecer qual tipo de ambiguidade está presente antes de executar, e saber o que fazer com cada uma. Saber quando ir ao mundo (Dimensão 1) e quando precisar a intenção (Dimensão 2). Engenheiros que desenvolvem essa capacidade se tornam multiplicadores: não porque produzem mais código, mas porque o código que produzem materializa intenções genuinamente desambiguadas.

**Muda a leitura do retrabalho.** Retrabalho passa a ser sinal diagnóstico com informação de dimensão: *"construímos a coisa certa da forma errada"* (Dimensão 2 mal resolvida) é diferente de *"construímos a coisa errada muito bem"* (Dimensão 1 ignorada). A causa muda completamente o remédio.

Uma sprint acaba com um card claro: "adicionar busca de produtos ao catálogo." O time está alinhado. Antes de implementar, um scout deliberado: a mesma intenção, formulada de três formas distintas para a ferramenta:

*"Implemente a busca de produtos no catálogo."*
*"Permita que o usuário encontre produtos pelo nome."*
*"Filtre a lista de produtos conforme o usuário digita."*

Três outputs emergem. O primeiro implementa busca full-text contra nome, descrição e categoria, com ranking por relevância. O segundo implementa correspondência parcial por nome, case-insensitive. O terceiro implementa filtragem client-side nas colunas visíveis da tabela.

Nenhum está errado. Todos são formalizações válidas de "busca de produtos". A divergência entre eles não é falha da ferramenta: é a imprecisão da palavra "busca" tornando-se visível. O que conta como correspondência? Em quais campos? O sistema consulta ou o cliente filtra? Como os resultados são ordenados? A reunião nunca precisou responder essas perguntas. A linguagem natural tolerava todas as interpretações ao mesmo tempo.

O scout tornou visível o que "busca" significa neste contexto antes de qualquer implementação ser comprometida. O próximo passo não é escolher o melhor output: é responder as perguntas que a divergência revelou. Essa resposta é a desambiguação. A implementação que vem depois é o scout virando executor. A instrução que você passa a ele já passou por desambiguação suficiente.

---

## 8. Conclusão

O processo de tradução que o desenvolvimento de software sempre foi carregou, desde o início, duas fontes de ambiguidade. A primeira foi nomeada pelo Deliberate Discovery: a ignorância sobre o mundo que precisa ser descoberta antes de virar custo. A segunda era gerenciada implicitamente pelo programador humano: filtro embutido no próprio ato de construir.

A inteligência artificial tornou esse filtro visível ao removê-lo. A segunda dimensão deixou de ter quem a detectasse. Quando formalizar passou a custar minutos, deixou de ser tolerável.

A Desambiguação Deliberada não substitui o modelo anterior: o completa. Nomeia as duas fontes de ambiguidade que o processo de tradução natural→formal carrega, propõe que a desambiguação deliberada de ambas é o verdadeiro output de cada ciclo, e que o aprendizado acumulado dessas resoluções é o ativo mais valioso que um time de software produz.

O colapso do custo de formalização não resolve a ambiguidade do mundo: ele a amplifica de forma combinatória. Cada sistema construído adiciona comportamento ao ambiente em que outros sistemas precisam operar. Cada nova composição gera estados que ninguém previu. Navegar esse ambiente exige capacidade de resposta proporcional à sua variedade. A primeira dimensão cresce: há mais domínio desconhecido emergindo de interações que não existiam antes. A segunda se multiplica: cada camada de delegação entre intenção e execução carrega imprecisão acumulada. AI reduz variedade: escolhe a interpretação mais provável e executa. O humano que sabe desambiguar deliberadamente é o que mantém capacidade de resposta proporcional a esse ambiente. Torna-se o fator limitante.

> Desenvolver software é navegar território desconhecido. O mecanismo dessa navegação é a tradução iterativa de intenção humana de linguagem natural para linguagem formal, removendo ambiguidade a cada passo: tanto a ignorância sobre o mundo que ainda não foi encontrado, quanto a imprecisão da linguagem que só se revela quando você tenta ser preciso o suficiente para executar.
>
> O output de cada ciclo é desambiguação.  
> O outcome acumulado é aprendizado.  
> AI não mudou o que o processo é. Tornou impossível ignorar o que ele sempre exigiu.

---

*Este documento é uma fonte para derivação de conteúdo (posts, palestras, artigos) sobre desenvolvimento de software. As ideias aqui desenvolvidas têm raízes no conceito de Deliberate Discovery (Dan North) e estendem esse modelo com a segunda dimensão da ambiguidade que o processo de tradução sempre carregou.*
