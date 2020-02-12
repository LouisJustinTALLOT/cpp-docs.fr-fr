---
title: "Procédure pas à pas : création d'un réseau de traitement d'image"
ms.date: 04/25/2019
helpviewer_keywords:
- image-processing networks, creating [Concurrency Runtime]
- creating image-processing networks [Concurrency Runtime]
ms.assetid: 78ccadc9-5ce2-46cc-bd62-ce0f99d356b8
ms.openlocfilehash: 03d95be8fae3565a51811357ed9553c3a2649674
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140755"
---
# <a name="walkthrough-creating-an-image-processing-network"></a>Procédure pas à pas : création d'un réseau de traitement d'image

Ce document montre comment créer un réseau de blocs de messages asynchrones qui effectuent le traitement d’image.

Le réseau détermine les opérations à effectuer sur une image en fonction de ses caractéristiques. Cet exemple utilise le modèle de *flux* de données pour acheminer les images via le réseau. Dans le modèle de flux de données, les composants indépendants d’un programme communiquent entre eux en envoyant des messages. Lorsqu’un composant reçoit un message, il peut effectuer une action, puis passer le résultat de cette action à un autre composant. Comparez ceci au modèle de *contrôle* de l’application, dans lequel une application utilise des structures de contrôle, par exemple des instructions conditionnelles, des boucles, et ainsi de suite, pour contrôler l’ordre des opérations dans un programme.

Un réseau basé sur le flux de données crée un *pipeline* de tâches. Chaque étape du pipeline effectue simultanément une partie de la tâche globale. Ce processus s'apparente à une chaîne de montage en construction automobile. À mesure que chaque véhicule traverse la ligne d’assemblage, une station assemble le cadre, une autre installe le moteur, et ainsi de suite. En permettant à plusieurs véhicules d’être assemblés simultanément, la ligne d’assemblage offre un meilleur débit que l’assemblage des véhicules complets un par un.

## <a name="prerequisites"></a>Conditions préalables requises

Lisez les documents suivants avant de commencer cette procédure pas à pas :

- [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)

- [Guide pratique pour utiliser un filtre de bloc de message](../../parallel/concrt/how-to-use-a-message-block-filter.md)

- [Procédure pas à pas : création des agents de flux de données](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)

Nous vous recommandons également de comprendre les principes de base de GDI+ avant de commencer cette procédure pas à pas.

## <a name="top"></a> Sections

Cette procédure pas à pas contient les sections suivantes :

