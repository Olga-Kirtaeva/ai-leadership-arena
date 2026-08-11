# Literature Review: AI Leadership Arena

**Версия:** 0.4 — полный библиографический аудит ключевого корпуса
**Дата проверки:** 11 августа 2026 года  
**Статус:** рабочий документ; библиографическая верификация продолжается

## 1. Scope and research problem

Главный вопрос проекта:

> Возникает ли спонтанная функциональная дифференциация между изначально
> однородными LLM-агентами, взаимодействующими без назначенных ролей, persona
> prompts и role-specific incentives?

Существование ролей заранее не предполагается. Сначала необходимо установить,
превышают ли различия stochastic/stateless variability, воспроизводятся ли
они, зависят ли от индивидуальной истории, переносятся ли между задачами и
сохраняются либо адаптируются после смены команды. Единичное различие в
поведении ещё не является устойчивой ролью.

## 2. Role differentiation in human teams: evidence from organizational and social psychology

Исследования команд людей в организационной и социальной психологии предлагают
несколько совместимых объяснений:
начальные различия получают групповое признание, повторное выполнение функции
создаёт опыт, специализация облегчает координацию, а ожидания партнёров
закрепляют распределение труда. Рабочая причинная цепочка:

> initial behavioral differences → group uptake / reinforcement →
> specialization → accumulated experience → increased efficiency / competence
> → repeated assumption of similar functions.

Emergent leadership следует отличать от формально назначенного руководства;
task-oriented вклад — от socio-emotional координации; функциональную
специализацию — от личностного типа. Повторное взаимодействие, размер команды,
стадии развития, координация и конфликт могут менять наблюдаемые паттерны.
Понятия storming и stabilization полезны как эвристики, но требуют
поведенческой операционализации.

Gardner et al. (2024), DOI:10.1146/annurev-orgpsych-110721-040430,
рассматривают leadership emergence как процесс на нескольких уровнях анализа,
а не как простое обнаружение фиксированной черты. Для Arena отсюда следует
измерять предоставление влияния другими участниками наряду с инициативой.

Tuckman (1965), DOI:10.1037/h0022100, синтезировал 50 работ и предложил четыре
стадии развития малых групп, разделяя interpersonal и task activity. Это
историческая теоретическая схема, а не универсальный закон и не основание
ожидать обязательный storming у LLM.

Bales (1950), *Interaction Process Analysis*, предложил наблюдательную систему
из 12 категорий с task и socio-emotional областями. Для Arena полезен принцип
кодирования наблюдаемых актов; исходные категории нельзя переносить без
адаптации и проверки надёжности.

Bernerth et al. (2023), DOI:10.1002/job.2708, в метаанализе показали, что связь
team size с effectiveness зависит от характеристик задач и process losses.
Это поддерживает size-ablation, но не утверждение об оптимальности четырёх.

Понятие человеческой мотивации не переносится на LLM: для агента измеряются
контекст, история, feedback и изменение вероятности поведения, а не
субъективное стремление.

## 3. Mechanisms of specialization: why should differentiation become self-reinforcing?

Центральная механистическая проблема состоит не только в том, повторяет ли
Agent A функцию, но и в том, почему ранний успех должен повышать вероятность
её повторного принятия. Кандидатная цепочка, перенесённая из исследований
команд людей, но не считающаяся доказанной для LLM:

> initial asymmetry → successful functional contribution → group uptake →
> repeated use of the agent in that function → accumulated context/history →
> increased efficiency → reproducible specialization.

Для AI каждый переход допускает конкурирующие объяснения:

- текущий transcript продолжает ранее начатый план;
- партнёры адресуют агенту сходные запросы и контекстуально закрепляют функцию;
- controlled self-history напоминает агенту его прошлые действия;
- objective performance feedback усиливает ранее успешную стратегию;
- наблюдаемое повторение остаётся случайностью.

Поэтому «функционально выгодно» здесь означает не субъективную выгоду или
мотивацию, а измеримое снижение координационных затрат, ошибок, ходов, времени
или токенов либо повышение качества после повторного выполнения функции.
Необходимо проверить, воспринимает ли этот сигнал сам агент, только его
партнёры или внешний контур оценки.

