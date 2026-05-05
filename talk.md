# Desambiguação Deliberada
### Uma palestra sobre o que o desenvolvimento de software sempre foi, e ficou impossível ignorar

---

## Estrutura

| Bloco | Conteúdo | Tempo |
|---|---|---|
| 1 | Abertura: o que você aprendeu? | 5 min |
| 2 | O mecanismo: tradução como processo | 7 min |
| 3 | Dan North e a primeira dimensão | 7 min |
| 4 | A segunda dimensão | 7 min |
| 5 | O colapso do custo de formalização | 5 min |
| **6** | **[DEMO] Convergência em ação** | **10 min** |
| 7 | O que muda na prática | 5 min |
| 8 | Fechamento | 4 min |
| | **Total** | **~50 min** |

---

## 1. Abertura

Feche os olhos. Pense no último projeto que você terminou.

Agora imagine que você pode voltar ao início. Apaga o código, a documentação, os deploys. Mas mantém tudo que você aprendeu ao longo do caminho.

Duas perguntas:

O que você faria igual?

O que você faria diferente?

A segunda lista é o que o projeto realmente produziu. Não o código entregue. Não as features deployadas. O conhecimento que, se você tivesse no início, teria mudado o que você construiu ou como você construiu.

Essa lista é o aprendizado real. E o processo que a produz é o que vou discutir aqui.

---

## 2. O mecanismo

Desenvolvimento de software é navegar território que você ainda não conhecia ao entrar. O que nem sempre fica claro é o mecanismo dessa navegação.

Existe um espectro entre dois mundos:

```
LINGUAGEM NATURAL ──────────────────────► LINGUAGEM FORMAL
Ambígua, rica, implícita                  Precisa, executável, literal
```

De um lado, o mundo das intenções. Linguagem natural é rica justamente porque tolera ambiguidade. Uma mesma frase pode significar coisas diferentes para pessoas diferentes, e isso funciona na conversa humana: usamos contexto, tom, histórico compartilhado para nos entender.

Do outro, o mundo das máquinas. Código não interpreta. Executa. Um sistema não infere o que você quis dizer. Faz exatamente o que foi especificado. O que parece uma limitação é também a razão de o software ser verificável, previsível e confiável.

Desenvolver software é mover intenção ao longo desse espectro. Cada passo exige que uma ambiguidade seja resolvida. Você não formaliza algo com duas interpretações possíveis sem escolher uma. E toda escolha elimina possibilidades.

Formalização é redução: de muitos significados possíveis para um único significado preciso.

Esse processo sempre existiu. O que variou foi o custo de cada passo. Isso vai importar daqui a pouco.

---

## 3. Dan North e a primeira dimensão

Em 2011, escrevi para o InfoQ sobre uma ideia que Dan North tinha acabado de articular. Quinze anos depois, ao ver o que a IA está fazendo com times de desenvolvimento, percebo que a ideia estava mais certa do que eu imaginava.

O que North nomeou: projetos falham não por falta de competência técnica, mas por falta de conhecimento sobre o que estão construindo. A verdadeira restrição não era velocidade de execução.

Era capacidade de aprender.

O ponto central do Deliberate Discovery é incômodo: a maior parte do risco em projetos de software vem do que os times não sabem que não sabem. Não das incertezas que estão na lista. Aquelas podem ser planejadas, atacadas. O risco real vem da ignorância que ainda não foi reconhecida como tal.

```
Não sei o que não sei   →   ignorância de 2ª ordem   (invisível, perigosa)
Sei que não sei X       →   ignorância de 1ª ordem   (visível, atacável)
Sei X                   →   conhecimento
```

O aprendizado acontece em dois movimentos. Primeiro: tornar a ignorância visível. Esse é o mais valioso e o menos praticado com intenção. Segundo: resolver o que agora você sabe que não sabe. Conversar com usuários reais, validar uma hipótese com dados, colocar algo em produção.

A prática do Deliberate Discovery era projetar o trabalho para provocar o primeiro movimento.

Dan North usava um exemplo concreto: coloque um hello world em produção antes de qualquer outra coisa. Não porque entrega valor. Porque revela tudo que você não sabia que não sabia: o pipeline de deploy, as credenciais de ambiente, os bloqueios de aprovação, os pontos de fricção entre times. Nada disso está no backlog. Tudo aparece quando você tenta entregar de verdade.

A metáfora é a névoa de guerra. O mapa começa coberto. A resposta não é esperar o território se revelar sozinho. É enviar um scout: ação barata cujo propósito não é conquistar território, mas remover névoa.

Esse modelo estava certo. Permanece fundacional. Mas havia algo que ele não nomeou completamente.

---

## 4. A segunda dimensão

O Deliberate Discovery focou na ignorância sobre o mundo: coisas que existem na realidade e que você ainda não encontrou.

