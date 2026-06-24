# Rapides rappels des résultats de la campagne d'évaluation

# Quels modèles évaluer ?
1. FoNDUE-GD_v2.mlmodel = modèle entraîné sur l'ensemble des langues
2. FoNDUE-GD_v2_fr.mlmodel = il s'agit du modèle FoNDUE-GD_v2.mlmodel fine-tuné sur des textes en français
3. FoNDUE-GD_v2_la.mlmodel = il s'agit du modèle FoNDUE-GD_v2.mlmodel fine-tuné sur des textes en latin
4. version_15
5. version_22
6. german_handwriting_fine-tune_BerlinGT_v1.2 (peut être exclus, considéré comme sous-performant; mais corrigé & utilisé pour la vérité terrain).

À cela s'ajoutent deux fine-tuning produits par D.-F. Bumba lors da la fin du mois de juin. Leurs performances semblent néanmoins, au premier coup d'oeil, bien inférieures à ce dont nous disposions précedemment. De plus, parallèlement à ces modèles _lightweights_, de rapides tests employant des vLLM ont été conduits.
Noter que pour chacun des tests, la segmentation est réputée être de confiance.