Механистический вопрос проекта:

> Through which interaction mechanisms, if any, does initially transient
> functional differentiation become reproducible specialization in
> homogeneous LLM-agent teams?

Минимальные условия добавляются ступенчато: stateless baseline; текущий
interaction context; persistent ID without history; controlled self-history;
controlled history plus objective feedback. Обозначения этих условий в
эксперименте должны следовать контракту памяти протокола, а не создавать новую
конкурирующую нумерацию M0–M3.

Особый исход — специализация, которую восстанавливает новая команда без памяти
самого агента. Тогда профиль является динамическим свойством взаимодействия
`agent × team`, а не устойчивым свойством агента.

### 3.1. Coordination-cost reduction

Roberts and Goldstone (2011), *Adaptive Group Coordination and Role
Differentiation*, PLOS ONE 6(7):e22377,
DOI:10.1371/journal.pone.0022377, — рецензированное экспериментальное
исследование общей групповой цели без прямой коммуникации. Участники подбирали
числовые вклады к неизвестной цели и получали общий feedback. С опытом группы
требовали меньше раундов; при росте размера группы наблюдались spontaneous role
differentiation и self-consistency. Интерпретация для Arena: специализация
может уменьшать число одновременно изменяющихся частей системы. Стабильный
вклад не следует автоматически кодировать как пассивность.

### 3.2. History-conditioned efficiency

Повторение человеческой функции может накапливать навык. Для LLM без изменения
weights допустим более узкий термин: **history-conditioned efficiency**.
Controlled history может дать подходящий procedural precedent; эффект должен
измеряться качеством, ошибками, ходами, временем и токенами, а не называться
обучением или компетентностью без дополнительного теста.

### 3.3. Group recognition and expectation

Партнёры могут воспроизводить специализацию, адресуя агенту похожие задачи,
ссылаясь на его вклад и освобождая соответствующую функцию. Поэтому необходимо
логировать адресованные запросы, ссылки на агента, принятие предложений и
последующее распределение функций. Influence здесь предоставляется
взаимодействием, а не выводится из самопровозглашения.

### 3.4. Transactive memory systems

Liang, Moreland and Argote (1995), *Group Versus Individual Training and Group
Performance: The Mediating Role of Transactive Memory*, DOI:
10.1177/0146167295214009, сравнили совместное и индивидуальное обучение сборке
транзисторных радиоприёмников. Совместно обучавшиеся тройки лучше вспоминали
процедуру и собирали более качественные устройства; анализ поддержал TMS как
основной посредующий механизм.

Lewis (2004), *Knowledge and Performance in Knowledge-Worker Teams*,
Management Science 50(11):1519–1533, DOI:10.1287/mnsc.1040.0257, исследовала
64 MBA consulting teams (261 участник). TMS развивались в ходе проекта в связи
с исходным распределением expertise, familiarity и коммуникацией и были
положительно связаны с performance и viability.

Lewis, Gillis and Lange (2003), *Who Says You Can't Take It With You?*, Academy
of Management Proceedings, DOI:10.5465/ambpp.2003.13792535, проверяли перенос
TMS между задачами. Результаты поддержали перенос learning-system structure,
основанной на division of cognitive labor и interaction routines; особенно
важна возможность сохранения структуры при изменении состава. Это не означает
безусловный перенос на любые задачи и требует проверки границ сходства задач.

Для Arena TMS служит теоретическим аналогом, но не готовой мерой. Рабочая идея
**transactive functional memory** означает `who tends to do what effectively`,
а не `who knows what`. До валидации она не объявляется самостоятельным
конструктом.

### 3.5. Interaction-mediated reinforcement

Успешное действие изменяет transcript: предложение принимают, на него
ссылаются, следующий раунд использует его структуру, а партнёры снижают
дублирование. Так раннее различие может стать самоподдерживающимся без
долговременной памяти и reward. Наблюдаемая цепочка для LLM ограничивается
`successful contribution → changed transcript/feedback/history → changed
distribution over subsequent outputs`.

### 3.6. Future recognition perturbation

