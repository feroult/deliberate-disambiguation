# Desambiguação Deliberada
### Uma palestra sobre o que o desenvolvimento de software sempre foi, e ficou impossível ignorar

---

## 1. Abertura

Feche os olhos. Pense no último projeto que você terminou.

Agora imagine que você pode voltar ao início. Apaga o código, a documentação, os deploys. Mas mantém tudo que você aprendeu.

Duas perguntas:

O que você faria igual?

O que você faria diferente?

A segunda lista é o que o projeto produziu de mais valioso. Não o código. O conhecimento que, se você tivesse no início, teria mudado o que você construiu.

Desenvolvimento de software, nesse sentido, é um processo de aprendizado. O software é o que sobra. O aprendizado é o que acumula.

---

## 2. O mecanismo

Navegar território desconhecido exige um mecanismo. No desenvolvimento de software, esse mecanismo tem uma forma específica. Pensa num espectro:

```
LINGUAGEM NATURAL ──────────────────────► LINGUAGEM FORMAL
Ambígua, rica, implícita                  Precisa, executável, literal
```

De um lado, o mundo das intenções. Linguagem natural tolera ambiguidade: uma mesma frase pode significar coisas diferentes para pessoas diferentes, e isso funciona. Nós navegamos ambiguidade com contexto, tom, histórico compartilhado.

Do outro, o mundo das máquinas. Código não interpreta. Executa. Um sistema não infere o que você quis dizer. Faz exatamente o que foi especificado.

Desenvolver software é mover intenção ao longo desse espectro. Cada passo exige que uma ambiguidade seja resolvida. Você não formaliza algo com duas interpretações possíveis sem escolher uma.

Formalização é redução: de muitos significados possíveis para um único significado preciso.

Esse processo sempre existiu. O que variou foi o custo de cada passo. E o que acontece quando esse custo vai a zero.

---

## 3. O que Dan North nomeou, e o que ele deixou de fora

Em 2011, escrevi para o InfoQ sobre uma ideia que Dan North tinha acabado de articular. Escrevi com a confiança de quem acabou de aprender algo.

Quinze anos depois, percebo que eu estava certo sobre uma coisa que não entendia completamente.

O que North nomeou: projetos falham não por falta de competência técnica, mas por falta de conhecimento sobre o que estão construindo. A verdadeira restrição não era velocidade de execução.

Era capacidade de aprender.

O ponto de partida é incômodo: a maior parte do risco em projetos vem do que os times não sabem que não sabem. A distinção importa:

```
Não sei o que não sei   →   ignorância de 2ª ordem   (invisível, perigosa)
Sei que não sei X       →   ignorância de 1ª ordem   (visível, atacável)
```

As incertezas que estão na lista podem ser planejadas, atacadas. O risco real vem da ignorância que ainda não foi reconhecida como tal.

Dan North provocava times com um exemplo concreto: coloque um hello world em produção antes de qualquer outra coisa. Não porque entrega valor. Porque revela tudo que você não sabia que não sabia: o pipeline de deploy, as credenciais, os bloqueios de aprovação. Nada disso está no backlog. Tudo aparece quando você tenta entregar de verdade.

É o scout: ação barata cujo propósito não é conquistar território, mas remover névoa.

Esse modelo estava certo. Permanece fundacional. Mas havia uma dimensão inteira que ele não nomeou. E que eu também não vi em 2011.

---

## 4. A segunda dimensão

Considere uma situação comum. A equipe toda está alinhada: "o administrador pode apagar um usuário". Dez palavras. Todo mundo assinou sorrindo.

Quando você senta para formalizar, as perguntas começam.

Apagar significa remover permanentemente ou marcar como inativo? O que acontece com o conteúdo que ele criou? Com os pedidos em aberto? Com os registros de auditoria? O usuário é notificado? Pode ser reativado?

Agora para. Olha essas perguntas com cuidado.

Algumas são semânticas: o que "apagar" significa nesse domínio? Essas existem na linguagem. A frase era ambígua e a conversa nunca precisou resolver.

