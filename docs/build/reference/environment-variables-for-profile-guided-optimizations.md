---
title: Variables d’environnement pour les optimisations guidées par profil | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19edc9c8a2702e5b7ac9ae4a49364718f19d3900
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379443"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>Variables d'environnement pour les optimisations guidées par profil

Il existe trois variables d’environnement qui affectent des scénarios de test sur une image créée avec **/LTCG : PGI** pour les optimisations guidées par profil :

- **PogoSafeMode** Spécifie s’il faut utiliser le mode rapide ou en mode sans échec pour le profilage de l’application.

- **VCPROFILE_ALLOC_SCALE** ajoute de la mémoire supplémentaire pour une utilisation par le profileur.

- **VCPROFILE_PATH** vous permet de spécifier le dossier utilisé pour les fichiers .pgc.

**Les variables d’environnement PogoSafeMode et VCPROFILE_ALLOC_SCALE sont obsolètes à partir de Visual Studio 2015.** Les options de l’éditeur de liens [/GENPROFILE ou /fastgenprofile.](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) et [/useprofile](useprofile.md) spécifient le même comportement de l’éditeur de liens en tant que ces variables d’environnement.

## <a name="pogosafemode"></a>PogoSafeMode

Cette variable d’environnement est déconseillée. Utilisez le **EXACT** ou **NOEXACT** arguments **/genprofile** ou **/fastgenprofile** pour contrôler ce comportement.

Définissez ou désactivez le **PogoSafeMode** variable d’environnement pour spécifier s’il faut utiliser le mode rapide ou en mode sans échec pour le profilage d’application sur x86 systèmes.

L’optimisation guidée par profil (PGO) a deux modes possibles pendant la phase de profilage : *mode rapide* et *mode sans échec*. Lorsque le profilage est en mode rapide, il utilise le **INC** instruction pour incrémenter des compteurs de données. Le **INC** instruction est plus rapide, mais n’est pas thread-safe. Lorsque le profilage est en mode sans échec, il utilise le **LOCK INC** instruction pour incrémenter des compteurs de données. Le **LOCK INC** instruction a les mêmes fonctionnalités que le **INC** instruction a et qu’il est thread-safe, mais il est plus lente que la **INC** instruction.

Par défaut, le profilage PGO fonctionne en mode rapide. **PogoSafeMode** est nécessaire uniquement si vous souhaitez utiliser le mode sans échec.

Pour exécuter le profilage PGO en mode sans échec, vous devez utiliser la variable d’environnement **PogoSafeMode** ou le commutateur de l’éditeur de liens **/PogoSafeMode**, selon le système. Si vous effectuez le profilage sur une x64 ordinateur, vous devez utiliser le commutateur de l’éditeur de liens. Si vous effectuez le profilage sur x86 ordinateur, vous pouvez utiliser l’éditeur de liens basculer ou de définir la **PogoSafeMode** variable d’environnement pour n’importe quelle valeur avant de commencer le processus d’optimisation.

### <a name="pogosafemode-syntax"></a>Syntaxe de PogoSafeMode

> **définir PogoSafeMode**[**=**_valeur_]

Définissez **PogoSafeMode** à n’importe quelle valeur pour activer le mode sans échec. Définir sans une valeur pour effacer une valeur précédente et l’activer à nouveau en mode rapide.

## <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE

Cette variable d’environnement est déconseillée. Utilisez le **MEMMIN** et **MEMMAX** arguments **/genprofile** ou **/fastgenprofile** pour contrôler ce comportement.

Modifier la **VCPROFILE_ALLOC_SCALE** variable d’environnement pour modifier la quantité de mémoire allouée pour contenir les données de profil. Dans de rares cas, il ne sera pas y avoir assez de mémoire disponible pour prendre en charge lors de l’exécution de scénarios de test de collecte des données de profil. Dans ce cas, vous pouvez augmenter la quantité de mémoire en définissant **VCPROFILE_ALLOC_SCALE**. Si vous recevez un message d’erreur pendant une série de tests qui indique que vous disposez d’une mémoire insuffisante, affecter une valeur supérieure à **VCPROFILE_ALLOC_SCALE**, jusqu'à ce que l’exécution du test terminé sans erreurs de mémoire insuffisante.

### <a name="vcprofileallocscale-syntax"></a>Syntaxe VCPROFILE_ALLOC_SCALE

> **définir VCPROFILE_ALLOC_SCALE**[__=__*scale_value*]

Le *scale_value* paramètre est un facteur d’échelle pour la quantité de mémoire pour les scénarios de test en cours d’exécution.  La valeur par défaut est 1. Par exemple, cette ligne de commande définit le facteur d’échelle 2 :

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofilepath"></a>VCPROFILE_PATH

Utilisez le **VCPROFILE_PATH** variable d’environnement pour spécifier le répertoire pour créer des fichiers .pgc. Par défaut, les fichiers .pgc sont créés dans le même répertoire que le fichier binaire en cours de profilage. Toutefois, si le chemin d’accès absolu du fichier binaire n’existe pas, ne peut être le cas lorsque vous exécutez des scénarios de profil sur une autre machine où le fichier binaire a été créé, vous pouvez définir **VCPROFILE_PATH** à un chemin d’accès qui existe sur l’ordinateur cible.

### <a name="vcprofilepath-syntax"></a>Syntaxe VCPROFILE_PATH

> **Définissez VCPROFILE_PATH**[**=**_chemin d’accès_]

Définir le *chemin d’accès* paramètre vers le chemin d’accès du répertoire à laquelle ajouter les fichiers .pgc. Par exemple, cette ligne de commande définit le dossier à C:\profile :

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>Voir aussi

[Optimisations guidées par profil](../../build/reference/profile-guided-optimizations.md)<br/>
[/GENPROFILE et /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](useprofile.md)<br/>