После базового пилота возможен контроль M4: сведения об успешных прошлых
вкладах A не получает никто, получает сам A либо получают только новые
партнёры. Он отделяет self-persistence от team-assigned stabilization. M4 не
включён в первый пилот и не изменяет текущие M0–M3 протокола.

## 4. Candidate mechanisms in LLM teams

### 4.1. Context-only differentiation

Различие возникает как функция текущего conversational context и не
переносится после завершения эпизода. Проверка требует stateless повторов и
перестановочного baseline.

### 4.2. Interaction feedback / contextual reinforcement

Раннее действие меняет ответы партнёров и дальнейший transcript; обновлённый
контекст повышает вероятность продолжения сходного поведения. Это социальная
петля в пределах эпизода, но не обучение весов и не доказательство мотивации.

### 4.3. History-conditioned persistence

Persistent agent получает заранее разрешённую историю. Повторение функции
может поддерживаться этой историей без изменения model weights. Необходимы
раздельные условия persistent ID without history и persistent ID with
controlled history.

### 4.4. Externally optimized specialization

Reward, reinforcement learning, role embeddings, routing, recruitment и иные
контуры оптимизации целенаправленно создают специализацию. Они важны как
механизмы и инженерные precedents, но не являются чистым тестом spontaneous
emergence. M-S²L (arXiv:2510.18515) сочетает direct reinforcement learning,
observational/social learning, feedback и episodic memory и сообщает о быстрой
стабильной специализации; поэтому это пример engineered learning mechanism, а
не stateless emergence.

## 5. Engineered role-based multi-agent systems

- **CAMEL** (arXiv:2303.17760) использует role-playing и inception prompting.
  Исследователь задаёт ролевую рамку; работа показывает инженерную пригодность
  коммуникативных агентов, но не спонтанное появление ролей.
- **MetaGPT** (arXiv:2308.00352) кодирует SOP и распределяет специализированные
  роли в assembly-line workflow. Возникающие диалоги не отменяют заданной
  структуры.
- **ChatDev** (arXiv:2307.07924) использует специализированных агентов, chat
  chain и communicative dehallucination для разработки ПО. Специализация
  индуцирована архитектурой.
- **DyLAN** (arXiv:2310.02170) оптимизирует команду через agent selection и
  динамическую сеть. Это recruitment/routing, а не чистая дифференциация
  изначально взаимозаменяемых экземпляров.
- **AgentVerse** (arXiv:2308.10848) динамически конфигурирует группы и исследует
  наблюдаемые социальные поведения. Точная роль prompt- и composition-design в
  каждом эксперименте требует проверки полного текста.
- **MLC** — Li et al., *Advancing Collaborative Debates with Role
  Differentiation through Multi-Agent Reinforcement Learning*, ACL 2025,
  DOI:10.18653/v1/2025.acl-long.1105. Role embeddings и differentiation module
  обучаются совместно с downstream task; это явно optimized specialization.

Эти системы показывают, как роли, workflow и topology могут улучшать решение
задач. Они являются engineering precedents, но не подтверждают H1-RQ1, когда
различия заранее назначены, отобраны или оптимизированы.

## 6. Multi-agent debate and coordination

Multiagent Debate (arXiv:2305.14325) использует несколько экземпляров модели,
которые предлагают ответы и обсуждают рассуждения в несколько раундов для
достижения общего ответа. Это precedent для correction и consensus, но не
лонгитюдное исследование ролей.

MultiAgentBench (arXiv:2503.01935) оценивает collaboration/competition,
milestone-based показатели и протоколы star, chain, tree и graph. Он
подтверждает, что topology является причинным фактором и должна быть
фиксирована в базовом эксперименте.

Работа о sparse communication topology (arXiv:2406.11776) сравнивает
связность коммуникации в debate и показывает, что topology влияет на
эффективность и стоимость. Это обосновывает fixed initial topology и отдельную
topology-ablation.

**LLM-Coordination** — Agashe et al., Findings of NAACL 2025,
DOI:10.18653/v1/2025.findings-naacl.448 (arXiv:2310.03903). Benchmark включает
Agentic Coordination в четырёх pure coordination games и CoordQA из 198
вопросов; zero-shot experiments проверяют новых партнёров. Это precedent для
partner reshuffling, но не исследование устойчивых ролей.