Há uma segunda fonte de ambiguidade no processo de desenvolvimento. Uma que opera de forma completamente diferente.

Considere uma situação comum. A equipe toda está alinhada: "o administrador pode apagar um usuário". Ninguém está em dúvida sobre se isso é a coisa certa a construir. O domínio é conhecido, a permissão faz sentido.

Quando você senta para formalizar, perguntas emergem que a conversa nunca precisou responder.

Apagar significa remover permanentemente ou marcar como inativo? O que acontece com o conteúdo que ele criou? Com os pedidos em aberto? Com os registros de auditoria? O usuário é notificado? Pode ser reativado?

Essas perguntas não existiam como ignorância sobre o mundo. A frase "o administrador pode apagar um usuário" era perfeitamente compreensível para todos na sala. Era compreensível justamente porque a linguagem natural tolerava múltiplas interpretações simultaneamente, sem que ninguém precisasse escolher entre elas.

A ambiguidade estava embutida na imprecisão da linguagem. Funcional enquanto a conversa durou. Só se tornou problema quando a formalização exigiu escolhas que a conversa nunca fez.

| | Dimensão 1 | Dimensão 2 |
|---|---|---|
| Fonte | Realidade não encontrada ainda | Linguagem tolerando múltiplas interpretações |
| Revelada por | Contato com o mundo real | Tentativa de formalização |
| Resolvida por | Exploração, experimento, validação | Especificação, escolha explícita |
| Metáfora | Névoa de guerra | Instrução que todos entenderam, cada um à sua maneira |

A Dimensão 2 sempre esteve presente. O que a tornava gerenciável antes era o programador humano como intermediário. Quando escrevia o código, era simultaneamente o agente de formalização e o detector de ambiguidade: encontrava uma imprecisão na especificação, pausava, perguntava, resolvia.

Esse humano operava como filtro de Dimensão 2 embutido no próprio ato de construir.

A IA substituiu esse intermediário por uma máquina que não tem esse mecanismo. A máquina não detecta ambiguidade: escolhe a interpretação mais provável e executa, sem saber se é a correta para o seu domínio. Não pausa para perguntar "o que você quis dizer com isso?". Produz código. A imprecisão que antes encontrava alguém capaz de suspender o processo agora encontra uma máquina que o acelera.

---

## 5. O colapso do custo de formalização

O que as ferramentas de geração de código tornaram visível não é que a máquina pode escrever código. É o que acontece quando o custo de cada ciclo de formalização colapsa para perto de zero.

Transformar intenção em código verificável, que antes levava horas ou dias, passa a levar minutos.

Para a Dimensão 1, o risco é o mesmo de sempre, só mais rápido: ignorância sobre o domínio ou a hipótese de negócio se formaliza em sistema em minutos, não em semanas.

Para a Dimensão 2, o risco se aprofunda. O filtro humano foi removido. A imprecisão que antes encontrava alguém que pausava para resolver agora encontra uma máquina que acelera.

O output inesperado, porém, é um scout. Mas só quando tratado como tal: não como erro a corrigir, mas como evidência a interpretar.

A pergunta certa não é "como ajusto a instrução?". É: qual dimensão esse gap está revelando?

```
Scout DD       →   ação barata revela ignorância sobre o mundo (Dim 1)
Scout formal   →   formalização barata revela imprecisão da intenção (Dim 2)
```

---

## [DEMO] Convergência em ação

> **Nota para o apresentador:** Demo ao vivo de 10 minutos. O objetivo é mostrar o conceito de desambiguação deliberada funcionando na prática, usando um documento real como exemplo. A convergência é iterativa: cada passagem parte de um texto melhor que o anterior, e cada melhoria é uma desambiguação identificável.

### Contextualização (1 min)

Diga ao público:

> "Acabei de descrever como formalização revela ambiguidade. Vou mostrar isso acontecendo em tempo real. O material que vou usar como fonte é um documento técnico sobre esse mesmo conceito. A tarefa: transformá-lo em conteúdo mais refinado. Cada passagem revela ambiguidade que estava embutida no texto. Cada resolução é uma desambiguação deliberada."

### Passo 1: mostre os arquivos (1 min)

Abra o terminal. Mostre o arquivo-fonte e o arquivo de output lado a lado.

Aponte: o documento-fonte está correto, mas ainda carrega a linguagem de quem está pensando enquanto escreve. Muita coisa implícita, transições frouxas, argumentos declarados mas não desenvolvidos.

### Passo 2: rode o primeiro passo de convergência (3 min)

Execute a passagem de transformação. O modelo lê o documento e produz uma versão mais precisa.

Enquanto roda, explique o que está acontecendo:

> "Cada passo resolve ambiguidades que o passo anterior não tocou. Não é reescrita. É formalização iterativa."

### Passo 3: mostre o diff (3 min)

Quando terminar, abra o diff. Aponte especificamente:

