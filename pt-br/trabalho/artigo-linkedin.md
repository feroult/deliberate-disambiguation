# O software que vem não é menos software

*Fonte: modelo-mental-desambiguacao-deliberada.md*  
*Status: rascunho para revisão*

---

AI escreve código mais rápido. Logo, precisamos de menos pessoas para escrever código.

A lógica circula como verdade inevitável. Mas ela parte de uma premissa que não aguenta o exame: que existe uma quantidade fixa de software a ser construído, e que a máquina está tomando a parte do humano.

Software nunca foi uma quantidade fixa. Ele sempre cresceu para preencher o espaço que as ferramentas abriram.

---

**O que está acontecendo não é compressão. É mudança de natureza.**

Quando o custo de construir colapsa, o que muda não é a velocidade do mesmo trabalho — é o que se torna possível construir. Saímos do software que executa estados para o software que gera estados: sistemas agênticos, composições que produzem comportamento emergente, código que opera sobre outro código.

Cada sistema construído adiciona comportamento ao ambiente em que outros sistemas precisam operar. E cada nova composição gera estados que ninguém previu. O território não fica apenas maior — fica combinatorialmente mais variado, enquanto você ainda está tentando navegá-lo.

O medo de que não haverá mais software é o inverso do que está acontecendo.

---

**O que navegar esse ambiente exige**

Para navegar um sistema que cresce em variedade, você precisa de capacidade de resposta proporcional à sua variedade. AI reduz variedade — escolhe a interpretação mais provável e executa. É excelente nisso.

Mas reduzir variedade num ambiente que está ficando combinatorialmente mais complexo não é navegar. É executar com confiança crescente num mapa que está ficando desatualizado.

O que a AI tornou visível não é que a máquina pode escrever código. É o que sempre foi o centro do trabalho de desenvolvimento — e que a máquina não faz.

---

**O mecanismo que sempre esteve lá**

Desenvolver software é mover intenção de linguagem natural para linguagem formal. Cada passo nessa direção exige que uma ambiguidade seja resolvida. Você não pode formalizar algo que ainda tem duas interpretações possíveis sem escolher uma.

Esse processo sempre carregou duas fontes de ambiguidade que operam de formas diferentes.

A primeira é a ignorância sobre o mundo: hipóteses não validadas, domínio não completamente compreendido, comportamento real de usuários desconhecido. Dan North nomeou isso no Deliberate Discovery — a maior parte do risco em projetos vem do que os times não sabem que não sabem.

A segunda é a imprecisão inerente à linguagem natural, que só se manifesta quando você tenta ser preciso o suficiente para uma máquina executar. "O administrador pode apagar um usuário" é perfeitamente compreensível numa reunião. Quando você senta para formalizar, emergem perguntas que a conversa nunca precisou responder: apagar significa remover permanentemente ou marcar como inativo? O que acontece com o conteúdo criado? Com os registros de auditoria?

Antes da AI, essa segunda fonte de ambiguidade era gerenciada implicitamente pelo programador humano: o agente de formalização que também detectava imprecisão e sabia pausar para resolvê-la. A AI substituiu esse intermediário por uma máquina que não detecta ambiguidade — escolhe a interpretação mais provável e executa, sem saber se é a correta para o seu domínio.

---

**O output divergente não é falha. É evidência.**

Quando a ferramenta produz algo diferente do que você esperava, a reação comum é ajustar o prompt e tentar de novo. Mas a divergência entre o que você descreveu e o que a máquina entendeu é a imprecisão da sua linguagem tornando-se visível. A máquina escolheu uma das interpretações válidas da sua frase — e ao fazê-lo revelou que havia mais de uma.

A pergunta certa não é "como ajusto a instrução?" — é "qual tipo de ambiguidade essa divergência está revelando?"

Se é ignorância sobre o mundo: você precisa ir ao mundo buscar a resposta. Conversar com usuários reais, rodar um experimento, validar uma hipótese com dados.

Se é imprecisão na linguagem da intenção: você precisa precisar o que está pedindo antes de pedir de novo.

São remédios diferentes para sintomas parecidos. Confundir os dois é a causa mais comum de retrabalho que ninguém consegue nomear.

---

**O teste de um ciclo bem-feito**

Não é a sensação de progresso. É conseguir completar uma dessas frases ao fim do ciclo:

*"Descobrimos que os usuários não fazem X como assumíamos."*

*"Decidimos que 'busca' significa correspondência parcial, sem distinção de maiúsculas."*

A primeira é aprendizado sobre o mundo. A segunda é precisão sobre a intenção. As duas são formas de nomear o que foi resolvido.

Se você não consegue completar nenhuma das duas, o ciclo produziu artefatos — não aprendizado. E artefatos sem aprendizado não acumulam. Eles apenas acrescentam ao território que o próximo ciclo vai ter que navegar.

---

**Quem se torna escasso**

Quando construir era lento, a lentidão forçava desambiguação. Você pensava antes de formalizar porque formalizar custava caro. Muito da imprecisão era resolvida implicitamente durante o ato de escrever código — o programador encontrava a ambiguidade e resolvia no processo.

Quando construir custa minutos, esse mecanismo desaparece. A ambiguidade não tratada se formaliza em sistema antes que alguém perceba o problema. A velocidade amplifica tanto o valor de desambiguar deliberadamente quanto o custo de não fazer isso.

O desenvolvedor que sabia construir software linear num mundo previsível está sendo substituído. O que sabe navegar território que se move enquanto é navegado está ficando mais escasso, não menos.

AI não mudou o que o processo é — tornou impossível ignorar o que ele sempre exigiu.

---

*O modelo completo — com as duas dimensões de ambiguidade, o loop de desambiguação deliberada e os arquivos de trabalho que documentam como o modelo foi construído — está em:*

*github.com/feroult/deliberate-disambiguation*