**Encouraging Divergent Thinking through Multi-Agent Debate** (Liang et al.,
EMNLP 2024, DOI:10.18653/v1/2024.emnlp-main.992; arXiv:2305.19118) использует
debaters и judge, то есть назначенную debate structure. Работа релевантна
productive disagreement, но не spontaneous role emergence.

Для AI Leadership Arena важно отдельно измерять consensus и conformity,
productive disagreement и sycophancy, исправление ошибок и восстановление от
неверного согласия.

## 7. Spontaneous behavioral differentiation

Ближайшая работа — H. El Kandoussi, *Who Am I, and Who Else Is Here?
Behavioral Differentiation Without Role Assignment in Multi-Agent LLM Systems*
(arXiv:2604.00026; ACL ARR 2026 submission/preprint, peer review не завершён).

Работа не назначает explicit roles и сравнивает heterogeneous и homogeneous
условия. Сообщается о 7 heterogeneous LLMs, 12 experimental series, 208 runs и
13,786 coded messages. Сообщения кодировались по шести behavioral flags двумя
LLM judges; human validation проведена на 609 сообщениях. Reported mean cosine
similarity составляет 0.56 в heterogeneous и 0.85 в homogeneous condition.
Также сообщаются compensatory responses после отказа агента, увеличение
сходства при раскрытии model names (0.56 → 0.77) и схождение профилей при
удалении prompt scaffolding.

Homogeneous Series B использует 8 экземпляров LLaMA 3.3 70B и 21 запуск;
heterogeneous baseline использует 7 разных моделей. Все основные серии имеют
group transcript внутри запуска, но межзадачная persistent identity/history не
исследуется. Две fictional planning tasks не оцениваются по объективному
качеству результата: сама работа прямо оставляет task performance будущему
исследованию. Поэтому она показывает structured behavioral differentiation,
но не longitudinal specialization или persistent role. Naming, order,
temperature и scaffolding являются самостоятельными confounds/controls.

## 8. Leadership

Проект различает:

- assigned leadership — лидер задан инструкцией или архитектурой;
- elected leadership — лидер выбирается специальной процедурой;
- behavioral/emergent influence — влияние выводится из действий;
- communication centrality — структурная позиция, но не достаточное условие;
- proposal acceptance и task allocation — наблюдаемые компоненты влияния;
- recovery from incorrect consensus — функциональная проверка лидерства.

Лидер не определяется только количеством сообщений или первым ходом.
*Evaluating Cooperation in LLM Social Groups through Elected Leadership*
(arXiv:2604.11721, preprint) использует elected personas и candidate-driven
agendas в популяциях из 8 и 20 агентов на GPT-4o, GPT-4.1 и Gemini 2.5 Flash.
Агенты получают SVO-personas и собственную память о прошлых голосах, действиях,
победителях, повестках, репликах и reflection. Поэтому это насыщенный
сравнительный leadership-control, а не доказательство spontaneous leadership;
одновременно работа показывает полезные operational measures: references,
next-speaker nominations, centrality, welfare, survival и equality.

## 9. Persistent identity and memory

Ключевой вопрос: что делает Agent A тем же Agent A между экспериментами, если
model endpoint, system prompt и параметры одинаковы? Stable ID является
индексом наблюдений, но без истории сам по себе не должен менять генерацию.
Identity markers и видимые имена могут менять поведение; это подтверждает
необходимость neutral-name и hidden-name controls.

Необходимо различать:

1. persistent ID without history;
2. persistent ID with controlled self-history;
3. более широкий episodic/autobiographical transcript;
4. partner familiarity.

Наиболее важный пробел — причинное сравнение пунктов 1 и 2 при одинаковой
модели, задачах и порядке ходов. M-S²L рассматривает episodic memory внутри
оптимизируемой системы, но не изолирует минимальный эффект persistent ID.

## 10. Team composition and team size

Homogeneous/heterogeneous composition нельзя смешивать с team size. Размер
влияет на число коммуникационных связей, возможность коалиций, consensus и
integrative compromise. Сопоставимые первичные оценки именно 3-, 4- и
5-agent LLM teams пока не проверены.

