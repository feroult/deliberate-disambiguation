# Desambiguação Deliberada

---

## 1. Abertura

O que é ser engenheiro de software está mudando. Não o ferramental. O papel fundamental.

Feche os olhos. Pense no último projeto que você terminou.

Agora imagine que você pode voltar ao início. Apaga o código, a documentação, os deploys. Mas mantém tudo que você aprendeu.

Duas perguntas:

O que você faria igual?

O que você faria diferente?

*(pausa)*

A segunda lista é o que o projeto produziu de mais valioso. Não o código. O conhecimento que, se você tivesse no início, teria mudado o que você construiu.

Desenvolvimento de software, nesse sentido, é um processo de aprendizado. O software é o que sobra. O aprendizado é o que acumula.

Se a lista do que você faria diferente é mais longa, o projeto funcionou. Você saiu dele sabendo mais do que entrou. Esse é o trabalho.

A pergunta não é o que a AI mudou. É o que ela revelou.

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

Formalizar é escolher: de muitos significados que funcionariam, um único vai executar.

Esse processo sempre existiu. O que variou foi o custo de cada passo. E o que acontece quando esse custo vai a zero.

O gargalo não desaparece. Muda de endereço.

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

Ninguém aprova "hello world em produção" na reunião de planejamento. Funciona melhor como "validação de pipeline com artefato de referência mínimo". O conteúdo é o mesmo. A névoa removida, idem.

Esse modelo estava certo. Permanece fundacional. Mas havia uma dimensão inteira que ele não nomeou. E que eu também não vi em 2011.

---

## 4. A segunda dimensão

Considere uma situação comum. A equipe toda está alinhada: "o administrador pode apagar um usuário". Dez palavras. Todo mundo assinou sorrindo.

Quando você senta para formalizar, as perguntas começam.

Apagar significa remover permanentemente ou marcar como inativo? O que acontece com o conteúdo que ele criou? Com os pedidos em aberto? Com os registros de auditoria? O usuário é notificado? Pode ser reativado?

Agora para. Olha essas perguntas com cuidado. São três camadas distintas.

Algumas são semânticas: o que "apagar" significa nesse domínio? Essas existem na linguagem. A frase era ambígua e a conversa nunca precisou resolver.

Outras são de domínio: o usuário *pode* ser reativado? Por quanto tempo os dados precisam ser retidos? Você não sabe. Nunca perguntou ao negócio. Não é imprecisão da linguagem. É ignorância sobre o mundo. A tentativa de precisar a D2 revelou uma D1 escondida embaixo.

E mesmo depois de decidir tudo isso (soft delete, 90 dias de retenção, reativação por administrador), ainda há uma camada que a especificação não alcança. Onde esse estado "inativo" vive? Que impacto tem nos relatórios, nas integrações, nos índices de busca? Que decisões de hoje vão custar caro quando o compliance mudar?

Essas não são perguntas sobre palavras. São perguntas sobre como a decisão se encaixa no sistema que está sendo construído, e no que ele vai se tornar.

Essa é a Dimensão 2 em sua forma completa: não só a imprecisão da linguagem, mas a ambiguidade de formalização que persiste mesmo depois que a linguagem foi precisada. Só um engenheiro que carrega o histórico do sistema, sua trajetória e suas restrições implícitas, consegue navegar.

| | Dimensão 1 | Dimensão 2 |
|---|---|---|
| Fonte | Realidade não encontrada ainda | Imprecisão da linguagem + modelo do sistema ausente |
| Revelada por | Contato com o mundo real | Tentativa de formalização |
| Resolvida por | Exploração, validação | Especificação + percepção arquitetural |
| Metáfora | Névoa de guerra | Instrução que todos entenderam, cada um à sua maneira |

As duas dimensões não são pipelines separados. Elas se alimentam. Tentar resolver D2 revela D1. Resolver D1 abre espaço para precisar D2. O ciclo é o processo.

O que tornava isso gerenciável era o programador humano: encontrava imprecisão na especificação, pausava, perguntava, resolvia. Quando a resposta dependia do mundo, ia buscar. Operava nos dois modos, no mesmo ato de construir.

A IA não tem esse mecanismo. Escolhe a interpretação mais provável e executa. Não pausa. Não pergunta. Não distingue o que é ambiguidade de linguagem do que é ignorância sobre o domínio. Formaliza tudo da mesma forma: silenciosamente.

