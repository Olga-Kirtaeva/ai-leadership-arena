# Literature Review: AI Leadership Arena

**Версия:** 0.1 — структурированный обзор до технической реализации  
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

## 2. Why roles emerge in human teams

Человеческая литература предлагает несколько совместимых объяснений:
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

Библиографические реквизиты первичных человеческих работ по emergent roles,
emergent leadership, task/socio-emotional differentiation и team development
в текущем контексте не установлены и требуют отдельной проверки. Человеческая
«мотивация» не переносится на LLM: для агента измеряются контекст, история,
feedback и изменение вероятности поведения, а не субъективное стремление.

## 3. Candidate mechanisms in LLM teams

### 3.1. Context-only differentiation

Различие возникает как функция текущего conversational context и не
переносится после завершения эпизода. Проверка требует stateless повторов и
перестановочного baseline.

### 3.2. Interaction feedback / contextual reinforcement

Раннее действие меняет ответы партнёров и дальнейший transcript; обновлённый
контекст повышает вероятность продолжения сходного поведения. Это социальная
петля в пределах эпизода, но не обучение весов и не доказательство мотивации.

### 3.3. History-conditioned persistence

Persistent agent получает заранее разрешённую историю. Повторение функции
может поддерживаться этой историей без изменения model weights. Необходимы
раздельные условия persistent ID without history и persistent ID with
controlled history.

### 3.4. Externally optimized specialization

Reward, reinforcement learning, role embeddings, routing, recruitment и иные
контуры оптимизации целенаправленно создают специализацию. Они важны как
механизмы и инженерные precedents, но не являются чистым тестом spontaneous
emergence. M-S²L (arXiv:2510.18515) сочетает direct reinforcement learning,
observational/social learning, feedback и episodic memory и сообщает о быстрой
стабильной специализации; поэтому это пример engineered learning mechanism, а
не stateless emergence.

## 4. Engineered role-based multi-agent systems

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
- **MLC:** точная публикация, расшифровка названия и экспериментальные условия
  по переданному контексту не установлены; утверждения о ней отложены.

Эти системы показывают, как роли, workflow и topology могут улучшать решение
задач. Они являются engineering precedents, но не подтверждают H1-RQ1, когда
различия заранее назначены, отобраны или оптимизированы.

## 5. Multi-agent debate and coordination

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

Для AI Leadership Arena важно отдельно измерять consensus и conformity,
productive disagreement и sycophancy, исправление ошибок и восстановление от
неверного согласия. Точная публикация под названием **LLM-Coordination**, а
также выбранная divergent-thinking работа в текущем контексте не установлены.
Zero-shot coordination with unfamiliar partners остаётся необходимым
направлением библиографической проверки.

## 6. Spontaneous behavioral differentiation

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

Homogeneous condition особенно важна: она ближе всего к проверке различий при
одинаковой модели. Однако основной сильный эффект относится к сравнению
heterogeneous/homogeneous composition. Работа показывает structured behavioral
differentiation, но не устанавливает longitudinal persistence одного agent ID
с controlled history. Behavioral differentiation не равна persistent role.
Naming и scaffolding являются самостоятельными confounds и controls.

## 7. Leadership

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
agendas. Это сравнительный leadership-control, а не доказательство spontaneous
leadership.

## 8. Persistent identity and memory

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

## 9. Team composition and team size

Homogeneous/heterogeneous composition нельзя смешивать с team size. Размер
влияет на число коммуникационных связей, возможность коалиций, consensus и
integrative compromise. Сопоставимые первичные оценки именно 3-, 4- и
5-agent LLM teams пока не проверены.

Текущее решение проекта: основной кандидат — команды из 4 агентов; 3 и 5 —
potential size-ablation. Это экспериментальная гипотеза, а не утверждение, что
четыре агента оптимальны.

## 10. Conflict and team stabilization

Человеческие понятия conflict/storming используются без предположений об
эмоциях. Возможные operational measures:

- competing plans и proposal rejection;
- reversals и correction attempts;
- disagreement persistence;
- redistribution of influence;
- convergence/stabilization time.

Следует различать productive disagreement, которое исправляет ошибки, и
циклическое блокирование, ухудшающее результат.

## 11. Evaluation methods

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
- **Team value:** strong synergy и best-member utilization; точные определения
  должны быть выбраны по первичному источнику.
- **Reliability:** Cohen's kappa для двух разметчиков, Fleiss' kappa для
  нескольких категориальных разметчиков, ICC для количественных оценок.
- **Inference:** mixed/hierarchical models с run/team/task как уровнями.
- **Team-level structure:** information-theoretic synergy только при заранее
  определённой переменной и достаточном объёме данных.