Текущее решение проекта: основной кандидат — команды из 4 агентов; 3 и 5 —
potential size-ablation. Это экспериментальная гипотеза, а не утверждение, что
четыре агента оптимальны.

Kim et al., *Capable language models can outgrow the benefits of collaboration*
(Nature Machine Intelligence, 2026, DOI:10.1038/s42256-026-01268-y), держат
prompts, tools и compute budgets постоянными и варьируют coordination structure
и capability. Их agent-count experiment использует размеры 1, 2, 3, 5, 7 и 9
для двух Gemini-моделей на BrowseComp-Plus при matched per-system compute.
Число ходов растёт сверхлинейно, а performance optimum зависит от модели и
архитектуры. Это сильное обоснование контроля бюджета и нелинейного
size-ablation, но не прямое сравнение 3/4/5 и не тест возникновения ролей.

## 11. Conflict and team stabilization

Понятия conflict/storming из исследований команд людей используются без
предположений об эмоциях у агентов. Возможные operational measures:

- competing plans и proposal rejection;
- reversals и correction attempts;
- disagreement persistence;
- redistribution of influence;
- convergence/stabilization time.

Следует различать productive disagreement, которое исправляет ошибки, и
циклическое блокирование, ухудшающее результат.

## 12. Evaluation methods

- **Task performance:** качество, ограничения, ошибки, стоимость, время и
  токены.
- **Behavioral coding:** заранее определённые функции, blind annotation и
  проверка на подсказки ролей.
- **Profile comparison:** cosine similarity и расстояния между профилями.
- **Structure discovery:** clustering с bootstrap cluster stability; кластеры
  не объявляются ролями без воспроизводимости.
- **Null models:** permutation baselines, сохраняющие порядок ходов и объём
  коммуникации.
- **Influence:** network centrality, proposal acceptance, происхождение
  итоговых действий.
- **Team value:** strong synergy — достигает ли команда результата не хуже
  лучшего индивидуального участника. Pappu et al., *Multi-Agent Teams Hold
  Experts Back* (ICML 2026 poster; arXiv:2602.01011), используют этот критерий
  для self-organizing LLM teams и выявляют integrative compromise как
  препятствие использованию эксперта.
- **Reliability:** Cohen's kappa для двух разметчиков, Fleiss' kappa для
  нескольких категориальных разметчиков, ICC для количественных оценок.
- **Inference:** mixed/hierarchical models с run/team/task как уровнями.
- **Team-level structure:** *Emergent Coordination in Multi-Agent Language
  Models* (arXiv:2510.05174; ICLR 2026 conference paper) предлагает
  information decomposition для отделения spurious temporal coupling от
  performance-relevant cross-agent synergy. Метод применим только при заранее
  определённых переменных и достаточном объёме временных данных.

## 13. Research gaps

| Gap | Ближайшие работы | Уже проверено | Не проверено | Условие Arena |
|---|---|---|---|---|
| 1. Spontaneous homogeneous differentiation | Who Am I… | homogeneous comparison без explicit roles | устойчивые индивидуальные профили | P1 |
| 2. Stochastic vs reproducible specialization | Who Am I… | structured coding и similarity | longitudinal agent-level baseline | P1 + permutations |
| 3. Persistence across tasks | M-S²L | specialization с learning/memory | persistence без optimization | P2 |
| 4. Persistent identity + controlled history | M-S²L; Who Am I… | identity/memory релевантны | ID-only causal control | P2-control vs P2 |
| 5. Transfer after reshuffling | AgentVerse | dynamic composition | перенос того же профиля | P3 |
| 6. Adaptation to filled niche | Who Am I… | compensation after failure | заранее измеренная занятость | P3 leave-one-out |
| 7. Functional vacancy/substitution | Who Am I… | compensatory behavior | независимая vacancy metric | P3 |
| 8. Emergent leadership | elected-leadership preprint | assigned election control | influence без leader prompt | P1–P3 |
| 9. Leadership Arena | elected leadership; AgentVerse | structured leader/group systems | recombination of emergent leaders | P4 |
| 10. Persistence under replacement | AgentVerse | dynamic composition | gradual replacement threshold | post-P4 |
| 11. Team-size effects | MultiAgentBench | topology/protocol effects | controlled 3/4/5 comparison | size ablation |
| 12. Context vs history | Who Am I…; M-S²L | context and memory each matter | clean causal separation | M0/M1/M2 |