Quando formalizar passou a custar minutos, a Dimensão 2 deixou de ter quem a detectasse.

A velocidade aumentou. A pergunta sobre o papel do engenheiro ficou sem resposta.

O que eu não vi em 2011 ficou impossível de ignorar.

---

## [DEMO] Convergência em ação

*(abra o terminal, coloque arquivo-fonte e output lado a lado)*

Acabei de descrever como formalização revela ambiguidade. Quero mostrar isso acontecendo em tempo real.

E vou fazer isso de um jeito um pouco torto: vou usar convergência para transformar o documento que deu origem a esta palestra. Um texto técnico sobre desambiguação deliberada, sendo formalizado iterativamente por um modelo de IA. Enquanto falo sobre o processo, o processo acontece na tela.

*(rode o primeiro passo de convergência)*

O modelo lê o documento e aplica todas as melhorias que consegue fazer numa passagem. Não é reescrita. É formalização iterativa. Cada passo resolve ambiguidades que o passo anterior não tocou.

*(abra o diff)*

Olha o que mudou. Você vai encontrar pelo menos um lugar onde uma frase tinha dois sentidos possíveis e o modelo escolheu um. Um lugar onde um argumento estava declarado mas não desenvolvido, e o modelo o completou. Um lugar onde uma imprecisão que na conversa passaria batida não sobreviveu à formalização.

*(aponte um exemplo concreto no diff — se o live run não surfaçar o esperado, use o diff de referência preparado)*

Pergunta diagnóstica: essa mudança resolveu uma Dimensão 1 ou uma Dimensão 2?

Na maioria dos casos é Dimensão 2. A linguagem tolerava múltiplas leituras. A formalização escolheu uma delas e a tornou explícita. O output não estava errado. Estava impreciso.

*(rode o segundo passo)*

O gap diminuiu. O documento está convergindo.

O processo para quando não há mais ambiguidade resolvível sem input do autor. Nesse ponto, o que resta são escolhas de Dimensão 1: intenção que só quem escreveu pode definir. O modelo para. Pergunta. E continua só quando a resposta chega.

Exatamente aí o humano é insubstituível. E não só porque o modelo para. Consistência replica o que foi decidido. Discernimento reconhece quando parar de replicar. São coisas diferentes.

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

Mas desambiguar o vocabulário não é o fim do trabalho. É só o início de uma decisão maior.

Escolha a terceira opção: filtragem client-side. Você desambiguou. "Busca" agora tem um significado preciso nesse contexto. E ainda assim, o engenheiro que vai formalizar essa intenção precisa fazer escolhas que a especificação não faz.

Isso é uma feature de catálogo pequeno, ou vai ter dez mil produtos? O filtro vive no cliente hoje. E quando vier a versão mobile? Essa decisão abre ou fecha o caminho para busca semântica daqui a dois sprints?

Essas perguntas não são sobre o que "filtrar" significa. São sobre onde essa decisão se encaixa no sistema que está sendo construído. Um engenheiro com percepção arquitetural tem um modelo de onde o sistema está indo, e usa esse modelo para escolher a formalização que preserva as opções que vão importar. Não a interpretação mais provável. A que é coerente com a trajetória do sistema.

Se você já disse "isso vai virar problema" antes de abrir o editor, você já fez isso. A palestra não está ensinando o que você não sabe. Está dando nome ao que você já faz.

A máquina não tem esse modelo. Formaliza silenciosamente. O resultado pode ser correto agora e incoerente daqui a seis meses.

*(nova linha de argumento)*

Alguém aqui está pensando: mas dá pra resolver isso com outro agente. Um agente de validação arquitetural. Você descreve a arquitetura do sistema, passa a formalização, o agente avalia se é coerente.

Honestamente? Eu pensei nisso também.

É uma ideia razoável. Funciona, em parte.

O agente pode verificar se a nova formalização contradiz o que já foi decidido. Isso é útil e real. Mas note o que você precisou passar para ele: um modelo do sistema. Sua estrutura atual, suas convenções, suas fronteiras.

O problema é que o modelo relevante não é esse. É o modelo do sistema que você *ainda está construindo*. A trajetória. As decisões que ainda não foram tomadas. As features que existem no roadmap mas não no código. As restrições que você sabe que vêm mas não estão documentadas em lugar nenhum.

Esse modelo não existe em nenhum arquivo. Ele existe na cabeça de quem esteve lá.

