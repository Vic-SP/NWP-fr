# NWP-fr
NeutralWikiPol-fr is an exploratory, fine-grained dataset designed to capture implicit, context-dependent semantic biases in French political biographies on Wikipedia.

## 📊 Dataset Structure
The dataset (`NeutralWikiPol-fr.txt`) is organized into three main components: Wikipedia raw metadata, Expert Annotations, and Bias Taxonomy. 

The tab-delimited columns are structured as follows:

The tab-delimited columns are structured in the following exact order:

| Column Name | Description |
| :--- | :--- |
| **Moderation Judgement** | The original Wikipedia moderator judgment (Neutral / Non-neutral). |
| **Targeted Statement** | The specific text excerpt extracted from Wikipedia based on moderator deletion rationales. |
| **Context Paragraph** | The surrounding paragraph providing necessary context for the targeted statement. |
| **Biographical Subject** | The political figure who is the subject of the biography. |
| **Biographical Summary** | The introductory summary of the candidate's biography. |
| **Edit Date** | The exact timestamp of the Wikipedia edit. |
| **Editor username** | The username of the Wikipedia contributor who made the edit. |
| **Annotator n°(x) judgment** | Five columns containing each annotator's judgement of a statement's neutrality. |
| **Annotator's Majority Vote** | The final aggregated judgment from the 5 political science experts (requires ≥ 3/5 agreement). |
| **Neutral Vote Ratio** | The exact proportion of experts who classified the statement as neutral. |
| **Non-neutral Vote Ratio** | The exact proportion of experts who classified the statement as non-neutral. |
| **ELB** | Binary indicator (0/1) for Explicit Linguistic Bias. Contains `"Null"` for neutral statements, as they are not concerned by bias categories. |
| **POV** | Binary indicator (0/1) for Point of View bias. Contains `"Null"` for neutral statements, as they are not concerned by bias categories. |
| **PDEI** | Binary indicator (0/1) for Promotional or Disqualifying Statements without Encyclopedic Interest. Contains `"Null"` for neutral statements, as they are not concerned by bias categories. |

## ⚙️ Technical Notes on Data Formatting
* **Paragraph Breaks:** Within the extracted text (Targeted Statements and Context Paragraphs), the `///` delimiter is used to explicitly indicate where a paragraph break occurred in the original Wikipedia source text.
* **Metadata & Attribution:** Unmodified Wikipedia metadata (`Editor username` and `Edit Date`) are strictly retained to fulfill the legal requirements of the CC BY-SA 4.0 license, ensuring that the original Wikipedia authors receive proper credit for their contributions.

## Wikipedia Content Extraction Protocol

To ensure the quality and relevance of our dataset, we manually filtered the samples using strict exclusion criteria:

* **Grammar and Style**: We isolated neutrality-focused revisions, excluding simultaneous changes such as formatting, spelling, or minor clarifications (e.g., expanding "Crémel affair" to "Nelly Crémel affair").

* **Vandalism**: Consistent with standard practices in neutrality research, we excluded blatant vandalism, including insults or crude edits (Recasens et al., 2013; Hube et al., 2018).

* **Source Misrepresentation**: We discarded revisions where the perceived bias stemmed from a misinterpretation of a cited reference (e.g., "biased extrapolation"). Evaluating these cases requires external context, whereas our dataset focuses strictly on intrinsic textual bias.

* **Non-Political Figures**: We excluded individuals whose primary notability lies outside the political sphere (e.g., comedians or business executives who ran for office but were not primarily active as politicians).

## Terms that indicate a lack of neutrality in the comments made by the Wikipedia editors

**Terms expressing explicitly neutrality or a lack of neutrality**

| Original (french) | Translation (english)|
| :--- | :--- |
| Caviardage | No translation: fraudulent or misleading alteration of an article |
| Conflit d'intérêt | Conflict of interest |
| Hagiographique | Hagiographic |
| Idéologique | Ideological |
| Neutralité | Neutrality |
| Objectivité | Objectivity |
| Orienté | Biased |
| Partialité | Partiality |
| Partisan | No translation: a way to describe a biased opinion |
| Péjoratif | Pejorative |
| Point de vue | Point of view |
| Promotionnel | Promotional |
| Publicitaire | Advertising |
| Sobriété | Sobriety |
| Subjectivité | Subjectivity |
| Trivialité | Triviality |

**Sentences expressing implicitly a lack of neutrality**

| Original (french) | Translation (english)|
| :--- | :--- |
| Un de ses amis le soutient ? Incroyable ! | One of his friends supports him? Unbelievable! |
| "Il a cependant", "a critiqué le caractère démagogique de". C'est Wikipédia on n'est pas là pour cirer les pompes. Les références sont là. |"However, he has", "he criticized the demagogic nature of". This is Wikipedia, we're not here to suck up. The references are there. |
| Le troisième élu au dernier reste, Aschieri était donc très loin d'être élu et pas "il manque de peu d'être élu". | The third seat was awarded via the last remainder, so Aschieri was very far from being elected and not "just short of being elected". |