- O que mudou na linguagem (registro, precisão, voz ativa)
- O que foi elaborado (argumento declarado mas não desenvolvido no original)
- O que foi removido (imprecisão funcional que não resistia à formalização)

Faça a pergunta diagnóstica em voz alta:

> "Essa mudança resolveu uma Dimensão 1 ou uma Dimensão 2? O modelo descobriu que o texto era ambíguo aqui, ou simplesmente escolheu uma interpretação?"

A resposta, na maioria dos casos, é Dimensão 2: a linguagem tolerava múltiplas leituras, e a formalização escolheu uma delas e a tornou explícita.

### Passo 4: rode o segundo passo (2 min)

Rode mais uma passagem. Mostre que o gap entre o original e o output diminuiu. O documento está convergindo.

Feche com:

> "O processo para quando não há mais ambiguidade resolvível sem input do autor. Nesse ponto, o que resta são escolhas de Dimensão 1: intenção que só quem escreveu o documento pode definir. É exatamente aí que o humano é insubstituível."

---

## 7. O que muda na prática

Três coisas mudam quando você pensa com esse modelo.

**A pergunta de diagnóstico muda.** Antes: "o que entregamos?" Agora: "o que desambiguamos, e em qual dimensão?" Um ciclo que não produziu nenhuma redução de ambiguidade identificável produziu artefatos, não aprendizado.

**O papel da ferramenta de formalização muda.** Ela tem dois usos legítimos e distintos: como scout (formalizar para revelar ambiguidade que ainda não foi identificada) e como executor (formalizar uma intenção já suficientemente clara). O erro é usar como executor quando a ambiguidade ainda não foi tratada. A instrução que você passa, a um programador, a uma ferramenta, a um agente, não é o início do processo de pensar. É o registro de uma intenção que já passou por desambiguação suficiente.

**O que se espera de um bom engenheiro muda.** O skill mais valioso não é operar bem a ferramenta. É reconhecer qual tipo de ambiguidade está presente antes de executar, e saber o que fazer com cada uma. Quando ir ao mundo (Dimensão 1). Quando precisar a intenção (Dimensão 2).

Engenheiros que desenvolvem essa capacidade se tornam multiplicadores: não porque produzem mais código, mas porque o código que produzem materializa intenções genuinamente desambiguadas.

Um exemplo concreto. A sprint termina com um card claro: "adicionar busca de produtos ao catálogo". A equipe está alinhada. Antes de implementar, um scout deliberado: a mesma intenção, formulada de três formas distintas para a ferramenta.

*"Implemente a busca de produtos no catálogo."*
*"Permita que o usuário encontre produtos pelo nome."*
*"Filtre a lista de produtos conforme o usuário digita."*

Três outputs. O primeiro: busca full-text contra nome, descrição e categoria, com ranking por relevância. O segundo: correspondência parcial por nome, case-insensitive. O terceiro: filtragem client-side nas colunas visíveis da tabela.

Nenhum está errado. Todos são formalizações válidas de "busca de produtos". A divergência não é falha da ferramenta. É a imprecisão da palavra "busca" tornando-se visível.

O que conta como correspondência? Em quais campos? O sistema consulta ou o cliente filtra? Como os resultados são ordenados? A reunião nunca precisou responder essas perguntas. A linguagem natural tolerava todas as interpretações ao mesmo tempo.

O próximo passo não é escolher o melhor output. É responder as perguntas que a divergência revelou.

---

## 8. Fechamento

O processo de tradução que o desenvolvimento de software sempre foi carregou, desde o início, duas fontes de ambiguidade.

A primeira foi nomeada pelo Deliberate Discovery: a ignorância sobre o mundo que precisa ser descoberta antes de virar custo.

A segunda era gerenciada implicitamente pelo programador humano. Um filtro embutido no próprio ato de construir. A IA tornou esse filtro visível ao removê-lo.

O colapso do custo de formalização não resolve a ambiguidade do mundo. Amplifica. Cada sistema construído adiciona comportamento ao ambiente em que outros sistemas precisam operar. Cada nova composição gera estados que ninguém previu. A primeira dimensão cresce. A segunda se multiplica.

AI reduz variedade: escolhe a interpretação mais provável e executa. O humano que sabe desambiguar deliberadamente é o que mantém capacidade de resposta proporcional a esse ambiente.

Torna-se o fator limitante.

> Desenvolver software é navegar território desconhecido. O mecanismo dessa navegação é a tradução iterativa de intenção humana de linguagem natural para linguagem formal, removendo ambiguidade a cada passo.
>
> O output de cada ciclo é desambiguação.
> O outcome acumulado é aprendizado.
> AI não mudou o que o processo é. Tornou impossível ignorar o que ele sempre exigiu.

---

*Baseada no conceito de Deliberate Discovery (Dan North) e sua extensão com a segunda dimensão da ambiguidade que o processo de tradução sempre carregou.*
