# Installation

Pour éviter tout soucis d'installation (pour les utilisateurs Windows ou de certaines distributions Linux), on fournit un [notebook Colab](https://colab.research.google.com/drive/1dMvd0vr-Owg6MUeVhxWr2EylcE6RZSAg?usp=sharing) (exécutable à condition de disposer d'un compte Google). Autrement, on se réfère à la procédure d'installation décrite par Denisa Bumba sur [gitlab](https://gitlab.com/eman8/scripts/scripts-pour-le-pretraitement-des-corpus-sur-EMAN/gestion_resultats_htr-ocr/-/tree/main/eScriptorium_postprocessing_pipeline?ref_type=heads).



# Rapides rappels des résultats des précédentes campagnes d'évaluations



Pour une description plus exhaustive et schématique de la chaîne de traitement, on consultera avec profit [la pipeline datée du 13 janvier 2026](https://groupes.renater.fr/wiki/eman/_media/prive/htrleibniz/pipeline_leibniz_13-01-2026.pdf) et, plus généralement, [les carnets de tests suivants](https://groupes.renater.fr/wiki/eman/prive/htrleibniz/chaine_de_traitement_pour_l_augmentation_de_la_verite_terrain_et_l_amelioration_des_modeles_htr).

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