## 'Ambiguously neutral sentences'

| **Original (french)** | **Translation (english)** | **Explanation** |
| :--- | :--- | :--- |
| Début 2016, le nouveau président du conseil régional de Nouvelle Aquitaine, le socialiste Alain Rousset, fait état d'un mauvais bilan financier de l'ancienne région Poitou-Charentes, déclarant que « c'est une région qui manifestait beaucoup de volontarisme et avait sans doute les yeux plus gros que le ventre par rapport aux capacités de financement ». Un audit commandé au cabinet EY et publié en avril 2016 confirme une « forte dégradation » de la situation financière de la région Poitou-Charentes sous la présidence de Ségolène Royal. L'étude relève des retards de paiements s'élevant à 132 millions d'euros et évoque une situation de quasi-banqueroute si la région n'avait pas été fusionnée avec l'Aquitaine et le Limousin en 2015. (...). | In early 2016, the new president of the Nouvelle-Aquitaine Regional Council, Socialist Alain Rousset, reported on the poor financial performance of the former Poitou-Charentes region, stating that “it was a region that showed a great deal of initiative but undoubtedly bit off more than it could chew in terms of its financing capacity.” An audit commissioned from EY and published in April 2016 confirmed a “sharp deterioration” in the financial situation of the Poitou-Charentes region under the presidency of Ségolène Royal. The study notes payment arrears totaling 132 million euros and suggests that the region would have been on the verge of bankruptcy had it not been merged with Aquitaine and Limousin in 2015. (...). | The accumulation of evidence that could be used to accuse the politician in question of financial mismanagement can be interpreted as a way to tarnish his or her image. | Lors du débat télévisé réunissant la totalité des candidats, il se distingue en citant la Constitution française, les traités de l'Union européenne, et en critiquant les emprunts bancaires des candidats favoris. Il précise que son parti n'a contracté aucun crédit et propose que les partis politiques ne puissent plus se financer auprès des banques, estimant que « ce sont les banques qui donnent après des instructions ». Un sondage visant à déterminer quel candidat a été perçu comme le plus convaincant lui attribue 3 % des suffrages. Les Décodeurs du Monde mettent en cause un « festival d'intox des candidats sur l'Europe lors du grand débat », et en particulier certaines affirmations de François Asselineau. Ce dernier déclare notamment à cette occasion que les traités européens poussent à la privatisation des services publics : selon Les Décodeurs, François Asselineau confond privatisation et libéralisation, cette dernière correspondant à la mise en concurrence des services publics avec des entreprises privées, à l'intérieur de secteurs d'activité précis (les services postaux, l'électricité et le gaz, le transport aérien, etc.) auparavant tous monopolistiques. Aussi, François Asselineau présente les grandes orientations des politiques économiques (GOPÉ) de la Commission européenne comme des directives que la France doit suivre impérativement, mais Les Décodeurs affirment qu'il s'agit de recommandations, non contraignantes. François Asselineau affirme également que la contribution nette de la France au budget de l'Union européenne (la contribution française à l'Union européenne diminuée des dépenses européennes accordées à la France) est de 9 milliards d'euros, alors que le calcul de cette contribution donne un résultat maximum de 6,1 milliards selon Les décodeurs. Ce chiffre est confirmé par RTBF, qui estime que de toute façon, le type de calcul proposé par Asselineau, purement comptable, a un intérêt limité. Ces contributions permettent en effet de faire progresser l'économie des pays les plus faibles, et ceux-ci sont alors susceptibles d'acheter du matériel aux pays les plus forts, ce qui, selon RTBF, complexifie l'équation simpliste d'Asselineau. | This content presents a collection of statements intended to promote the candidate. | En 2011, Florian Philippot déclare qu'il n'envisage pas une candidature ailleurs que dans le département du Nord, où il est né et a grandi. | In 2011, Florian Philippot stated that he did not plan to run for office anywhere other than in the Nord department, where he was born and raised. | This transcript of a speech by the politician helps promote his candidacy. |



# Experimental Prompts for NeutralWikiPol-fr Evaluation

This file contains the exact prompt templates used in the experimental benchmarking of state-of-the-art Large Language Models (LLMs) against human political science experts, as described in Section 5 (*Evaluation Protocol*/*Exploratory Experiments with LLMs*) of the paper.

## ⚙️ Experimental Parameters
To ensure transparency and address reproducibility constraints, the experiments were conducted under the following environmental settings:
* **Testing Period:** November 26, 2025, to December 2, 2025.
* **Evaluated Models:** DeepSeek-R1, Gemini 3, Grok 4, GPT-5.1, and Mistral Large 3.
* **Access Method:** Consumer web interfaces (as noted in the paper's limitations regarding strict API temperature controls).