- [Définition de la fonctionnalité de traitement d’image](#functionality)

- [Création du réseau de traitement des images](#network)

- [Exemple complet](#complete)

## <a name="functionality"></a>Définition de la fonctionnalité de traitement d’image

Cette section présente les fonctions de prise en charge que le réseau de traitement d’images utilise pour travailler avec les images lues à partir du disque.

Les fonctions suivantes, `GetRGB` et `MakeColor`, extraient et combinent les différents composants de la couleur donnée, respectivement.

[!code-cpp[concrt-image-processing-filter#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_1.cpp)]

La fonction suivante, `ProcessImage`, appelle l’objet [std :: function](../../standard-library/function-class.md) donné pour transformer la valeur de couleur de chaque pixel dans un objet [bitmap](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) GDI+. La fonction `ProcessImage` utilise l’algorithme [Concurrency ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) pour traiter chaque ligne de la bitmap en parallèle.

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_2.cpp)]

Les fonctions suivantes, `Grayscale`, `Sepiatone`, `ColorMask`et `Darken`, appellent la fonction `ProcessImage` pour transformer la valeur de couleur de chaque pixel dans un objet `Bitmap`. Chacune de ces fonctions utilise une expression lambda pour définir la transformation de couleur d’un pixel.

[!code-cpp[concrt-image-processing-filter#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_3.cpp)]

La fonction suivante, `GetColorDominance`, appelle également la fonction `ProcessImage`. Toutefois, au lieu de modifier la valeur de chaque couleur, cette fonction utilise les objets [Concurrency :: combinables](../../parallel/concrt/reference/combinable-class.md) pour calculer si le composant de couleur rouge, vert ou bleu domine l’image.

[!code-cpp[concrt-image-processing-filter#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_4.cpp)]

La fonction suivante, `GetEncoderClsid`, récupère l’identificateur de classe pour le type MIME donné d’un encodeur. L’application utilise cette fonction pour récupérer l’encodeur d’une image bitmap.

[!code-cpp[concrt-image-processing-filter#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_5.cpp)]

[[Haut](#top)]

## <a name="network"></a>Création du réseau de traitement des images

Cette section décrit comment créer un réseau de blocs de messages asynchrones qui effectuent le traitement d’image sur chaque image JPEG (. jpg) dans un répertoire donné. Le réseau effectue les opérations de traitement d’image suivantes :

1. Pour toute image créée par Tom, convertir en nuances de gris.

1. Pour toute image dont la couleur dominante est rouge, supprimez les composants vert et bleu, puis assombriz-le.

1. Pour toute autre image, appliquez le ton sépia.

Le réseau applique uniquement la première opération de traitement d’image qui correspond à l’une de ces conditions. Par exemple, si une image est créée par Tom et que sa couleur dominante est rouge, l’image est convertie en nuances de gris uniquement.

Une fois que le réseau a effectué chaque opération de traitement d’image, il enregistre l’image sur le disque sous la forme d’un fichier bitmap (. bmp).

Les étapes suivantes montrent comment créer une fonction qui implémente ce réseau de traitement d’image et applique ce réseau à chaque image JPEG dans un répertoire donné.

#### <a name="to-create-the-image-processing-network"></a>Pour créer le réseau de traitement des images

1. Créez une fonction, `ProcessImages`, qui prend le nom d’un répertoire sur le disque.

   [!code-cpp[concrt-image-processing-filter#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_6.cpp)]

1. Dans la fonction `ProcessImages`, créez une variable `countdown_event`. La classe `countdown_event` est présentée plus loin dans cette procédure pas à pas.

   [!code-cpp[concrt-image-processing-filter#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_7.cpp)]

1. Créez un objet [std :: Map](../../standard-library/map-class.md) qui associe un objet `Bitmap` à son nom de fichier d’origine.

   [!code-cpp[concrt-image-processing-filter#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_8.cpp)]

1. Ajoutez le code suivant pour définir les membres du réseau de traitement des images.

   [!code-cpp[concrt-image-processing-filter#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_9.cpp)]

1. Ajoutez le code suivant pour connecter le réseau.

   [!code-cpp[concrt-image-processing-filter#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_10.cpp)]

1. Ajoutez le code suivant pour envoyer à l’en-tête du réseau le chemin d’accès complet de chaque fichier JPEG dans le répertoire.

   [!code-cpp[concrt-image-processing-filter#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_11.cpp)]

1. Attendez que la variable `countdown_event` atteigne zéro.

   [!code-cpp[concrt-image-processing-filter#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_12.cpp)]

Le tableau ci-dessous décrit les membres du réseau.

|Membre|Description|
|------------|-----------------|
|`load_bitmap`|Objet [Concurrency :: transformer](../../parallel/concrt/reference/transformer-class.md) qui charge un objet `Bitmap` à partir du disque et ajoute une entrée à l’objet `map` pour associer l’image à son nom de fichier d’origine.|
|`loaded_bitmaps`|Objet [Concurrency :: unbounded_buffer](reference/unbounded-buffer-class.md) qui envoie les images chargées aux filtres de traitement d’image.|
|`grayscale`|Objet `transformer` qui convertit les images créées par Tom en nuances de gris. Elle utilise les métadonnées de l’image pour déterminer son auteur.|
|`colormask`|Objet `transformer` qui supprime les composants de couleur vert et bleu des images dont la couleur dominante est rouge.|
|`darken`|Objet `transformer` qui assombrit les images dont la couleur dominante est rouge.|
|`sepiatone`|Objet `transformer` qui applique le ton sépia aux images qui ne sont pas créées par Tom et qui ne sont pas principalement en rouge.|
|`save_bitmap`|Objet `transformer` qui enregistre les `image` traités sur le disque sous forme de bitmap. `save_bitmap` récupère le nom de fichier d’origine à partir de l’objet `map` et remplace son extension de nom de fichier par. bmp.|
|`delete_bitmap`|Objet `transformer` qui libère la mémoire pour les images.|
|`decrement`|Objet [Concurrency :: Call](../../parallel/concrt/reference/call-class.md) qui agit en tant que nœud terminal dans le réseau. Il décrémente l’objet `countdown_event` pour signaler à l’application principale qu’une image a été traitée.|

La mémoire tampon des messages `loaded_bitmaps` est importante car, en tant qu’objet `unbounded_buffer`, elle offre des objets `Bitmap` à plusieurs destinataires. Lorsqu’un bloc cible accepte un objet `Bitmap`, l’objet `unbounded_buffer` ne propose pas cet objet `Bitmap` à d’autres cibles. Par conséquent, l’ordre dans lequel vous liez des objets à un objet `unbounded_buffer` est important. Les blocs de message `grayscale`, `colormask`et `sepiatone` utilisent chacun un filtre pour accepter uniquement certains `Bitmap` objets. La mémoire tampon des messages `decrement` est une cible importante de la mémoire tampon des messages `loaded_bitmaps` car elle accepte tous les objets `Bitmap` qui sont rejetés par les autres mémoires tampons de messages. Un objet `unbounded_buffer` est requis pour propager les messages dans l’ordre. Par conséquent, un objet `unbounded_buffer` se bloque jusqu’à ce qu’un nouveau bloc cible lui soit lié et accepte le message si aucun bloc cible actuel n’accepte ce message.

Si votre application nécessite que plusieurs blocs de messages traitent le message, au lieu d’un seul bloc de message qui accepte le message, vous pouvez utiliser un autre type de bloc de message, tel que `overwrite_buffer`. La classe `overwrite_buffer` contient un message à la fois, mais propage ce message à chacune de ses cibles.

L’illustration suivante montre le réseau de traitement des images :

![Réseau de traitement d’image](../../parallel/concrt/media/concrt_imageproc.png "Réseau de traitement d'images")

L’objet `countdown_event` dans cet exemple permet au réseau de traitement des images d’informer l’application principale lorsque toutes les images ont été traitées. La classe `countdown_event` utilise un objet [Concurrency :: Event](../../parallel/concrt/reference/event-class.md) pour signaler quand une valeur de compteur atteint zéro. L’application principale incrémente le compteur chaque fois qu’il envoie un nom de fichier au réseau. Le nœud terminal du réseau décrémente le compteur après que chaque image a été traitée. Une fois que l’application principale a parcouru le répertoire spécifié, elle attend que l’objet `countdown_event` signale que son compteur a atteint zéro.

L’exemple suivant illustre la classe `countdown_event` :

[!code-cpp[concrt-image-processing-filter#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_13.cpp)]

[[Haut](#top)]

## <a name="complete"></a>L’exemple complet

L'exemple de code suivant illustre l'exemple complet. La fonction `wmain` gère la bibliothèque GDI+ et appelle la fonction `ProcessImages` pour traiter les fichiers JPEG dans le répertoire `Sample Pictures`.

[!code-cpp[concrt-image-processing-filter#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-image-processing-network_14.cpp)]

L’illustration suivante montre un exemple de sortie. Chaque image source est au-dessus de son image modifiée correspondante.

![Exemple de sortie pour l’exemple](../../parallel/concrt/media/concrt_imageout.png "Sortie de l'exemple")

`Lighthouse` est créée par Tom Alphin et est donc convertie en nuances de gris. `Chrysanthemum`, `Desert`, `Koala`et `Tulips` ont en rouge la couleur dominante et les composants Blue et Green Color sont donc supprimés et obscurcis. `Hydrangeas`, `Jellyfish`et `Penguins` correspondent aux critères par défaut et par conséquent, il s’agit de sépia toned.

[[Haut](#top)]

### <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `image-processing-network.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**CL. exe/DUNICODE/EHsc Image-Processing-Network. cpp/Link Gdiplus. lib**

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas relatives au runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