Outras são de domínio: o usuário *pode* ser reativado? Por quanto tempo os dados precisam ser retidos? Você não sabe — porque nunca perguntou ao negócio. Não é imprecisão da linguagem. É ignorância sobre o mundo. A tentativa de precisar a D2 revelou uma D1 escondida embaixo.

E mesmo depois de responder as duas — depois de decidir que "apagar" significa soft delete, que dados ficam por 90 dias, que a reativação é possível por administrador — ainda há uma camada que a especificação não alcança. Onde esse estado "inativo" vive? Que impacto tem nos relatórios, nas integrações, nos índices de busca? Que decisões de hoje vão custar caro quando o compliance mudar?

Essas não são perguntas sobre palavras. São perguntas sobre como a decisão se encaixa no sistema que está sendo construído — e no sistema que ele vai se tornar.

Essa é a Dimensão 2 em sua forma completa: não só a imprecisão da linguagem, mas a ambiguidade de formalização que persiste mesmo depois que a linguagem foi precisada. E que só um engenheiro com visão do sistema inteiro — sua história, sua trajetória, suas restrições implícitas — consegue navegar.

| | Dimensão 1 | Dimensão 2 |
|---|---|---|
| Fonte | Realidade não encontrada ainda | Linguagem + escolhas de formalização sem modelo do sistema |
| Revelada por | Contato com o mundo real | Tentativa de formalização |
| Resolvida por | Exploração, validação | Especificação + percepção arquitetural |
| Metáfora | Névoa de guerra | Instrução que todos entenderam, cada um à sua maneira |

As duas dimensões não são pipelines separados. Elas se alimentam. Tentar resolver D2 revela D1. Resolver D1 abre espaço para precisar D2. O ciclo é o processo.

O que tornava isso gerenciável era o programador humano: encontrava imprecisão na especificação, pausava, perguntava, resolvia — e quando a resposta dependia do mundo, ia buscar. Operava nos dois modos, no mesmo ato de construir.

A IA não tem esse mecanismo. Escolhe a interpretação mais provável e executa. Não pausa. Não pergunta. Não distingue o que é ambiguidade de linguagem do que é ignorância sobre o domínio. Formaliza tudo da mesma forma: silenciosamente.

Quando formalizar passou a custar minutos, a Dimensão 2 deixou de ter quem a detectasse.

O que eu não vi em 2011 ficou impossível de ignorar.

---

## [DEMO] Convergência em ação

*(abra o terminal, coloque arquivo-fonte e output lado a lado)*

Acabei de descrever como formalização revela ambiguidade. Quero mostrar isso acontecendo em tempo real.

E vou fazer isso de um jeito um pouco torto: vou usar convergência para transformar o documento que deu origem a esta palestra. Um texto técnico sobre desambiguação deliberada, sendo formalizado iterativamente por um modelo de IA. Enquanto falo sobre o processo, o processo acontece na tela.

*(rode o primeiro passo de convergência)*

O modelo lê o documento e aplica todas as melhorias que consegue fazer numa passagem. Não é reescrita. É formalização iterativa. Cada passo resolve ambiguidades que o passo anterior não tocou.

*(abra o diff quando terminar)*

Olha o que mudou. Você vai encontrar pelo menos um lugar onde uma frase tinha dois sentidos possíveis e o modelo escolheu um. Um lugar onde um argumento estava declarado mas não desenvolvido, e o modelo o completou. Um lugar onde uma imprecisão que na conversa passaria batida não sobreviveu à formalização.

*(aponte um exemplo concreto no diff)*

Pergunta diagnóstica: essa mudança resolveu uma Dimensão 1 ou uma Dimensão 2?

Na maioria dos casos é Dimensão 2. A linguagem tolerava múltiplas leituras. A formalização escolheu uma delas e a tornou explícita. O output não estava errado. Estava impreciso.

*(rode o segundo passo)*

O gap diminuiu. O documento está convergindo.

O processo para quando não há mais ambiguidade resolvível sem input do autor. Nesse ponto, o que resta são escolhas de Dimensão 1: intenção que só quem escreveu pode definir. O modelo para. Pergunta. E continua só quando a resposta chega.

Exatamente aí o humano é insubstituível.

---

## 5. O que muda

Duas coisas mudam quando você pensa com esse modelo.

