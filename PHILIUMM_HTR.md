# Installation

Pour éviter tout soucis d'installation (pour les utilisateurs Windows ou de certaines distributions Linux), on fournit un [notebook Colab](https://colab.research.google.com/drive/1dMvd0vr-Owg6MUeVhxWr2EylcE6RZSAg?usp=sharing) (exécutable à condition de disposer d'un compte Google). Autrement, on se réfère à la procédure d'installation décrite par Denisa Bumba sur [gitlab](https://gitlab.com/eman8/scripts/scripts-pour-le-pretraitement-des-corpus-sur-EMAN/gestion_resultats_htr-ocr/-/tree/main/eScriptorium_postprocessing_pipeline?ref_type=heads).


# Rapides rappels des résultats des précédentes campagnes d'évaluations

Pour une description exhaustive et schématique de la chaîne de traitement, on consultera avec profit [la pipeline datée du 13 janvier 2026](https://groupes.renater.fr/wiki/eman/_media/prive/htrleibniz/pipeline_leibniz_13-01-2026.pdf) et, plus généralement, [les carnets de tests suivants](https://groupes.renater.fr/wiki/eman/prive/htrleibniz/chaine_de_traitement_pour_l_augmentation_de_la_verite_terrain_et_l_amelioration_des_modeles_htr). Pour des ressources complémentaires, cf. la page sur le [wiki Renater](https://groupes.renater.fr/wiki/eman/prive/htrleibniz/ressources). Dans ce document, on ne s'intéresse qu'à la partie HTR (et très légèrement à la partie HMER ci-après).

Bien que des résultats assez impressionnants aient pu être obtenus avec des grands modèles de langue généralistes (avec Claude dernier du nom (juin 2026) par Matthew McMillan, Qwen 3.7 plus...), la priorité est donnée à de _petits_ modèles spécialisés (Kraken, FoNDUE-GD) finetunés ou non. Une première étape de segmentation est nécessaire, elle est suivie d'une étape de transcription par ces modèles (présentés ci-après). On procède classiquement en évaluant le résultat d'un modèle contre une vérité de terrain produite spécialement pour l'occasion et vérifiée (voir ci-après l'annexe _Corpus : vérité de terrain certifiée_ pour avoir accès à quelques unes des pages utilisées comme vérité de terrain; de surcroît, un millier de pages supplémentaires pourraient être obtenues si un bon algorithme d'alignement est mis en place; voir les [protocoles de transcription](https://groupes.renater.fr/wiki/eman/prive/htrleibniz/principes_de_relecture_03-12-2025)). Des [statistiques des donneés de terrain](https://groupes.renater.fr/wiki/eman/prive/htrleibniz/statistiques_de_la_verite_de_terrain) sont disponibles.

De plus, un module de calcul de CER/WER a été fait par D.-F. Bumba et intégré dans `eScriptorium_postprocessing_pipeline` (présenté dans la partie installation ci-avant) utilisant `tecquel` et `pywer`.

# Quels modèles évaluer ?
1. FoNDUE-GD_v2.mlmodel = modèle entraîné sur l'ensemble des langues
2. FoNDUE-GD_v2_fr.mlmodel = il s'agit du modèle FoNDUE-GD_v2.mlmodel fine-tuné sur des textes en français
3. FoNDUE-GD_v2_la.mlmodel = il s'agit du modèle FoNDUE-GD_v2.mlmodel fine-tuné sur des textes en latin
4. version_15
5. version_22
6. german_handwriting_fine-tune_BerlinGT_v1.2 (peut être exclus, considéré comme sous-performant; mais corrigé & utilisé pour la vérité terrain).

À cela s'ajoutent deux fine-tuning produits par D.-F. Bumba lors da la fin du mois de juin. Leurs performances semblent néanmoins, au premier coup d'oeil, bien inférieures à ce dont nous disposions précedemment. De plus, parallèlement à ces modèles _lightweights_, de rapides tests employant des vLLM ont été conduits.
Noter que pour chacun des tests, la segmentation est réputée être de confiance.

# Ré-évaluation des modèles, détections d'aberrations (scores faussés)

# Détection et identification des erreurs produites par les modèles

# Reconstruction textuelle à partir de plusieurs transcriptions, _take the best leave the worst_

# Quelques compléments LLM

# Quelques compléments vLLM

# Quelques tests d'alignement

L'objectif des travaux d'alignement est le suivant : étant donné que l'on dispose d'un PDF contenant une transcription (avec apparat critique) réalisé par des experts, il est souhaitable de pouvoir réutiliser ce travail en le calquant ligne à ligne sur (environ?) un millier de folios. Ainsi, on récupérerait un millier de pages de vérité de terrain. Pour ce faire, la stratégie est la suivante (étant donné que les textes ne sont pas déjà alignés (même faiblement) : générer une transcription automatique avec un modèle présentant un niveau de confiance suffisant, calculer les appariements textuels pour pouvoir remplacer (lorsque c'est nécessaire) la transcription générée de la ligne par la vérité de terrain.

Les grands essais d'alignement se sont fondés sur [passim](https://github.com/dasmiq/passim). D'autres essais ont été faits en réemployant et détournant l'utilisation de `sentence-transformers/all-MiniLM-L6-v2`. Les résultats ne sont pas concluants quoiqu'ils restent encourageants.

TESTS ENCORE À FAIRE!!!!


# Annexes 

## Corpus (vérité de terrain certifiée)

Version au 29 juin 2026.

| Date | column_2 | Source | Segmentation corrected | N image | Author | Difficulty level | Time for correction | Base model | Annotation notes | Alignement | Author_2 | Language | HTR corrected | Difficulty level_2 | Time for HTR text correction | HTR model or ALIGN | Correction notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | VI-4 | Test modèle "blla" sur des échantillons de Leibniz |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 07-01-2026 |  | LH_1_2_1 | LH_1_2_1_0004r.jpg | 1 | Denisa | Easy | 40-50 min | blla.mlmodel |  | Yes | Denisa | lat | Yes | Difficult | 1h10 | passim_best |  |
|  |  |  | LH_1_2_1_0004v.jpg | 2 | Denisa | Easy | 40-50 min | blla.mlmodel |  | Yes |  |  |  |  |  | passim_best |  |
|  |  |  | LH_1_2_1_0005r.jpg | 3 | Denisa | Easy | 40-50 min | blla.mlmodel |  | Yes |  |  |  |  |  | passim_best |  |
|  |  |  | LH_1_2_1_0027r.jpg | 5 | Denisa | Difficult | 50-60 min | blla.mlmodel |  | Yes |  |  |  |  |  | passim_best |  |
|  |  | LH_1_3_4 | LH_1_3_4_0011r-0010v.jpg | 9 | Denisa | Easy | 40 min | blla.mlmodel |  | Yes |  |  |  |  |  | passim_best |  |
|  |  | LH_4_6_12a | LH_4_6_12a_0001v.jpg | 37 | Denisa | Easy | 30 min | blla.mlmodel |  | Yes |  |  |  |  |  | passim_best |  |
|  |  | Fine-tuning "test-train-1" model |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 08-01-2026 |  | Test modèle "test-train-1" sur des échantillons similaires |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  | LH_1_2_1 | LH_1_2_1_0025r-0024v.jpg | 4 | Denisa | Difficult | 27 min | test-train-1.mlmodel | double page,additions | Yes |  |  |  |  |  | passim_best |  |
|  |  | LH_1_3_1 | LH_1_3_1_0008v-0007r.jpg | 7 | Denisa | Very difficult | 50 min | test-train-1.mlmodel | double page, additions, lines span over the margin zone, zones difficult to correct | Yes | Audrey | fr |  |  |  | passim_best |  |
|  |  | LH_1_3_4 | LH_1_3_4_0008r-0007v.jpg | 8 | Denisa | Easy | 30 min | test-train-1.mlmodel | double page, lines tend to go up and down, difficult to have a straight line | Yes | Denisa | lat | Yes | Difficult | ? | passim_best |  |
|  |  | LH_1_3_5 | LH_1_3_5_0024v-0023r.jpg | 10 | Denisa | Easy | 20 min | test-train-1.mlmodel | double page, margin notes, cleaner format | Yes | Sébastien | fr |  |  |  | passim_best |  |
|  |  | LH_1_3_7_A | LH_1_3_7_A_0004v-0003r.jpg | 11 | Denisa | Easy | 8 min | blla.mlmodel | double page (left page empty), writing that tends to go slightly up, so the lines are cut in small segments | Yes | Denisa | lat | Yes | Easy | 1h | passim_best | l.52 (il manque le début de la ligne dans l'éd. critique) ; pas sûre d'avoir bien transcrit |
|  |  | LH_1_3_7_D | LH_1_3_7_D_0002v-0001r.jpg | 13 | Denisa | Difficult | 35 min | test-train-1.mlmodel | double page, correcting the zones took more time | Yes |  |  |  |  |  | passim_best |  |
|  |  | LH_1_4_4 | LH_1_4_4_0001v.jpg | 17 | Denisa | Easy | 8 min | test-train-1.mlmodel | simple page, baselines already pretty well detected. Sometimes lines are segmented when the writing goes up a little. | Yes |  |  |  |  |  | passim_best |  |
|  |  | Fine-tuning "test-train-2" model |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  | Test modèle "test-train-2" sur des échantillons similaires |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 09-01-2026 |  | LH_1_3_1 | LH_1_3_1_0003r-0002v.jpg | 6 | Denisa | Difficult | 37 min | test-train-2.mlmodel | double page, the new model is better at recognising long, tilted lines without spliting them in several segments. I noticed that the model fine-tuned on eScriptorium does not recognise the InterlinearLine type of lines at all... and recognizes less than before. I should test the local fine-tuning and check if adding classes is allowed. | Yes | Audrey | fr | En cours |  |  | align_clean_no_app_lev_0.4 |  |
|  |  | LH_1_3_7_C | LH_1_3_7_C_0001.jpg | 12 | Denisa | Very difficult | 60 min | test-train-2.mlmodel | double page, the zones are almost overlapping. It took time to correct the zones. Many margin notes. | Yes |  |  |  |  |  | passim_best |  |
|  |  | LH_1_4_1 | LH_1_4_1_0001r.jpg | 14 | Denisa | Easy | 10 min | test-train-2.mlmodel | double page, less lines, easy layout. Almost perfect line detection on this page. | Yes | Denisa | lat | Yes | Easy | 1h | passim_best |  |
|  |  | LH_1_4_7 | LH_1_4_7_0015v-0014r.jpg | 20 | Denisa | Very difficult | 63 min | test-train-2.mlmodel | double page, many margin lines, different character sizes. | Yes | Mathias | fr | Yes | Difficult | 2h | passim_best | Problèmes de masks + une partie substantielle de la transcription manquait (faite de zéro) |
|  |  | Fine-tuning "test-train-3" model |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  | Test modèle "test-train-3" sur des échantillons similaires |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 12-01-2026 |  | LH_1_4_3 | LH_1_4_3_0004r-0003v.jpg | 16 | Denisa | Easy | 20 min | test-train-3.mlmodel | double page, very good segmentation for main lines, less good for the addition lines | Yes |  | lat |  |  |  | passim_best |  |
|  |  |  | LH_1_4_3_0002v-0001r.jpg | 15 | Denisa | Easy | 5 min | test-train-3.mlmodel | double page, almost perfect segmentation (both zones and lines), some addition lines not detected | Yes |  | lat |  |  |  | passim_best |  |
|  |  | LH_1_4_7 | LH_1_4_7_0012v-0011r.jpg | 19 | Denisa | Easy | 7 min | test-train-3.mlmodel | double page, almost perfect, added some missing addition lines | Yes | Florian | fr | Yes | Easy | 1h | passim_best |  |
|  |  | LH_1_4_8 | LH_1_4_8_0016r-0015v.jpg | 21 | Denisa | Easy | 15 min | test-train-3.mlmodel | double page, almost perfect, added some missing addition lines | Yes |  | fr |  |  |  | passim_best |  |
|  |  | LH_1_6_2 | LH_1_6_2_0002v-0001r.jpg | 22 | Denisa | Easy | 10 min | test-train-3.mlmodel | double page, almost perfect, added some missing addition lines | Yes |  | lat |  |  |  | passim_best |  |
|  |  | LH_1_6_4 | LH_1_6_4_0002r-0001v.jpg | 23 | Denisa | Very easy | 5 min | test-train-3.mlmodel | double page, no margin notes, ink with low contrast | Yes |  | fr |  |  |  | passim_best |  |
|  |  | LH_1_6_5 | LH_1_6_5_0002v-0001r.jpg | 24 | Denisa | Very difficult | 14 min | test-train-3.mlmodel | double page, margin note zone as large as main zone on the left page, low contrast ink, uppercase letter that are very large | Yes | Florian | fr | Yes | Very easy | 45mn | passim_best |  |
|  |  | LH_1_6_6 | LH_1_6_6_0002v-0001r.jpg | 25 | Denisa | Very difficult | 45 min | test-train-3.mlmodel | double page, margine note lines very close to the main zone, sometimes overlapping with the main zone. We decided not to cut too much into the mainzone (right page) -> review this decision later. | Yes |  | lat |  |  |  | passim_best |  |
|  |  | Fine-tuning "test-train-4" model |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  | Test modèle "test-train-4" sur des échantillons similaires |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 13-01-2026 |  | LH_1_6_11 | LH_1_6_11_0002r-0001v.jpg | 26 | Denisa | Easy | 8 min | test-train-4.mlmodel | double page, almost perfect, few lines missed | Yes |  |  |  |  |  | passim_best |  |
|  |  | LH_1_7_5 | LH_1_7_5_0065r-0064v.jpg | 27 | Denisa | Easy | 8 min | test-train-4.mlmodel | double page, almost perfect segmentation, this time we went into details, adjusting the baselines starting with uppercase letter | Yes |  |  |  |  |  | passim_best |  |
|  |  | LH_1_7_6 | LH_1_7_6_0043r-0042v.jpg | 28 | Denisa | Easy | 15 min | test-train-4.mlmodel | double page, very good segmentation, corrected some addition lines and some baselines | Yes |  |  |  |  |  | passim_best |  |
|  |  | LH_1_20 | LH_1_20_0065v-0064r.jpg | 29 | Denisa | Very difficult | 53 min | test-train-4.mlmodel | double page, a lot of margin notes, close to the main zone, and a lot of additions | Yes | Mathias | fr | Yes | Medium | 1h30 | passim_best |  |
| 16-01-2026 |  |  | LH_1_20_0111v-0110r.jpg | 30 | Denisa | Very difficult | 50 min | test-train-4.mlmodel | double page, vertical lines on the margins of the left page | Yes |  |  |  |  |  | passim_best |  |
| 09-02-2026 |  |  | LH_1_20_0164v-0163r.jpg | 31 | Denisa | Easy | 15 min | blla.mlmodel | double page, vertical lines, quotation marks distanced from the text lines, few additions | Yes |  |  |  |  |  | passim_best |  |
|  |  |  | LH_1_20_0287v-0284r.jpg | 32 | Denisa | Easy | 10 min | blla.mlmodel | double page, fade ink | Yes |  |  |  |  |  | passim_best |  |
| 10-02-2026 |  | LH_2_3_1 | LH_2_3_1_0051r-0050v.jpg | 33 | Denisa | Difficult | 25 min | test-train-4.mlmodel | double page, fade ink in some parts, lots of small additions, vertical lines | Yes |  |  |  |  |  | passim_best |  |
|  |  |  | LH_2_3_1_0054r-0053v.jpg | 34 | Denisa | Easy | 15 min | test-train-4.mlmodel | double page, margin notes and small addition lines | Yes |  |  |  |  |  | passim_best |  |
|  |  | Fine-tuning "test-train-5" model (⚠️ this model is a model trained from scratch, we will continue to use test-train-4) |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  | Test modèle "test-train-5" sur des échantillons similaires |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  | LH_2_3_1 | LH_2_3_1_0058r-0057v.jpg | 35 | Denisa | Very difficult | 45 min | test-train-4.mlmodel | double page, very small letters, small addition lines, some zones are difficult to delimitate | Yes |  |  |  |  |  | passim_best |  |
| 12-02-2026 |  | LH_4_1_4d | LH_4_1_4d_0002r-0001v.jpg | 36 | Denisa | Difficult | 12 min | test-train-4.mlmodel | double page, with crossed over lines and additional lines that are illegible | Yes |  |  |  |  |  | passim_best |  |
| 19-02-2026 |  | LH_1_4_7 | LH_1_4_7_0012r-0011v.jpg | 18 | Denisa | Easy | 15 min | test-train-5.mlmodel | double page, part of the text on the first page is erased, small interlinear additions | Yes | Florian | fr | Yes | Medium | 2h | passim_best |  |
| 28-05-2026 |  | LH_1_1_4 | LH_1_1_4_0072r.jpg | 38 | Denisa | Easy | 2 min | blla.mlmodel |  |  |  | lat |  |  |  | passim_best |  |
|  |  | LH_1_2_1 | LH_1_2_1_0001r.jpg | 39 | Denisa | Difficult | 35 min | fine-tuned-model_best | a lot of crossed-over passages that are illegible |  |  | lat |  |  |  | passim_best |  |
|  |  |  | LH_1_2_1_0002r.jpg | 40 | Denisa | Difficult | 28 min | fine-tuned-model_best |  |  |  | lat |  |  |  | passim_best |  |
| 22-06-2026 |  | LH_1_3_1 | LH_1_3_1_0001v.jpg | 93 | Rui |  |  | best_0.4006 |  | Yes | Rui | fr | En cours |  |  | passim_best |  |
|  |  | LH_1_3_1 | LH_1_3_1_0003v-0002r.jpg | 94 | Rui |  |  | best_0.4006 |  |  |  | fr |  |  |  |  |  |
| 10-03-2026 | VIII-1 | LH_4_8 | LH_4_8_0073r-0072v.jpg | 1 | Denisa | Easy | 5 min | test-train-4.mlmodel | double page, few lines | Yes | Denisa | lat, ge | Yes | Easy | 15 min | align_all_lev_0.4 | Did not transcribe lines in German, difficult to make the correspondance. |
|  |  | LH_4_8 | LH_4_8_0073v-0072r.jpg | 2 | Denisa | Very difficult | > 1h | test-train-4.mlmodel | double page, many (long) lines | Yes | Denisa | lat, ge, fr, en | Yes | Very difficult | > 3 hrs | align_all_lev_0.4 | l.32 "machina 1000 tonnen" : not sure of the transcription inside the () l. 285 "[[]] in △  communi crescit injecto certo sale, et" : not sure of the transcription of communi |
|  |  | LH_35_3A | LH_35_3A_8_0027r.jpg | 3 | Denisa | Easy | 15 min | test-train-4.mlmodel | single pages, very segmented lines | Yes | Denisa | fr, ge, lat | Yes | Easy | 30 min | align_clean_lev_0.4 |  |
|  |  | LH_35_5_2 | LH_35_5_2_0006r-0005v.jpg | 5 | Denisa | Very difficult | > 1h | test-train-4.mlmodel | double page, very difficult, with a lot of fractions and mixed of complex and simple maths, many elements of the layout to correct as well, vertical text... | Yes | Denisa | lat | Yes | Very difficult | 4 hrs | passim_best | We did not correct the lines in the margin on the left page, it was too complicated. We will delete all empty lines before training. This pages needs a second review. |
| 11-03-2026 |  |  | LH_35_5_2_0006v-0005r.jpg | 6 | Denisa | Difficult | 40 min | test-train-4.mlmodel | double page, with maths -> review later the segmentation of lines containing fractions | Yes |  | lat |  |  |  | passim_best |  |
|  |  |  | LH_35_5_2_0008r-0007v.jpg | 7 | Denisa | Difficult | 30 min | test-train-4.mlmodel | double page, with maths -> review later the segmentation of lines containing fractions | Yes |  | lat |  |  |  | passim_best |  |
|  |  |  | LH_35_5_2_0008v-0007r.jpg | 8 | Denisa | Easy | 13 min | test-train-4.mlmodel |  | Yes | Denisa | lat | Yes | Easy | 25 min | passim_best | review l.26 (intersection symbol ?) : non, c'est un symbole de la multiplication, il est correct : ⌣ (U+2323) |
|  |  |  | LH_35_5_2_0009r.jpg | 9 | Denisa | Easy | 13 min | test-train-4.mlmodel |  | Yes | Denisa | lat | Yes | Easy | 25 min | passim_best |  |
|  |  | LH_35_12_1 | LH_35_12_1_0327r.jpg | 10 | Denisa | Easy | 15 min | test-train-4.mlmodel |  | Yes | Denisa | lat | Yes | Easy | 30 min | passim_best |  |
|  |  | LH_35_12_2 | LH_35_12_2_0156r-0155v.jpg | 11 | Denisa | Easy | 30 min | test-train-4.mlmodel |  | Yes |  | lat |  |  |  | passim_best |  |
| 12-03-2026 |  |  | LH_35_12_2_0156v-0155r.jpg | 12 | Denisa | Difficult | 40 min | test-train-4.mlmodel | double page, with maths and graphiczones. | Yes |  | lat |  |  |  | passim_best |  |
| 16-03-2026 |  | LH_35_14_2 | LH_35_14_2_0099v-0098r.jpg | 13 | Denisa | Difficult | 45 min | test-train-4.mlmodel | double page, ink with low contrast | Yes | Denisa | lat | Yes | Difficult | > 4 hrs | passim_best | l. 79 abbréviation : contra -> con = 9 ; cette abréaviation revient souvent dans ce texte. reprendre à partir de la l. 101 |
| 17-03-2026 |  |  | LH_35_14_2_0101v-0100r.jpg | 14 | Denisa | Difficult | 1h10 | test-train-4.mlmodel | 4 columns, a lot of lines to correct, low contrast ink | Yes | Denisa | lat | Yes | Difficult | 1h50 | passim_best |  |
|  |  |  | LH_35_14_2_0131v-0130r.jpg | 15 | Denisa | Easy | 22 min | test-train-4.mlmodel |  | Yes | Denisa | lat | Yes | Easy | 30 min | passim_best |  |
|  |  |  | LH_35_14_2_0133v-0132r.jpg | 16 | Denisa | Easy | 35 min | test-train-4.mlmodel |  | Yes | Denisa | lat | Yes | Easy | 1h | passim_best |  |
| 18-03-2026 |  | Fine-tuning "fine-tuned-model_best" model |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  | Test modèle "fine-tuned-model_best" sur des échantillons similaires |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| 23-03-2026 |  | LH_35_14_2 | LH_35_14_2_0134v-0129r.jpg | 17 | Denisa | Easy | 15 min | fine-tuned-model_best |  | Yes | Denisa | lat | Yes | Easy | 1h | passim_best |  |
| 20-04-2026 |  | LH_35_15_1 | LH_35_15_1_0014r.jpg | 18 | Denisa | Easy | 9 min | fine-tuned-model_best | simple page, over segmented baselines | Yes | Audrey | fr | Yes | Easy | 20min | passim_best |  |
|  |  |  | LH_35_15_1_0017r.jpg | 19 | Denisa | Easy | 8 min | fine-tuned-model_best | simple page, over segmented baselines | Yes | Audrey | fr | Yes | Easy |  | passim_best |  |
|  |  | LH_35_15_6 | LH_35_15_6_0021r.jpg | 20 | Denisa | Easy | 7 min | fine-tuned-model_best |  | Yes | Denisa | fr | Yes | Easy | 15 min | passim_best |  |
|  |  |  | LH_35_15_6_0024r.jpg | 21 | Denisa | Easy | 9 min | fine-tuned-model_best |  | Yes | Denisa | lat | Yes | Easy | 1h | passim_best |  |
|  |  |  | LH_35_15_6_0046v.jpg | 22 | Denisa | Difficult | 15 min | fine-tuned-model_best |  | Yes |  | lat |  |  |  | passim_best |  |
| 28-05-2026 |  |  | LH_35_15_6_0048r-0047v.jpg | 23 | Denisa | Easy | 19 min | fine-tuned-model_best |  | Yes | Denisa | lat | Yes | Medium | 2h | passim_best |  |
|  |  |  | LH_35_15_6_0048v-0047r.jpg | 24 | Denisa | Easy | 10 min | fine-tuned-model_best |  | Yes |  |  |  |  |  | passim_best |  |
| 15-06-2026 |  | LH_35_15_6 | LH_35_15_6_0056r.jpg | 31 | Denisa | Easy | 11 min | fine-tuned-model_best | all baselines oversegmented, even with our best segmentation model | Yes |  | lat |  |  |  | passim_best |  |
|  |  |  | LH_35_15_6_0057r.jpg | 32 | Denisa | Easy | 5 min | fine-tuned-model_best |  | Yes |  | lat |  |  |  | passim_best |  |
|  |  |  | LH_35_15_6_0063v.jpg | 34 | Denisa | Easy | 6 min | fine-tuned-model_best |  | Yes |  | lat |  |  |  | passim_best |  |
| 18-06-2026 |  | LH_37_2 | LH_37_2_0101r.jpg | 38 | Denisa | Easy | 25 min | fine-tuned-model_best |  | No |  | lat |  |  |  |  |  |
|  |  | LH_37_4 | LH_37_4_0071r.jpg | 39 | Denisa | Very easy | 12 min | fine-tuned-model_best | /!\ encre qui traverse la page | No |  | lat |  |  |  |  |  |
| 19-06-2026 |  |  | LH_37_4_0071v.jpg | 40 | Denisa | Very easy | 3 min | fine-tuned-model_best | /!\ encre qui traverse la page | No |  | lat |  |  |  |  |  |
|  |  | LH_38 | LH_38_0018v-0017r.jpg | 42 | Denisa | Easy | 20 min | fine-tuned-model_best |  | No |  | lat |  |  |  |  |  |
| 04-06-2026 | Corpus Audrey | LH_35_4_12 | 5r.jpg | 1 | Audrey | Easy | 15 min | fine-tuned-model_best | only the right page | Yes | Audrey | fr | Yes | Very easy |  | passim_best |  |
|  |  | LH_35_4_12 | 9r.jpg | 2 | Audrey | Easy | 30 min | fine-tuned-model_best | simple page | Yes | Audrey | fr | Yes | Easy |  | passim_best |  |
|  |  | LH_35_4_12 | 9v.jpg | 3 | Audrey | Easy | 10 min | fine-tuned-model_best | only the right page | Yes | Audrey | fr | Yes | Very easy |  | passim_best |  |
|  |  | LH_35_11_8 | LH_35_11_8_0002r.jpg | 1 |  |  |  |  |  |  | Florian | fr | Yes | Very easy |  | kraken:version_22 |  |
|  |  | LH_4_5_10 | LH_4_5_10_11r.jpg | 2 |  |  |  |  |  |  | Florian | fr | Yes | Very easy |  | kraken:version_22 | Probables soucis avec les symboles mathématiques |
|  |  | LH_4_5_10 | LH_4_5_10_11v.jpg | 3 |  |  |  |  |  |  | Florian | fr | Yes | Very easy |  | kraken:version_22 | Probables soucis avec les symboles mathématiques |
|  |  | LH_4_5_10 | LH_4_5_10_25r.jpg | 10 |  |  |  |  |  |  | Mathias | fr | Yes | Very easy |  | kraken:version_22 |  |
| 18-06-2026 | Leibniz_french_corpus | LH_4_5_10 | LH_4_5_10_25v.jpg | 11 |  |  |  |  |  |  | Mathias | fr | Yes | Very easy |  | kraken:version_22 |  |
| 29-04-2026 | Transcribathon | LH_1_20 | LH_1_20_0063r-0062v.jpg | 1 (doc16) | Audrey | - | - | fine-tuned-model_best | - | HTR | Audrey | fr | Yes | - | - | FoNDUE-GD_v2_fr |  |
|  |  |  | LH_1_20_0063v-0062r.jpg | 1 (doc16) | Audrey | - | - | fine-tuned-model_best | - | No | - | fr |  | - | - |  |  |
|  |  | LH_2_3_3 | LH_2_3_3_0017r.jpg | 1 (doc7) | Clélia CRIALESI | - | - | fine-tuned-model_best | - | HTR | Clélia CRIALESI | lat | Yes | - | - | manual | ne pas inclure, texte beaucoup trop compliqué avec uniquement des références à d'autres auteurs, oeuvres d'art... mais bon pour la segmentation |
|  |  |  | LH_2_3_3_0022r.jpg | 2 (doc 7) | Clélia CRIALESI | - | - | fine-tuned-model_best | - | No |  | lat |  |  |  |  |  |
|  |  |  | LH_2_3_3_0022v.jpg | 3 (doc 7) | Clélia CRIALESI | - | - | fine-tuned-model_best | - | No |  | lat |  |  |  |  |  |
|  |  |  | LH_2_3_3_0024r.jpg | 4 (doc 7) | Clélia CRIALESI | - | - | fine-tuned-model_best | - | No |  | lat |  |  |  |  |  |
|  |  | LH_4_2_11 | LH_4_2_11_0013r-0012v.jpg | 1 (doc 9) | Clément CARTIER | - | - | fine-tuned-model_best | - | HTR | Clément CARTIER | lat | Review | - | - | FoNDUE-GD_v2_la | à priori bon, à revoir en grand |
|  |  |  | LH_4_2_11_0013v-0012r.jpg | 2 (doc 9) | Clément CARTIER | - | - | fine-tuned-model_best | - | No |  | lat |  |  |  |  |  |
|  |  | LH_42_4_1 | LH_42_4_1_0007v.jpg | 1 (doc24) | David DENECHAUD | - | - | fine-tuned-model_best | - | HTR | David DENECHAUD | fr | Yes | - | - | FoNDUE-GD_v2_fr | à priori bon, à revoir en grand |
|  |  |  | LH_42_4_1_0008r.jpg | 2 (doc24) | David DENECHAUD | - | - | fine-tuned-model_best | - | HTR | David DENECHAUD | fr | En cours | - | - | FoNDUE-GD_v2_fr | revu, jusqu'à la ligne n°30 |
|  |  | LH_4_1_11 | LH_4_1_11_0001r.jpg | 1 (doc8) | Mathias | - | - | fine-tuned-model_best | - | HTR | Mathias | lat | Yes | - | - | FoNDUE-GD_v2_la |  |
|  |  |  | LH_4_1_11_0001v.jpg | 2 (doc8) | Mathias | - | - | fine-tuned-model_best | - | No |  | lat |  |  |  |  |  |
|  |  | LH_4_5_6 | LH_4_5_6_0015r-0014v.jpg | 1 (doc12) | Michael MASSUSSI et ? | - | - | fine-tuned-model_best | - | HTR | Michael MASSUSSI et ? | lat | En cours | - | - | FoNDUE-GD_v2_la | revu, jusqu'à la ligne n°19 - beaucoup de choses à revoir |
|  |  |  | LH_4_5_6_0015v-0014r.jpg | 2 (doc12) | Michael MASSUSSI et ? | - | - | fine-tuned-model_best | - | No |  | lat |  |  |  |  |  |
|  |  | LH_4_3_2 | LH_4_3_2_0002r-0001v.jpg | 1(doc10) | Nadiejda TAMITEGAMA | - | - | fine-tuned-model_best | - | HTR | Nadiejda TAMITEGAMA | lat | Yes | - | - | FoNDUE-GD_v2_la |  |
|  |  |  | LH_4_3_2_0002v-0001r.jpg | 2(doc10) | Nadiejda TAMITEGAMA | - | - | fine-tuned-model_best | - | No |  |  |  |  |  |  |  |
|  |  | LH_1_6_17 | LH_1_6_17_0002r-0001v.jpg | 1(doc3) | Nicolas Gregoire VEYRIE | - | - | fine-tuned-model_best | - | HTR | Nicolas Gregoire VEYRIE | lat | Yes | - | - | FoNDUE-GD_v2_la | à revoir pour les accents... on ne mets pas d'accents en latin |
|  |  |  | LH_1_6_17_0002v-0001r.jpg | 2(doc3) | Nicolas Gregoire VEYRIE | - | - | fine-tuned-model_best | - | HTR | Nicolas Gregoire VEYRIE | lat | Yes | - | - | FoNDUE-GD_v2_la |  |
|  |  | LH_2_3_1 | LH_2_3_1_0049r.jpg | 1(doc5) | Simone CHERI | - | - | fine-tuned-model_best | - | HTR | Simone CHERI | lat | Yes | - | - | manual | à priori bon, à revoir en grand ; renommer les fichiers pour le n° de page |
|  |  |  | LH_2_3_1_0049v.jpg | 2(doc5) | Simone CHERI | - | - | fine-tuned-model_best | - | No |  |  |  |  |  |  |  |
|  |  | LH_1_3_1 | LH_1_3_1_0024v.jpg | 1(doc20) | Taro TOKUTAKE | - | - | fine-tuned-model_best | - | HTR | Taro TOKUTAKE | fr | En cours | - | - | FoNDUE-GD_v2_fr | revu, jusqu'à la ligne n°30 |
|  |  | LH_35_11_8 | LH_35_11_8_0002r.jpg | 2(doc25) | YUAN Rui | - | - | fine-tuned-model_best | - | HTR | YUAN Rui | fr | Yes | - | - | FoNDUE-GD_v2_fr | à priori bon, à revoir en grand |
| 22-06-2026 | AVI-4_copies_au_propre | LH_1_4_8 | LH_1_4_8_0020r-0019v.jpg | 1 | Pedro |  |  | best_0.4006 | - | No |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | TOTAL PAGES CORRIGEES : | 43 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | TOTAL PAGES CORRIGEES (LAT) : | 21 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  | TOTAL PAGES CORRIGEES (FR) : | 19 |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  | Tableau des scores (c'est pas une compétition) |  |  |  |  |  |  |  |  |  |  |  |  |  |

