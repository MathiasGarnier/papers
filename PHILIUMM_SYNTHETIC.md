On cherche à générer des pages synthétiques de manuscrits de Leibniz. Pourquoi ? Pour apprendre à le faire tout d'abord et ensuite pour aider au finetuning d'un modèle d'HTR. Initialement, on a souhaité se restreindre à des GAN, les modèles de diffusion étant trop intensifs en calcul (ou alors l'installation ne se passait pas comme prévu voire tout simplement le code ne fonctionnait pas). Finalement, un tout petit modèle comme [Emuru](https://huggingface.co/blowing-up-groundhogs/emuru) (_T5-based decoder with a Variational Autoencoder_; 0.7B) permet d'obtenir des résultats déjà intéressants (si on pense à appliquer ultérieurement de la petite géométrie pour dégrader, reformater, transformer l'image générée afin de la rendre plus réaliste, c'est-à-dire qu'elle colle plus à ce que l'on peut effectivement observer dans les manuscrits de Leibniz).

C'est un modèle prenant en entrée une ligne stylisée accompagnée de sa transcription ainsi que le texte que l'on souhaite voir écrit selon le style manuscrit fourni. En sortie, on obtient donc une image. Pour les premiers tests de ce modèle, on s'est borné à extraire des XML Pages toutes les lignes afin d'avoir une correspondance texte <-> bounding box. Il suffisait alors de fournir au modèle le texte que l'on souhaitait voir générer. Pour cela, comme on cherche à générer des données non précédemment vues, on a récupéré des échantillons textuels que l'on a ensuite mélangés (quitte à obtenir des textes ne voulant plus rien dire; certains résultats tendent à montrer que l'important n'est pas là, qui plus est, pour des modèles non sémantiques et "purement visuels", ce n'est pas un soucis).


En partant de la référence manuscrite suivante : 

![Alt text](PHILIUMM_PLOTS/image_test_ligne.png)

en obtient la sortie brute, via Emuru, que voici :

![Alt text](PHILIUMM_PLOTS/outputModel.png)