A primeira é a pergunta de diagnóstico. Antes: "o que entregamos?" Agora: "o que desambiguamos, e em qual dimensão?" Um ciclo que não produziu nenhuma redução de ambiguidade identificável produziu artefatos, não aprendizado.

A segunda é o que se espera de um bom engenheiro. O skill mais valioso não é operar bem a ferramenta. É reconhecer qual tipo de ambiguidade está presente antes de executar. Quando ir ao mundo buscar a resposta (Dimensão 1). Quando precisar a intenção antes de qualquer coisa (Dimensão 2).

Um exemplo concreto. Card claro: "adicionar busca de produtos ao catálogo". A equipe alinhada. Antes de implementar, um scout deliberado: a mesma intenção, formulada de três formas distintas.

*"Implemente a busca de produtos no catálogo."*
*"Permita que o usuário encontre produtos pelo nome."*
*"Filtre a lista de produtos conforme o usuário digita."*

Três outputs completamente diferentes. Busca full-text com ranking. Correspondência parcial por nome. Filtragem client-side. Todos corretos. Todos formalizações válidas de "busca de produtos".

A divergência não é falha da ferramenta. É a imprecisão da palavra "busca" tornando-se visível. A reunião nunca precisou responder o que isso significava. A linguagem natural tolerava todas as interpretações ao mesmo tempo.

"Busca" era uma palavra. Agora é uma decisão.

Mas o problema vai mais fundo que vocabulário.

Escolha a terceira opção: filtragem client-side. Você desambiguou. "Busca" agora tem um significado preciso nesse contexto. E ainda assim, o engenheiro que vai formalizar essa intenção precisa fazer escolhas que a especificação não faz.

Isso é uma feature de catálogo pequeno, ou vai ter dez mil produtos? O filtro vive no cliente hoje — e quando vier a versão mobile? Essa decisão abre ou fecha o caminho para busca semântica daqui a dois sprints?

Essas perguntas não são sobre o que "filtrar" significa. São sobre onde essa decisão se encaixa no sistema que está sendo construído. Um engenheiro com percepção arquitetural tem um modelo de onde o sistema está indo, e usa esse modelo para escolher a formalização que preserva as opções que vão importar. Não a interpretação mais provável. A que é coerente com a trajetória do sistema.

A máquina não tem esse modelo. Formaliza silenciosamente. O resultado pode ser correto agora e incoerente daqui a seis meses.

É aí que o gut feeling do engenheiro sênior — essa percepção contextual de como as decisões de hoje constrangem as de amanhã — é uma forma de desambiguação que a especificação não consegue capturar. E que a máquina no piloto automático não tem como fazer.

Alguém aqui está pensando: mas dá pra resolver isso com outro agente. Um agente de validação arquitetural. Você descreve a arquitetura do sistema, passa a formalização, o agente avalia se é coerente.

É uma ideia razoável. E funciona — em parte.

O agente pode verificar se a nova formalização contradiz o que já foi decidido. Isso é útil e real. Mas note o que você precisou passar para ele: um modelo do sistema. Sua estrutura atual, suas convenções, suas fronteiras.

O problema é que o modelo relevante não é esse. É o modelo do sistema que você *ainda está construindo*. A trajetória. As decisões que ainda não foram tomadas. As features que existem no roadmap mas não no código. As restrições que você sabe que vêm mas não estão documentadas em lugar nenhum.

Esse modelo não existe em nenhum arquivo. Ele existe na cabeça de quem esteve lá.

Você pode criar um agente que valida contra o sistema de hoje. Mas quem define o modelo do sistema de amanhã? De volta ao engenheiro. O problema não foi eliminado. Foi movido um nível acima.

E agora você tem dois problemas: o de antes, mais o de garantir que o agente validador tem o modelo certo do futuro. Que é, ele mesmo, um problema de Dimensão 1.

---

## 6. Fechamento

O humano que sabe desambiguar deliberadamente torna-se o fator limitante.

Não porque é mais rápido. Porque é o único que para quando precisa parar, pergunta quando precisa perguntar, e só formaliza quando a intenção já é precisa o suficiente para executar.

AI não mudou o que o processo é. Tornou impossível ignorar o que ele sempre exigiu.