## 12. Research gaps

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

## 13. Implications for experimental design

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

## 14. Source table

Из-за ширины полей сведения приведены в компактной таблице; «н/у» означает
«не установлено / требует проверки».

| Reference | Year | Status | DOI / arXiv | Models / N | Composition / assigned roles | ID / memory | Tasks / protocol | Metrics / controls / findings | Limits / relevance |
|---|---:|---|---|---|---|---|---|---|---|
| El Kandoussi, *Who Am I…* | 2026 | preprint; ACL ARR submission | arXiv:2604.00026; DOI:10.21203/rs.3.rs-9088445/v1 | 7 heterogeneous models; homogeneous N н/у | both; no explicit roles | persistence/memory н/у | group discussions; 12 series | coding, cosine, kappa; 0.56 vs 0.85; failure compensation | no longitudinal role test; closest emergence precedent |
| Li et al., CAMEL | 2023 | preprint; later publication status н/у | arXiv:2303.17760 | models/N н/у | role-playing; assigned | н/у | instruction cooperation | performance details н/у | engineered roles |
| Hong et al., MetaGPT | 2023 | preprint; later status н/у | arXiv:2308.00352 | models/N н/у | heterogeneous assigned roles | н/у | software engineering, SOP | coherent solutions reported | engineered workflow |
| Qian et al., ChatDev | 2023 | preprint; later status н/у | arXiv:2307.07924 | models/N н/у | specialized assigned agents | н/у | software, chat chain | design/debug findings | engineered roles |
| Liu et al., DyLAN | 2023 | preprint; later status н/у | arXiv:2310.02170 | models/N н/у | selected team | trial-based selection | code, decisions, reasoning, arithmetic; dynamic network | optimized recruitment |
| Chen et al., AgentVerse | 2023 | preprint; later status н/у | arXiv:2308.10848 | models/N н/у | dynamic composition | н/у | collaborative tasks | group vs single-agent; social behaviors | conditions require full-text check |
| Du et al., Multiagent Debate | 2023 | preprint; later status н/у | arXiv:2305.14325 | models/N н/у | identical procedure; roles н/у | episode history only | multi-round debate; math/strategy/factuality | task performance | no persistent identity |
| Zhu et al., MultiAgentBench | 2025 | preprint; later status н/у | arXiv:2503.01935 | models/N н/у | protocols vary | н/у | interactive benchmark | milestones; star/chain/tree/graph | benchmark, not role-emergence test |
| Li et al., Sparse Topology | 2024 | preprint; later status н/у | arXiv:2406.11776 | GPT/Mistral; N н/у | topology manipulated | н/у | debate, multimodal/alignment | quality and cost | topology confound evidence |
| Faulkner et al., Elected Leadership | 2026 | preprint | arXiv:2604.11721 | models/N н/у | elected personas/agendas | enduring strategy details н/у | common-pool simulation | welfare, survival, centrality | assigned/elected control only |
| M-S²L | 2025 | preprint | arXiv:2510.18515 | models/N н/у | specialization optimized | episodic memory | tasks/protocol н/у | rapid stable specialization reported | mechanisms bundled |
| MLC | н/у | н/у | н/у | н/у | н/у | н/у | н/у | н/у | exact source unresolved |
| LLM-Coordination | н/у | н/у | н/у | н/у | н/у | н/у | unfamiliar-partner claim requires verification | н/у | exact source unresolved |

## 15. Open bibliographic verification

Требуют проверки по полным первичным текстам:

1. peer-reviewed status, venue и DOI для CAMEL, MetaGPT, ChatDev, DyLAN,
   AgentVerse, Multiagent Debate, MultiAgentBench и sparse-topology paper;
2. точные модели, N agents, prompts, memory и communication protocol почти во
   всех инженерных работах;
3. точный N homogeneous condition и longitudinal setup в *Who Am I…*;
4. точные задачи, число агентов и ablations M-S²L;
5. идентификация публикаций, обозначенных как MLC и LLM-Coordination;
6. выбор и проверка первичных работ по divergent thinking, conformity,
   sycophancy и zero-shot coordination;
7. первичные человеческие источники по emergent roles, emergent leadership,
   task/socio-emotional differentiation, team development, size и conflict;
8. первичные определения strong synergy, best-member utilization и
   information-theoretic synergy;
9. сопоставимые исследования команд из 3, 4 и 5 LLM-агентов;
10. наличие работ, напрямую сравнивающих persistent ID without history с
    persistent ID with controlled history.

До завершения этих проверок неизвестные поля нельзя использовать для расчёта
выборки, выбора модели или утверждений о научной новизне.
