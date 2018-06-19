---
title: 'Procédure pas à pas : Création d’un réseau de traitement d’Image | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image-processing networks, creating [Concurrency Runtime]
- creating image-processing networks [Concurrency Runtime]
ms.assetid: 78ccadc9-5ce2-46cc-bd62-ce0f99d356b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e66de10879596b0e0877eb70f5ac95e082b8ae31
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693651"
---
# <a name="walkthrough-creating-an-image-processing-network"></a>Procédure pas à pas : création d'un réseau de traitement d'image
Ce document montre comment créer un réseau de blocs de messages asynchrones qui effectuent le traitement d’image.  
  
 Le réseau détermine les opérations à effectuer sur une image, en fonction de ses caractéristiques. Cet exemple utilise le *flux de données* modèle pour router des images via le réseau. Dans le modèle de flux de données, les composants indépendants d’un programme communiquent entre eux en envoyant des messages. Lorsqu’un composant reçoit un message, il peut effectuer une action et puis passe le résultat de cette action à un autre composant. Comparez ceci avec la *flux de contrôle* modèle, dans laquelle une application utilise des structures de contrôle, par exemple, les instructions conditionnelles, les boucles et ainsi de suite, pour contrôler l’ordre des opérations dans un programme.  
  
 Un réseau qui est basé sur le flux de données crée un *pipeline* de tâches. Chaque étape du pipeline effectue simultanément une partie de la tâche globale. Ce processus s'apparente à une chaîne de montage en construction automobile. Comme chaque véhicule passe via la ligne de l’assembly, un poste assemble le châssis, un autre installe le moteur et ainsi de suite. En activant plusieurs véhicules d’être assemblés en même temps, la ligne de l’assembly fournit le débit plus élevé que celui des véhicules d’assemblage à la fois.  
  
## <a name="prerequisites"></a>Prérequis  
 Lisez les documents suivants avant de commencer cette procédure pas à pas :  
  
