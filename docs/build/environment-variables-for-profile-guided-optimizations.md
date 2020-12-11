---
description: En savoir plus sur les variables d’environnement pour les optimisations de Profile-Guided
title: Variables d'environnement pour les optimisations guidées par profil
ms.date: 03/14/2018
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
ms.openlocfilehash: dd78db781fc19b7ecfd451e01dc046b21bd87d11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156669"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>Variables d'environnement pour les optimisations guidées par profil

Il existe trois variables d’environnement qui affectent les scénarios de test sur une image créée avec **/LTCG : PGI** pour les optimisations guidées par profil :

- **PogoSafeMode** spécifie s’il faut utiliser le mode rapide ou le mode sans échec pour le profilage de l’application.

- **VCPROFILE_ALLOC_SCALE** ajoute de la mémoire supplémentaire pour une utilisation par le profileur.

- **VCPROFILE_PATH** vous permet de spécifier le dossier utilisé pour les fichiers. PGC.

**Les variables d’environnement PogoSafeMode et VCPROFILE_ALLOC_SCALE sont déconseillées à partir de Visual Studio 2015.** Les options de l’éditeur de liens [/GENPROFILE ou/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) et  [/USEPROFILE](reference/useprofile.md) spécifient le même comportement de l’éditeur de liens que ces variables d’environnement.

## <a name="pogosafemode"></a>PogoSafeMode

Cette variable d’environnement est déconseillée. Utilisez les arguments **exacts** ou **noexacts** de **/GENPROFILE** ou **/FASTGENPROFILE** pour contrôler ce comportement.

Désactivez ou définissez la variable d’environnement **PogoSafeMode** pour spécifier s’il faut utiliser le mode rapide ou le mode sans échec pour le profilage de l’application sur les systèmes x86.

L’optimisation guidée par profil (PGO) a deux modes possibles pendant la phase de profilage : le *mode rapide* et le *mode sans échec*. Lorsque le profilage est en mode rapide, il utilise l’instruction **Inc** pour augmenter les compteurs de données. L’instruction **Inc** est plus rapide, mais n’est pas thread-safe. Lorsque le profilage est en mode sans échec, il utilise l’instruction **Lock Inc** pour augmenter les compteurs de données. L’instruction **Lock Inc** a les mêmes fonctionnalités que l’instruction **Inc** , et est thread-safe, mais elle est plus lente que l’instruction **Inc** .

Par défaut, le profilage PGO fonctionne en mode rapide. **PogoSafeMode** est requis uniquement si vous souhaitez utiliser le mode sans échec.

Pour exécuter le profilage PGO en mode sans échec, vous devez utiliser la variable d’environnement **PogoSafeMode** ou le commutateur de l’éditeur de liens **/PogoSafeMode**, selon le système. Si vous effectuez le profilage sur un ordinateur x64, vous devez utiliser le commutateur de l’éditeur de liens. Si vous effectuez le profilage sur un ordinateur x86, vous pouvez utiliser le commutateur de l’éditeur de liens ou définir la variable d’environnement **PogoSafeMode** sur n’importe quelle valeur avant de démarrer le processus d’optimisation.

### <a name="pogosafemode-syntax"></a>Syntaxe PogoSafeMode

> **définir PogoSafeMode**[ **=** _valeur_]

Définissez **PogoSafeMode** sur n’importe quelle valeur pour activer le mode sans échec. Définissez sans valeur pour effacer une valeur précédente et réactiver le mode rapide.

## <a name="vcprofile_alloc_scale"></a>VCPROFILE_ALLOC_SCALE

Cette variable d’environnement est déconseillée. Utilisez les arguments **MEMMIN** et **MEMMAX** pour **/GENPROFILE** ou **/FASTGENPROFILE** afin de contrôler ce comportement.

Modifiez la variable d’environnement **VCPROFILE_ALLOC_SCALE** pour modifier la quantité de mémoire allouée pour contenir les données de profil. Dans de rares cas, il n’y a pas assez de mémoire disponible pour prendre en charge la collecte des données de profil lors de l’exécution de scénarios de test. Dans ce cas, vous pouvez augmenter la quantité de mémoire en définissant **VCPROFILE_ALLOC_SCALE**. Si vous recevez un message d’erreur pendant une série de tests qui indique que vous ne disposez pas de suffisamment de mémoire, assignez une plus grande valeur à **VCPROFILE_ALLOC_SCALE**, jusqu’à ce que l’exécution du test se termine sans erreurs de mémoire insuffisante.

### <a name="vcprofile_alloc_scale-syntax"></a>Syntaxe de VCPROFILE_ALLOC_SCALE

> **définir VCPROFILE_ALLOC_SCALE**[ __=__ *scale_value*]

Le paramètre *scale_value* est un facteur d’échelle pour la quantité de mémoire que vous souhaitez pour exécuter des scénarios de test.  La valeur par défaut est 1. Par exemple, cette ligne de commande définit le facteur d’échelle sur 2 :

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofile_path"></a>VCPROFILE_PATH

Utilisez la variable d’environnement **VCPROFILE_PATH** pour spécifier le répertoire dans lequel créer les fichiers. PGC. Par défaut, les fichiers. PGC sont créés dans le même répertoire que le fichier binaire en cours de profilage. Toutefois, si le chemin d’accès absolu du fichier binaire n’existe pas, comme cela peut être le cas lorsque vous exécutez des scénarios de profil sur un autre ordinateur que celui sur lequel le fichier binaire a été généré, vous pouvez définir **VCPROFILE_PATH** sur un chemin d’accès qui existe sur l’ordinateur cible.

### <a name="vcprofile_path-syntax"></a>Syntaxe de VCPROFILE_PATH

> **Set VCPROFILE_PATH**[ **=** _chemin_]

Définissez le paramètre *path* sur le chemin d’accès du répertoire dans lequel ajouter les fichiers. PGC. Par exemple, cette ligne de commande définit le dossier C:\profile :

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>Voir aussi

[Optimisations guidées par profil](profile-guided-optimizations.md)<br/>
[/GENPROFILE et/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](reference/useprofile.md)<br/>