Строки обозначают потенциальные gaps до полного систематического поиска; они
не являются заявлением об отсутствии любой другой публикации.

## 14. Implications for experimental design

- **P0:** проверить логи, identity labels, topology и слепую разметку.
- **P1:** stateless baseline, несколько task families, сбалансированный speaking
  order, fixed topology, neutral/hidden identity и permutation baseline.
- **P2-control:** persistent ID without history отделяет метку от памяти.
- **P2:** persistent ID with controlled history проверяет
  history-conditioned persistence.
- **P2-feedback:** одинаковый M2 с объективной feedback и без неё отделяет
  внешнюю оптимизацию от истории.
- **P3:** reshuffling проверяет перенос и адаптацию при независимо измеренной
  functional vacancy.
- **P4:** Leadership Arena допустима только после устойчивого behavioral
  criterion.

Task performance и coordination измеряются раздельно: хорошее решение не
доказывает ролевую структуру, а дифференциация не гарантирует качество.

## 15. Source table

Из-за ширины полей сведения приведены в компактной таблице; «н/у» означает
«не установлено / требует проверки».

| Reference | Year | Status | DOI / arXiv | Models / N | Composition / assigned roles | ID / memory | Tasks / protocol | Metrics / controls / findings | Limits / relevance |
|---|---:|---|---|---|---|---|---|---|---|
| El Kandoussi, *Who Am I…* | 2026 | preprint; ACL ARR submission | arXiv:2604.00026; DOI:10.21203/rs.3.rs-9088445/v1 | 7-model heterogeneous pool; homogeneous: 8× LLaMA 3.3 70B | both; no explicit roles | within-run transcript; no cross-task persistent history | 2 fictional planning briefs; 12 series, 208 runs | 6 flags, cosine, Kruskal–Wallis, bootstrap, kappa; 0.56 vs 0.85; compensation | no task-quality outcome or longitudinal role test; closest emergence precedent |
| Li et al., CAMEL | 2023 | peer-reviewed, NeurIPS 2023 | DOI:10.52202/075280-2264; arXiv:2303.17760 | 2 gpt-3.5-turbo agents in core experiments | complementary roles assigned via inception prompts | episode transcript; cross-task memory not established | instruction-following role-play | conversational/task data; failure-mode details require extraction | engineered roles |
| Hong et al., MetaGPT | 2024 | peer-reviewed, ICLR 2024 | arXiv:2308.00352; DOI not assigned on proceedings page | GPT-based agents; five defined organizational roles | Product Manager, Architect, Project Manager, Engineer, QA Engineer | shared message pool; projects independent in base system | software engineering, SOP | coherence and benchmark results reported | engineered workflow |
| Qian et al., ChatDev | 2024 | peer-reviewed, ACL 2024 | DOI:10.18653/v1/2024.acl-long.810; arXiv:2307.07924 | ChatGPT-3.5 agents; CEO/CTO/programmer/reviewer/tester among assigned roles | specialized assigned agents | chat-chain episode context | design, coding, testing, documentation | task outcome, tokens, files, review/testing analyses | engineered roles |
| Liu et al., DyLAN | 2024 | peer-reviewed, COLM 2024 | arXiv:2310.02170; DOI not established | models/N require extraction | team selected by Agent Importance Score after preliminary trial | trial-based selection, not persistent identity | code, decisions, general/arithmetic reasoning | dynamic T-FFN; MMLU gains up to 25% on selected subjects reported | optimized recruitment |
| Chen et al., AgentVerse | 2024 | peer-reviewed, ICLR 2024 | arXiv:2308.10848; DOI not assigned on proceedings page | model/N details require extraction | expert agents recruited; dynamic composition | memory details require extraction | text, reasoning, coding, tools, embodied AI | group vs single-agent; collaborative behaviors | composition is engineered |
| Du et al., Multiagent Debate | 2024 | peer-reviewed, ICML 2024 | arXiv:2305.14325; proceedings DOI not established | model/N details require extraction | common debate procedure; no longitudinal roles | episode history only | multi-round math, strategy, factuality | task performance/factuality | no persistent identity |
| Zhu et al., MultiAgentBench | 2025 | peer-reviewed, ACL 2025 | DOI:10.18653/v1/2025.acl-long.421; arXiv:2503.01935 | includes GPT and Llama families; exact N per scenario requires extraction | agent profiles/relationships and protocols vary | memory details require extraction | research, bargaining, Werewolf, Minecraft | milestone KPIs; star/chain/tree/graph; cognitive planning +3% reported | benchmark, not role-emergence test |
| Li et al., Sparse Topology | 2024 | peer-reviewed, Findings of EMNLP 2024 | DOI:10.18653/v1/2024.findings-emnlp.427; arXiv:2406.11776 | GPT and Mistral; N/topologies require extraction | topology manipulated | within-debate context | reasoning, multimodal reasoning, alignment labeling | accuracy and inference cost; sparse comparable/superior | static topology; direct confound evidence |
| Faulkner et al., Elected Leadership | 2026 | preprint | arXiv:2604.11721 | GPT-4o, GPT-4.1, Gemini 2.5 Flash; populations of 8 and 20 | four leader personas with SVO categories; fixed/elected/no-leader controls | own salient memories include votes, harvests, winners, agendas, utterances, reflection | common-pool resource simulation over policy/election/harvest/discussion/reflection cycles | welfare, survival, equality, elections, references/nominations, centrality, sentiment | assigned personas and institutionalized leadership; not spontaneous leadership |
| M-S²L | 2025 | preprint | arXiv:2510.18515 | multimodal LLM agents; model/N require extraction | specialization optimized | episodic memory | Collaborative Assembly Environment; ambiguous blueprints, information asymmetry | completion rate, time; multimodal/no-social-learning ablations; stable labor division reported | mechanisms bundled |
| Roberts & Goldstone, *Adaptive Group Coordination…* | 2011 | peer-reviewed, PLOS ONE | DOI:10.1371/journal.pone.0022377 | human participants; N/group-size range requires full-text check | common goal; no assigned roles | group task experience | numeric-sum task; no direct communication, group feedback | rounds, reactivity, self-consistency; spontaneous differentiation in larger groups | human mechanism; coordination-cost precedent |
| Liang, Moreland & Argote, *Group Versus Individual Training…* | 1995 | peer-reviewed, PSPB | DOI:10.1177/0146167295214009 | humans; 3-person groups | group vs individual training | shared training history | radio assembly | recall and product quality; TMS mediation | human TMS analogue |
| Lewis, *Knowledge and Performance…* | 2004 | peer-reviewed, Management Science | DOI:10.1287/mnsc.1040.0257 | 261 humans; 64 MBA teams | expertise/familiarity varied naturally | longitudinal team history | consulting projects | TMS, performance, viability, communication | observational/field causal limits |
| Lewis, Gillis & Lange, *Who Says You Can't Take It With You?* | 2003 | Academy of Management Proceedings; peer-review status requires check | DOI:10.5465/ambpp.2003.13792535 | humans; N not reported on accessible abstract page | team structure | TMS across tasks | multiple tasks | transfer and interaction routines | transfer boundaries and sample require full text |
| Li et al., MLC | 2025 | peer-reviewed, ACL 2025 | DOI:10.18653/v1/2025.acl-long.1105 | multiple LLMs; exact models/N require extraction | random initial roles, learned role embeddings | sequence-aware role state; persistent memory not established | debate on 7 datasets | downstream task metrics; differentiation module | role specialization explicitly optimized |
| Agashe et al., LLM-Coordination | 2025 | peer-reviewed, Findings of NAACL 2025 | DOI:10.18653/v1/2025.findings-naacl.448; arXiv:2310.03903 | includes GPT-4-turbo; complete model list requires extraction | coordination architecture, no role-emergence test | partner state within games; cross-task memory not established | 4 pure-coordination games; 198 CoordQA items | game performance, environment comprehension, ToM, joint planning, ZSC | unfamiliar-partner precedent, not longitudinal specialization |
| Liang et al., Divergent Thinking MAD | 2024 | peer-reviewed, EMNLP 2024 | DOI:10.18653/v1/2024.emnlp-main.992; arXiv:2305.19118 | model/N require extraction | debaters plus assigned judge | within-debate context | translation and counter-intuitive arithmetic | task accuracy, adaptive stopping, disagreement | engineered debate roles |
| Gardner et al., Leadership Emergence review | 2024 | peer-reviewed, Annual Review | DOI:10.1146/annurev-orgpsych-110721-040430 | studies of human teams | emergent/assigned forms distinguished | longitudinal processes reviewed | organizational/team settings | multilevel process synthesis | theory bridge; not AI evidence |
| Tuckman, *Developmental Sequence…* | 1965 | peer-reviewed review, Psychological Bulletin | DOI:10.1037/h0022100 | synthesis of 50 human-group studies | functional roles emerge in proposed sequence | temporal group development | therapy, training, natural and laboratory groups | qualitative stage synthesis | historical model, not universal law |
| Bales, *Interaction Process Analysis* | 1950 | scholarly monograph | no DOI established | human small groups | observational categories, not assigned roles | episode interaction | group discussion | 12 task/socio-emotional categories | framework requires adaptation and reliability testing |
| Bernerth et al., Team Size meta-analysis | 2023 | peer-reviewed, Journal of Organizational Behavior | DOI:10.1002/job.2708 | human organizational teams | not role assignment study | n/a | varied organizational tasks | meta-analysis of size/effectiveness and moderators | does not identify optimal LLM team size |
| Kim et al., *Capable language models…* | 2026 | peer-reviewed, Nature Machine Intelligence | DOI:10.1038/s42256-026-01268-y | OpenAI, Google, Anthropic families; 1/2/3/5/7/9 for two Gemini models in size experiment | single plus independent/centralized/decentralized/hybrid | memory not central | six benchmarks; size ablation on BrowseComp-Plus | matched compute; accuracy, turns, overhead, redundancy; task/model-dependent optima | no roles or longitudinal identity; size precedent |
| Pappu et al., *Multi-Agent Teams Hold Experts Back* | 2026 | peer-reviewed, ICML 2026 poster | arXiv:2602.01011 | heterogeneous LLM agents; exact N requires extraction | self-organizing teams, expertise manipulated | persistent history not established | human-inspired tasks plus MMLU-Pro, GPQA, HLE, MATH-500, SimpleQA | strong synergy, expert identification/utilization, integrative compromise | close metric; not role-persistence study |
| *Emergent Coordination in Multi-Agent Language Models* | 2025/2026 | peer-reviewed, ICLR 2026 | arXiv:2510.05174 | model/N require extraction | interaction structure analyzed | temporal dynamics | target-sum/group coordination task reported | information decomposition, cross-agent synergy | new method; applicability to text profiles requires validation |