-   [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [Guide pratique pour utiliser un filtre de bloc de message](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
-   [Procédure pas à pas : création des agents de flux de données](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)  
  
 Nous vous recommandons également de que vous comprenez les notions de base de [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] avant de commencer cette procédure pas à pas.  
  
##  <a name="top"></a> Sections  
 Cette procédure pas à pas contient les sections suivantes :  
  
-   [Définition des fonctionnalités de traitement d’Image](#functionality)  
  
-   [Création du réseau de traitement d’Image](#network)  
  
-   [Exemple complet](#complete)  
  
##  <a name="functionality"></a> Définition des fonctionnalités de traitement d’Image  
 Cette section présente les fonctions de prise en charge par le réseau de traitement d’image pour travailler avec des images qui sont lus à partir du disque.  
  
 Les fonctions suivantes, `GetRGB` et `MakeColor`, extraire et combiner les différents composants de la couleur donnée, respectivement.  
  
 [!code-cpp[concrt-image-processing-filter#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_1.cpp)]  
  

 La fonction suivante, `ProcessImage`, appelle la donnée [std::function](../../standard-library/function-class.md) objet à transformer la valeur de couleur de chaque pixel dans un [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] [Bitmap](https://msdn.microsoft.com/library/ms534420.aspx) objet. Le `ProcessImage` fonction utilise le [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorithme pour traiter chaque ligne de la bitmap en parallèle.  

  
 [!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_2.cpp)]  
  
 Les fonctions suivantes, `Grayscale`, `Sepiatone`, `ColorMask`, et `Darken`, appelez le `ProcessImage` fonction permettant de transformer la valeur de couleur de chaque pixel dans un `Bitmap` objet. Chacune de ces fonctions utilise une expression lambda pour définir la transformation de couleur d’un pixel.  
  
 [!code-cpp[concrt-image-processing-filter#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_3.cpp)]  
  
 La fonction suivante, `GetColorDominance`, appelle également la `ProcessImage` (fonction). Toutefois, au lieu de modifier la valeur de chaque couleur, cette fonction utilise [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) objets pour calculer si le composant de couleur rouge, vert ou bleu domine l’image.  
  
 [!code-cpp[concrt-image-processing-filter#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_4.cpp)]  
  
 La fonction suivante, `GetEncoderClsid`, récupère l’identificateur de classe pour le type MIME donné d’un encodeur. L’application utilise cette fonction pour extraire l’encodeur pour une image bitmap.  
  
 [!code-cpp[concrt-image-processing-filter#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_5.cpp)]  
  
 [[Haut](#top)]  
  
##  <a name="network"></a> Création du réseau de traitement d’Image  
 Cette section décrit comment créer un réseau de blocs de messages asynchrones qui effectuent le traitement de l’image sur chaque [!INCLUDE[TLA#tla_jpeg](../../parallel/concrt/includes/tlasharptla_jpeg_md.md)] image (.jpg) dans un répertoire donné. Le réseau effectue les opérations de traitement d’image suivantes :  
  
1.  Pour toute image qui est créée par Tom, convertir en nuances de gris.  
  
2.  Pour toute image qui est le rouge comme couleur dominante, supprimer les composants verts et bleus et assombrissement puis il.  
  
3.  Pour toute autre image, appliquer le ton sépia.  
  
 Le réseau s’applique uniquement la première opération de traitement d’image qui correspond à l’une de ces conditions. Par exemple, si une image est créée par Tom et rouge comme couleur dominante, l’image est uniquement convertie en nuances de gris.  
  
 Une fois le réseau effectue chaque opération de traitement d’image, elle enregistre l’image sur le disque sous forme de fichier bitmap (.bmp).  
  
 Les étapes suivantes montrent comment créer une fonction qui implémente ce réseau de traitement d’image et s’applique à ce réseau à chaque [!INCLUDE[TLA#tla_jpeg](../../parallel/concrt/includes/tlasharptla_jpeg_md.md)] image dans un répertoire donné.  
  
#### <a name="to-create-the-image-processing-network"></a>Pour créer le réseau de traitement d’image  
  
1.  Créez une fonction, `ProcessImages`, qui prend le nom d’un répertoire sur le disque.  
  
     [!code-cpp[concrt-image-processing-filter#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_6.cpp)]  
  
2.  Dans le `ProcessImages` fonctionne, créez un `countdown_event` variable. La `countdown_event` classe est illustrée plus loin dans cette procédure pas à pas.  
  
     [!code-cpp[concrt-image-processing-filter#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_7.cpp)]  
  
3.  Créer un [std::map](../../standard-library/map-class.md) objet associe un `Bitmap` objet avec son nom de fichier d’origine.  
  
     [!code-cpp[concrt-image-processing-filter#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_8.cpp)]  
  
4.  Ajoutez le code suivant pour définir les membres du réseau de traitement d’image.  
  
     [!code-cpp[concrt-image-processing-filter#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_9.cpp)]  
  
5.  Ajoutez le code suivant pour vous connecter au réseau.  
  
     [!code-cpp[concrt-image-processing-filter#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_10.cpp)]  
  
6.  Ajoutez le code suivant pour envoyer au début du réseau, le chemin d’accès complet de chaque [!INCLUDE[TLA#tla_jpeg](../../parallel/concrt/includes/tlasharptla_jpeg_md.md)] fichier dans le répertoire.  
  
     [!code-cpp[concrt-image-processing-filter#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_11.cpp)]  
  
7.  Attendez que le `countdown_event` variable atteigne la valeur zéro.  
  
     [!code-cpp[concrt-image-processing-filter#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_12.cpp)]  
  
 Le tableau ci-dessous décrit les membres du réseau.  
  
|Membre|Description|  
|------------|-----------------|  
|`load_bitmap`|A [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) objet qui charge une `Bitmap` de l’objet à partir du disque et ajoute une entrée pour le `map` objet à associer l’image avec son nom de fichier d’origine.|  
|`loaded_bitmaps`|A [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objet qui envoie les images chargées aux filtres de traitement d’image.|  
|`grayscale`|A `transformer` objet qui convertit les images qui sont créées par Tom en nuances de gris. Il utilise les métadonnées de l’image pour déterminer son auteur.|  
|`colormask`|A `transformer` objet qui supprime les composants de couleur vert et bleu à partir d’images qui sont le rouge comme couleur dominante.|  
|`darken`|A `transformer` objet diminuer la luminosité images qui ont le rouge comme couleur dominante.|  
|`sepiatone`|A `transformer` objet qui applique le ton sépia aux images qui ne sont pas créées par Tom et ne sont pas principalement en rouge.|  
|`save_bitmap`|A `transformer` objet qui enregistre le traité `image` sur le disque sous forme de bitmap. `save_bitmap` Récupère le nom de fichier d’origine à partir de la `map` de l’objet et modifie son extension de nom de fichier pour les fichiers .bmp.|  
|`delete_bitmap`|A `transformer` objet qui libère la mémoire pour les images.|  
|`decrement`|A [concurrency::call](../../parallel/concrt/reference/call-class.md) objet qui agit comme le nœud terminal dans le réseau. Il décrémente le `countdown_event` objet afin de signaler à l’application principale qu’une image a été traitée.|  
  
 Le `loaded_bitmaps` tampon de messages est important car, comme un `unbounded_buffer` de l’objet, il offre `Bitmap` objets à plusieurs destinataires. Lorsqu’un bloc cible accepte un `Bitmap` objet, le `unbounded_buffer` objet n’offre que `Bitmap` objet à d’autres cibles. Par conséquent, l’ordre dans lequel vous liez les objets à un `unbounded_buffer` objet est important. Le `grayscale`, `colormask`, et `sepiatone` messages chaque bloc utilisent un filtre pour accepter uniquement certains `Bitmap` objets. Le `decrement` tampon de messages est une cible importante de la `loaded_bitmaps` mémoire tampon des messages, car il accepte tous les `Bitmap` les objets qui sont rejetés par les tampons de messages. Un `unbounded_buffer` objet est nécessaire pour propager des messages dans l’ordre. Par conséquent, un `unbounded_buffer` objet bloque jusqu'à ce qu’un nouveau bloc cible est lié et accepte le message si aucun bloc en cours de la cible n’accepte ce message.  
  
 Si votre application nécessite que plusieurs messages bloque le processus du message, au lieu de simplement le bloc d’un message qui tout d’abord accepte le message, vous pouvez utiliser un autre type de bloc de message, tel que `overwrite_buffer`. La `overwrite_buffer` classe contient un seul message à la fois, mais il propage ce message à chacune de ses cibles.  
  
 L’illustration suivante montre le réseau de traitement d’image :  
  
 ![Réseau de traitement d’image](../../parallel/concrt/media/concrt_imageproc.png "concrt_imageproc")  
  
 Le `countdown_event` objet dans cet exemple active le réseau de traitement d’image informer l’application principale lorsque toutes les images ont été traitées. Le `countdown_event` classe utilise un [concurrency::event](../../parallel/concrt/reference/event-class.md) objet pour indiquer quand une valeur de compteur atteint zéro. L’application principale incrémente le compteur chaque fois qu’il envoie un nom de fichier pour le réseau. Le nœud de terminaison du réseau décrémente le compteur après chaque image a été traité. Une fois l’application principale a parcouru le répertoire spécifié, il attend que le `countdown_event` objet signale que son compteur a atteint zéro.  
  
 L’exemple suivant illustre la `countdown_event` classe :  
  
 [!code-cpp[concrt-image-processing-filter#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_13.cpp)]  
  
 [[Haut](#top)]  
  
##  <a name="complete"></a> L’exemple complet  
 L'exemple de code suivant illustre l'exemple complet. Le `wmain` fonction gère le [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] bibliothèque et appelle le `ProcessImages` fonctionner au processus le [!INCLUDE[TLA#tla_jpeg](../../parallel/concrt/includes/tlasharptla_jpeg_md.md)] les fichiers dans le `Sample Pictures` active.  
  
 [!code-cpp[concrt-image-processing-filter#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_14.cpp)]  
  
 L’illustration suivante montre un exemple de sortie. Chaque image source est au-dessus de son image modifiée correspondante.  
  
 ![Exemple de sortie pour l’exemple](../../parallel/concrt/media/concrt_imageout.png "concrt_imageout")  
  
 `Lighthouse` est créée par Tom Alphin et par conséquent, est converti en nuances de gris. `Chrysanthemum`, `Desert`, `Koala`, et `Tulips` ont rouge comme couleur dominante et par conséquent, les composants de la couleur bleue et verte supprimés et sont foncées. `Hydrangeas`, `Jellyfish`, et `Penguins` correspondent aux critères par défaut et sont donc sépia tons.  
  
 [[Haut](#top)]  
  
### <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `image-processing-network.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 **CL.exe /DUNICODE /EHsc image-processing-Network.cpp /link gdiplus.lib**  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures pas à pas relatives au runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