Você pode criar um agente que valida contra o sistema de hoje. Mas quem define o modelo do sistema de amanhã? De volta ao engenheiro. O problema não foi eliminado. Foi movido para onde sempre esteve.

O agente precisa do modelo para funcionar. O modelo relevante é o de amanhã. E o engenheiro que o carrega é o mesmo que reconhece quando o padrão passado deixou de ser a resposta certa. Consistência replica. Discernimento percebe quando parar de replicar.

Não é um gargalo humano num processo que a máquina poderia assumir. É a fonte sem a qual o processo não tem direção.

Boa notícia: é aí que você está.

(Não é pessimismo. É geografia.)

*(avança para o slide de transição; fica em silêncio por alguns segundos)*

---

## 6. Fechamento

Esse humano é o fator limitante. Não no sentido de gargalo, de obstáculo que atrasa. No sentido de ponto de decisão: a parte do processo que determina o throughput de todo o resto.

Não porque é mais rápido. Porque é o único que para quando precisa parar, pergunta quando precisa perguntar, e só formaliza quando a intenção já é precisa o suficiente para executar.

*(pausa)*

A indústria está encontrando nomes para esse papel. Harness engineer — quem constrói o scaffold que define onde a máquina pode agir. Supervisor engineer: quem revisa o que ela formalizou silenciosamente.

Os nomes vão mudar. O que eles descrevem não: o humano que sabe desambiguar deliberadamente.

A AI alargou o canal. O harness e o supervisor continuam, mas governam um fluxo maior. O papel do engenheiro não foi eliminado. Foi escalado.

Parar quando a pressão é para avançar. Perguntar quando todo mundo acha que já sabe a resposta. Você já faz isso. E sabe exatamente o custo de quando não fez.

*(pausa — olha para a plateia)*

O processo não mudou. Você sempre soube fazer isso. Agora tem nome.

---

## Slides Sugeridos

### Âncora visual — Espinha dorsal da apresentação

A apresentação organiza-se em torno de sete imagens âncora que formam uma narrativa visual progressiva e coerente.

**A metáfora central:** um feixe de streamlines — linhas curvas fluindo horizontalmente, mais amplas nas bordas, afunilando num canal estreito no centro, e expandindo simetricamente de volta. A forma é sempre a mesma. O que muda é o que está sobre ela e o que ela carrega de significado.

**As sete âncoras:**

**A1 — Descoberta:** Mapa parcialmente revelado com névoa de guerra. Uma figura humana na zona de clareza, olhando para o desconhecido. O território conhecido tem contornos cartográficos visíveis no fundo limpo. O resto: névoa densa. Introduz ignorância de 2ª ordem sem nomear.

**A2 — Espectro:** Textura em duas zonas — linguagem natural (esquerda, cursiva, caótica) e código estruturado (direita, monospaced, preciso). No centro, ghost streamlines em 10% de opacidade já estão presentes mas quase invisíveis: A2 e A3 coexistem na mesma imagem (slide 1), usada novamente no slide 3. A separação conceitual entre A2 (polos separados) e A3 (streamlines emergindo) é narrativa, não visual: a forma já está lá desde o início, esperando ser reconhecida.

**A3 — Semente do gargalo:** A forma do funil aparece antes de ter nome. "O gargalo não desaparece. Muda de endereço." A3 tem duas manifestações: integrada na imagem A2 (slides 1 e 3 — streamlines em 10% de opacidade sobre a textura do espectro, mesma imagem) e standalone para o slide 4 (streamlines em 15% de opacidade sobre fundo limpo, sem textura, imagem separada).