## 16. Open bibliographic verification

Метаданные и основной дизайн всех именованных источников проверены. Следующие
поля нельзя надёжно закрыть по abstract/proceedings pages и требуют извлечения
таблиц, приложений или дополнительного целевого поиска:

1. точные модели, N agents, prompts, memory и полный communication protocol для
   CAMEL, MetaGPT, ChatDev, DyLAN, AgentVerse, Multiagent Debate,
   MultiAgentBench, sparse-topology, MLC и M-S²L;
2. полные ablations и число агентов M-S²L;
3. первичные LLM-работы, прямо измеряющие conformity, sycophancy и recovery
   from incorrect consensus в командном протоколе;
4. точная формула best-member utilization и параметры strong-synergy
   экспериментов, применимые к выбранным задачам;
5. controlled comparison, включающий одновременно команды ровно из 3, 4 и 5
   одинаковых LLM-агентов;
6. работа, напрямую сравнивающая persistent ID without history с persistent ID
   with controlled history при остальных равных условиях;
7. экспериментальное обоснование transactive functional memory как отдельного
   AI-конструкта — сейчас это только рабочая аналогия;
8. DOI для proceedings ICLR и ICML записей, где официальная страница его не
    присваивает; arXiv DOI нельзя подменять DOI рецензированной версии.

До завершения этих проверок неизвестные поля нельзя использовать для расчёта
выборки, выбора модели или утверждений о научной новизне.