**A4 — Loop de desambiguação:** Streamlines ao fundo, contínuas. Sobre elas, o ciclo D1/D2 como overlay. No ponto de convergência — o centro horizontal — o âmbar (#c8882a) aparece: é onde a decisão humana ocorre.

**A5 — Transição:** Apenas streamlines. Sem D1/D2, sem âmbar, sem anotações. O fluxo puro. Slide de respiro entre a demo e o fechamento.

**A6 — Papeis nomeados:** Harness (linhas externas do feixe, branco 80%, guardrails) + supervisor (barra âmbar vertical no centro). Labels discretos como anotações técnicas.

**A7 — Canal alargado pela AI:** Streamlines em maior densidade. Setas diagonais marcam os harness limits expandidos. Setas verticais crescem a partir do centro (supervisor scaling).

**Regras do sistema visual:**
- Fundo: near-black (#0d0d14)
- Streamlines: branco ou cinza claro, sem setas de direção
- Âmbar (#c8882a): exclusivo para marcadores de decisão humana
- Harness lines: branco 80%, levemente mais espessas
- Estilo: vector-illustration, flat, zero profundidade de campo
- Labels (quando presentes): sans-serif cinza claro, anotação técnica

---

**Slide 1 — Título**
*Visual:* Fundo com imagem gerada. Texto sobreposto: "Desambiguação Deliberada" em tipografia sans-serif grande, branco, centrado.

> **Prompt de imagem:** Dark abstract background for a tech conference title slide, 16:9 aspect ratio. Deep near-black background (#0d0d14). Two texture zones blend across the frame, connected by flowing lines. Left third: a dense, organic layering of natural language fragments in white at 18% opacity — cursive handwriting in multiple styles and sizes, partial printed words at different angles, question marks, ellipses, em-dashes, crossed-out phrases, overlapping scripts, fragments that start and don't finish — the visual texture of ambiguity and richness, chaotic but warm. Right third: monospaced code characters, bracket symbols, curly braces, angle brackets, semicolons, type annotations, and function-signature fragments in white at 18% opacity, arranged in tight precise grid-like patterns — the texture of formal language, structured and cold. Center: multiple smooth curved streamlines run horizontally across the full width of the composition — widest at both the left and right edges, tapering gradually toward a narrow channel at the exact horizontal midpoint, then expanding symmetrically back out on the right side, exactly mirroring the flow shape that appears in the closing slides of this deck. Rendered in white at 10% opacity — barely there, just the shape. No amber. No labels. No harness lines. The two texture zones and the streamlines dissolve into each other at center with a soft gradient blur. No sharp boundaries. No recognizable words or complete sentences. The overall impression is two worlds in motion, one flowing into the other. Cinematic, intellectual, dark. Zero saturation. Aspect ratio 16:9.

*Conteúdo:* Abre a sessão em silêncio. O palestrante começa a falar antes de avançar.

---

**Slide 2 — O exercício**
*Visual:* Fundo escuro. Apenas duas perguntas, sem título:
"O que você faria igual?"
"O que você faria diferente?"
*Conteúdo:* O palestrante pediu que a audiência fechasse os olhos antes de mostrar. O slide aparece como resposta ao exercício.

---

**Slide 3 — O espectro**
*Visual:* Mesmo background do slide 1 (reutilizar a imagem gerada). Diagrama monospace sobreposto, centrado:

```
LINGUAGEM NATURAL ─────────────────► LINGUAGEM FORMAL
Ambígua, rica, implícita             Precisa, executável, literal
```

No ponto de convergência das streamlines do background — o centro horizontal do slide — um label pequeno em fonte sans-serif light, cinza claro, baixa opacidade: "Engenharia de Software". Posicionado discretamente, como uma anotação técnica.

*Conteúdo:* O mecanismo central. Palestrante explica os dois polos antes de mostrar o slide; o diagrama confirma. O label no centro planta onde a engenharia vive nesse espectro.

---

**Slide 4 — O gargalo muda de endereço**
*Visual:* Fundo com imagem gerada. Texto sobreposto, centrado, tipografia média: "O gargalo não desaparece. Muda de endereço."

> **Prompt de imagem (âncora A3):** Minimalist abstract background for a presentation slide, 16:9, near-black background (#0d0d14). Multiple smooth curved streamlines run horizontally across the full width — the same flow shape that will reappear in the closing slides, but rendered here as a ghost: all lines at 15% opacity, white, no amber, no labels, no harness lines. The lines converge gently toward the horizontal midpoint and expand back out symmetrically. The convergence is barely visible — present as a shape, not as a concept. The foreground is empty, leaving room for overlaid text. The image should feel like a shadow of something that hasn't been named yet. Flat, vector-illustration aesthetic. No depth of field. Aspect ratio 16:9.

*Conteúdo:* Última linha da seção 2. O speaker fala e avança sem explicar. A imagem fica por alguns segundos — o visual do funil plantado antes de ter nome.

---

**Slide 5 — Taxonomia da ignorância**
*Visual:* Diagrama em dois níveis com setas descendentes:

```
Não sei o que não sei  →  2ª ordem  (invisível, perigosa)
        ↓
Sei que não sei X      →  1ª ordem  (visível, atacável)
        ↓
             Conhecimento
```

*Conteúdo:* A estrutura do risco em projetos. O que pode ser atacado vs. o que ainda não foi reconhecido como ameaça.

---

**Slide 6 — O scout**
*Visual:* Imagem gerada, full-bleed, ocupando todo o slide. Legenda discreta na base.

> **Prompt de imagem (âncora A1):** Minimalist vector illustration on a near-black background (#0d0d14), 16:9, flat vector-illustration style — no painterly texture, no depth of field. The majority of the frame is filled with a dense semi-opaque layer of tiny near-white particles suggesting fog or unknown territory — flat, not volumetric. At the lower-left region, a circular zone of clarity opens: the fog dissolves here, revealing the clean dark background beneath. Within the cleared zone, subtle topographic contour lines and a faint cartographic grid are visible on the dark background — rendered in white at 10% opacity, the visual language of a partially-revealed map, suggesting that what was hidden is now territory that can be named and traversed. The boundary between fog and clarity glows faintly in muted amber (#c8882a) — a soft luminous edge, not dramatic, just warm. At the center of the cleared zone, a minimal anonymous figure: a simple white silhouette, gender-neutral, no detail. The figure stands at the amber boundary facing toward the fog. Palette: near-black background, near-white fog particles, faint white map contours in the cleared zone, white figure, muted amber at the boundary only. Flat, vector-illustration aesthetic. Aspect ratio 16:9. The emotional register is quiet and deliberate — not heroic, not dramatic.

*Legenda no slide (fonte pequena, base):* "Ação barata cujo propósito não é conquistar território, mas remover névoa."
*Conteúdo:* O hello world em produção como scout. A ação que revela o que não estava no backlog.

---

**Slide 7 — "O administrador pode apagar um usuário"**
*Visual:* No centro, um cartão de user story: "O administrador pode apagar um usuário." Abaixo, em fonte menor, as perguntas emergindo em cascata: "Remover permanentemente ou soft delete?", "O conteúdo criado?", "Os pedidos em aberto?", "Auditoria?", "Reativação?"
*Conteúdo:* Introdução da Dimensão 2. As perguntas aparecem depois que o palestrante lança a história — o slide revela o que estava escondido atrás de dez palavras.

---

**Slide 8 — D1 × D2**
*Visual:* A tabela comparativa em tipografia limpa, sem bordas pesadas:

| | D1 | D2 |
|---|---|---|
| Fonte | Realidade não encontrada | Linguagem imprecisa + modelo ausente |
| Revelada por | Contato com o mundo real | Tentativa de formalização |
| Resolvida por | Exploração, validação | Especificação + percepção arquitetural |
| Metáfora | Névoa de guerra | Instrução que cada um entendeu à sua maneira |

*Conteúdo:* O palestrante não lê a tabela — aponta as linhas e comenta. Referência visual para a audiência fixar a distinção.

---

**Slide 9 — O loop**
*Visual:* Diagrama circular sobre fundo escuro. Dois nós conectados por dois arcos opostos formando um ciclo fechado.

> **Prompt de imagem (âncora A4):** Minimalist abstract diagram on a near-black background (#0d0d14), flat vector-illustration style, 16:9. Background layer: multiple smooth curved streamlines run horizontally across the full width — widest at both edges, tapering toward a narrow channel at the exact horizontal midpoint, then expanding symmetrically back out. Lines rendered in white at 20% opacity — present as a shape, not dominant. Foreground layer: a minimal circular diagram centered on the composition. Two soft-edged rectangular nodes — one at the top and one at the bottom of an implied circle, slightly offset horizontally. Top node labeled "D2" in light-grey sans-serif; bottom node labeled "D1", same treatment. Two smooth arcs connect the nodes — one clockwise on the right, one counter-clockwise on the left. Each arc has a small directional arrow at midpoint and a short label along the curve: right arc reads "tentar resolver D2 revela D1", left arc reads "resolver D1 abre espaço para D2". At the center of the diagram — where the arcs cross and where the streamlines converge — a subtle amber glow (#c8882a) marks the point of human decision: where disambiguation happens. Arcs rendered as gradient lines, white transitioning to muted amber toward the center. Overall: centered, symmetrical. No decorative elements. No shadows. Palette: near-black, white/light-grey, amber accent at center only. Aspect ratio 16:9.

*Conteúdo:* As dimensões não são sequenciais. O ciclo é o processo. A IA quebra esse ciclo ao não pausar.

---

**Slide 10 — DEMO**
*Visual:* Fundo escuro. Texto centrado: "DEMO". Abaixo, em fonte pequena para o palestrante: "(arquivo-fonte | output lado a lado)"
*Conteúdo:* Transição para a seção ao vivo. Palestrante abre o terminal e explica o que vai acontecer antes de rodar o primeiro passo.

---

**Slide 11 — Três prompts, três produtos**
*Visual:* Três caixas verticais lado a lado, cada uma com prompt e output correspondente:

| "Implemente a busca" | "Permita encontrar por nome" | "Filtre conforme digita" |
|---|---|---|
| Full-text com ranking | Correspondência parcial | Filtragem client-side |

*Conteúdo:* O scout deliberado em ação. A divergência como sinal de D2, não como falha da ferramenta.

---

**Slide 12 — Percepção arquitetural**
*Visual:* Linha do tempo horizontal sobre fundo escuro. Três pontos marcados conectados por seta pontilhada. Abaixo, as perguntas arquiteturais em fonte menor.

> **Prompt de imagem (background):** Dark illustration of an architectural blueprint or engineering schematic rendered as a subtle background texture, 16:9. Near-black background (#0d0d14). In the background, thin white technical drawing lines — floor plans, circuit traces, or system diagrams — rendered at 14–16% opacity, visible but not dominant; lines are crisp, not blurred. A faint grid of fine horizontal and vertical guide lines at 10% opacity underlies the schematic, suggesting precision and structure. The overall texture reads as "a system being thought through" without depicting any specific recognizable object. One region of the composition — roughly the left third — has slightly denser linework, creating a subtle visual anchor without becoming a focal point. The foreground is otherwise empty, leaving space for overlaid text and diagram. Mood: precise, intelligent, slightly cold. Flat, no depth of field, no lighting drama. Vector-illustration aesthetic. Aspect ratio 16:9.

> **Design spec do diagrama (Figma/Keynote):** Linha horizontal centralizada, cor branca 60% opacidade, ocupando 70% da largura do slide. Três pontos na linha: círculo preenchido de 10px cada. Label acima de cada ponto em fonte regular 14pt. Seta pontilhada no sentido esquerda→direita com espaçamento de traço irregular (sugerindo incerteza/futuro). Ponto 1: "hoje — filtragem client-side". Ponto 2: "sprint +2 — busca semântica?" (ponto de interrogação explícito, cor levemente mais fraca). Ponto 3: "versão mobile" (ainda mais fraco, quase fantasma). Perguntas arquiteturais listadas abaixo da linha em 12pt, cor cinza claro.

*Nota visual:* Exceção intencional ao sistema de streamlines — o fundo de esquema técnico serve ao contexto específico de percepção arquitetural; o visual spine retoma no slide 13.
*Conteúdo:* O que a especificação não faz. O modelo mental do sistema que só existe na cabeça de quem esteve lá.

---

**Slide 13 — [transição]**
*Visual:* Fundo com imagem gerada. Sem texto sobreposto.

> **Prompt de imagem (âncora A5):** Minimalist abstract illustration on a near-black background (#0d0d14), flat vector-illustration style, 16:9. Multiple smooth curved streamlines run horizontally across the full width of the composition — widest at both the left and right edges, tapering gradually toward a narrow channel at the exact horizontal midpoint, then expanding symmetrically back out. Lines rendered in white at 40% opacity. Nothing else in the composition — no labels, no amber, no harness lines, no annotations, no diagram overlay. The streamlines are the only element. The shape is the message: flow constrained through a channel and continuing out the other side. Flat, vector-illustration. Aspect ratio 16:9.

*Conteúdo:* Pausa visual entre a demo e o fechamento. O palestrante não fala. A imagem fica 3–5 segundos antes de avançar. A forma do sistema está lá — o que falta nomear são os papeis.

---

**Slide 14 — O fator limitante**
*Visual:* Fundo com imagem editada a partir do slide 15. Texto sobreposto: "Esse humano é o fator limitante." em tipografia grande, branco.

> **Prompt de edição (a partir da imagem do slide 15):** Remove the two labels ("harness" and "supervisor") and their hairlines. Remove the amber vertical bar at the center, keeping only the ambient amber warmth that bleeds into the streamlines. Do not change the harness lines, the streamlines, the background, or the color palette. The result should be the same composition, clean — no annotations, no markers.

*Nota de produção:* Gerar a imagem do slide 15 primeiro; slide 14 é uma edição dela. A audiência não sabe disso.
*Conteúdo:* Abre a seção 6. O speaker enuncia a tese e a explica antes de avançar para o slide 15 onde nomeia os papeis.

---

**Slide 15 — Harness / Supervisor**
*Visual:* Fundo com imagem gerada. Texto sobreposto, duas linhas, tipografia média, branco:
"Harness engineer."
"Supervisor engineer."
Gerar esta imagem primeiro — o slide 14 é uma edição dela.

> **Prompt de imagem (âncora A6):** Minimalist abstract flow illustration on a near-black background (#0d0d14), vector-illustration style, 16:9. Multiple streamlines — smooth, curved parallel lines suggesting continuous horizontal flow — run across the full width of the composition. The lines are widest at both the left and right edges, filling most of the vertical space there. They taper gradually toward a narrow channel at the exact horizontal midpoint, then expand symmetrically back out on the right side. The lines pass through the center unbroken. At the narrow channel, a subtle amber warmth (#c8882a) bleeds into the lines. Two harness lines run along the outer edges of the streamline bundle — one above the topmost line, one below the bottommost line — converging at the channel and expanding back out symmetrically; they are more opaque and slightly thicker than the flow lines, rendered in white at 80% opacity, defining the limits within which the flow can act. A small label "harness" in light-grey sans-serif is placed just outside one of the harness lines on the left half of the image, with a minimal hairline connecting to it. At the amber center, a small vertical bar in the same amber tone marks the supervisor presence. A small label "supervisor" in the same light-grey sans-serif is placed just above or below the amber bar, with a minimal hairline connecting to it. Labels feel like technical annotations — quiet, precise, not decorative. Palette: near-black background, white/light-grey for flow lines and harness lines, muted amber at center. Flat, no depth of field. Aspect ratio 16:9.

*Conteúdo:* Os nomes que a indústria está encontrando. Os nomes vão mudar. O que eles descrevem não.

---

**Slide 16 — O canal alargado**
*Visual:* Fundo com imagem gerada. Texto sobreposto, uma linha, tipografia média, branco: "A AI alargou o canal."

> **Prompt de imagem (âncora A7):** Minimalist abstract flow illustration on a near-black background (#0d0d14), vector-illustration style, 16:9. Multiple streamlines — smooth, curved parallel lines — run across the full width of the composition, wider and more numerous than in the harness/supervisor slide: the channel itself is wider, the flow denser. The lines taper toward a center channel and expand back out, same shape as before, but with more lines and greater spread. Two harness lines run along the outer edges of the streamline bundle, rendered in white at 80%, converging and expanding with the flow. At the harness lines, short diagonal tick marks point outward — the guardrail has expanded, the boundary moved outward to contain the larger flow. At the center channel, a vertical amber bar marks the supervisor presence; from the top and bottom of this bar, short vertical arrows extend upward and downward — the supervisor is scaling, governing more throughput than before. The overall impression: same system, wider capacity, same human control structure. Palette: near-black background, white/light-grey streamlines and harness, muted amber (#c8882a) at center. Flat, no depth of field. Aspect ratio 16:9.

*Conteúdo:* A AI alargou o canal. O harness e o supervisor continuam, mas governam um fluxo maior. O papel do engenheiro não foi eliminado. Foi escalado.

---

**Slide 17 — Fechamento**
*Visual:* Fundo com imagem gerada. Texto sobreposto, duas linhas, tipografia ampla, branco:
"O processo não mudou."
"Você sempre soube fazer isso. Agora tem nome."

> **Prompt de imagem:** Cinematic abstract background for a closing presentation slide, 16:9. A long empty corridor or tunnel, viewed from straight-on perspective — perfectly centered vanishing point. The corridor is modern and geometric: clean concrete or dark metal walls, receding into a distant point of faint warm light. The near end (foreground) is in almost total darkness; the far end glows dimly, suggesting continuation rather than termination. No figures. No labels. No windows. The corridor should feel like time or process — something that was always there, that you always had to walk through, that hasn't changed even if the speed has. Photorealistic or cinematic digital painting. Palette: near-monochromatic dark charcoal and near-black, with a single warm amber-white glow at the vanishing point. The mood is quiet, honest, and slightly sobering — not triumphant, not tragic. Just clear.

*Nota visual:* Exceção intencional ao sistema de streamlines — o corredor encerra com uma metáfora de continuidade em vez de permanecer no vocabulário técnico. O visual spine completou seu arco no slide 16.
*Conteúdo:* Última linha falada. Slide fica na tela enquanto abre para perguntas.

---

## Palácio Mental

*Âncora visual → ideia central → quando clicar.*

---

### Abertura (slides 1–2)

**[1] Título** — dois mundos fluindo para um canal estreito
Começa falando antes de avançar. Faz o exercício inteiro: "Feche os olhos..."
→ **clica em:** "Duas perguntas:"

**[2] O exercício** — duas perguntas na tela
*(pausa longa — deixa a audiência pensar)*
**Punchline:** "A pergunta não é o que a AI mudou. É o que ela revelou."
→ **clica depois** da última linha.

---

### Mecanismo (slides 3–4)

**[3] O espectro** — diagrama + "Engenharia de Software" no centro
**Punchline:** "Formalizar é escolher: de muitos significados que funcionariam, um único vai executar."
→ **clica em:** "O gargalo não desaparece. Muda de endereço."

**[4] Gargalo** — streamlines fantasma, sem texto
*(silêncio — 2 a 3 segundos. Não fala.)*
→ **clica** em silêncio.

---

### North (slides 5–6)

**[5] Taxonomia** — diagrama 2ª ordem → 1ª ordem → Conhecimento
**Punchline:** "O risco real vem da ignorância que ainda não foi reconhecida como tal."
→ **clica em:** "É o scout: ação barata cujo propósito não é conquistar território, mas remover névoa."

**[6] Scout** — figura na borda da névoa, âmbar no limite
**Punchline:** "Esse modelo estava certo. Mas havia uma dimensão inteira que ele não nomeou. E que eu também não vi em 2011."
→ **clica** ao final da seção 3.

---

### Segunda dimensão (slides 7–9)

**[7] Apagar usuário** — cartão → perguntas em cascata
*(as perguntas em cascata são o punchline — deixa a audiência ler)*
→ **clica em:** "Agora para. São três camadas distintas."

**[8] D1 × D2** — tabela
*(não lê — aponta e comenta)*
**Punchline:** "As duas dimensões não são pipelines separados. Elas se alimentam."
→ **clica em:** "O ciclo é o processo."

**[9] O loop** — ciclo D1↔D2, âmbar no centro
**Punchline:** "A IA formaliza tudo da mesma forma: silenciosamente."
→ **clica** ao abrir o terminal.

---

### Demo (slides 10–11)

**[10] DEMO** — tela preta
*(abre terminal, arquivo-fonte | output lado a lado; demo acontece aqui)*
**Punchline:** "Consistência replica o que foi decidido. Discernimento reconhece quando parar de replicar."
→ **clica** antes do exemplo de busca de produtos.

**[11] Três prompts** — tabela 3 × 2
**Punchline:** "'Busca' era uma palavra. Agora é uma decisão."
→ **clica em:** "Mas desambiguar o vocabulário não é o fim do trabalho."

---

### O que muda (slide 12)

**[12] Percepção arquitetural** — blueprint + linha do tempo
**Punchline:** "Não a interpretação mais provável. A que é coerente com a trajetória do sistema."
*(contra-argumento do agente validador vem aqui)*
→ **clica depois de:** "(Não é pessimismo. É geografia.)" + pausa.

---

### Transição (slide 13)

**[13] Silêncio** — streamlines puras, sem texto
*(3 a 5 segundos. Não fala. Avança.)*
→ **clica** em silêncio.

---

### Fechamento (slides 14–17)

**[14] Fator limitante** — A6 sem labels, texto grande na tela
**Punchline:** "Porque é o único que para quando precisa parar, pergunta quando precisa perguntar."
→ **clica** depois da *(pausa)*, antes de nomear os papéis.

**[15] Harness / Supervisor** — A6 com labels
**Punchline:** "Os nomes vão mudar. O que eles descrevem não."
→ **clica em:** "Os nomes vão mudar. O que eles descrevem não."

**[16] Canal alargado** — streamlines mais densas, setas expandindo
*(slide aparece; então fala)* "A AI alargou o canal."
**Punchline:** "O papel do engenheiro não foi eliminado. Foi escalado."
→ **clica** na *(pausa — olha para a plateia)*.

**[17] Fechamento** — corredor, luz ao fundo
**Última linha:** "O processo não mudou. Você sempre soube fazer isso. Agora tem nome."
→ **fica na tela** durante Q&A.
