---
title: Variables d'environnement pour les optimisations guidées par profil
ms.date: 03/14/2018
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
ms.openlocfilehash: 099e57f1ac69223adafe7bec1af4cc3452915e86
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825827"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>Variables d'environnement pour les optimisations guidées par profil

Il existe trois variables d’environnement qui affectent des scénarios de test sur une image créée avec **/LTCG : PGI** pour les optimisations guidées par profil :

- **PogoSafeMode** Spécifie s’il faut utiliser le mode rapide ou le mode sans échec pour le profilage de l’application.

- **VCPROFILE_ALLOC_SCALE** ajoute de la mémoire supplémentaire pour une utilisation par le profileur.

- **VCPROFILE_PATH** vous permet de spécifier le dossier utilisé pour les fichiers .pgc.

**Les variables d’environnement PogoSafeMode et VCPROFILE_ALLOC_SCALE sont déconseillées à compter de Visual Studio 2015.** Les options de l’éditeur de liens [/GENPROFILE ou /fastgenprofile.](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) et [/USEPROFILE](reference/useprofile.md) spécifient le même comportement de l’éditeur de liens en tant que ces variables d’environnement.

## <a name="pogosafemode"></a>PogoSafeMode

Cette variable d’environnement est déconseillée. Utilisez le **EXACT** ou **NOEXACT** arguments à **/genprofile** ou **/fastgenprofile** pour contrôler ce comportement.

Effacer ou de définir le **PogoSafeMode** variable d’environnement pour spécifier s’il faut utiliser le mode rapide ou le mode sans échec pour le profilage d’application sur x86 systèmes.

Optimisation guidée par profil (PGO) a deux modes possibles pendant la phase de profilage : *mode rapide* et *mode sans échec*. Lorsque le profilage est en mode rapide, il utilise le **INC** instruction pour incrémenter des compteurs de données. Le **INC** instruction est plus rapide mais n’est pas thread-safe. Lorsque le profilage est en mode sans échec, il utilise le **LOCK INC** instruction pour incrémenter des compteurs de données. Le **LOCK INC** instruction a les mêmes fonctionnalités que le **INC** instruction a et est thread-safe, mais il est plus lent que le **INC** instruction.

Par défaut, le profilage PGO fonctionne en mode rapide. **PogoSafeMode** est nécessaire uniquement si vous souhaitez utiliser le mode sans échec.

Pour exécuter le profilage PGO en mode sans échec, vous devez utiliser la variable d’environnement **PogoSafeMode** ou le commutateur de l’éditeur de liens **/PogoSafeMode**, selon le système. Si vous effectuez le profilage sur un x64 ordinateur, vous devez utiliser le commutateur de l’éditeur de liens. Si vous effectuez le profilage sur un x86 ordinateur, vous pouvez utiliser l’éditeur de liens basculer ou définir le **PogoSafeMode** variable d’environnement à n’importe quelle valeur avant de commencer le processus d’optimisation.

### <a name="pogosafemode-syntax"></a>Syntaxe de PogoSafeMode

> **set PogoSafeMode**[**=**_value_]

Définissez **PogoSafeMode** à n’importe quelle valeur pour activer le mode sans échec. Définir sans une valeur pour effacer une valeur précédente et de réactiver le mode rapide.

## <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE

Cette variable d’environnement est déconseillée. Utilisez le **MEMMIN** et **MEMMAX** arguments à **/genprofile** ou **/fastgenprofile** pour contrôler ce comportement.

Modifier le **VCPROFILE_ALLOC_SCALE** variable d’environnement pour modifier la quantité de mémoire allouée pour contenir les données de profil. Dans de rares cas, il y aura suffisamment de mémoire disponible pour prendre en charge collecte des données de profil lors de l’exécution des scénarios de test. Dans ce cas, vous pouvez augmenter la quantité de mémoire en définissant **VCPROFILE_ALLOC_SCALE**. Si vous recevez un message d’erreur au cours d’une série de tests qui indique que vous disposez d’une mémoire insuffisante, attribuez une valeur supérieure à **VCPROFILE_ALLOC_SCALE**, jusqu'à ce que l’exécution du test terminé sans erreurs de mémoire insuffisante.

### <a name="vcprofileallocscale-syntax"></a>Syntaxe VCPROFILE_ALLOC_SCALE

> **set VCPROFILE_ALLOC_SCALE**[__=__*scale_value*]

Le *scale_value* paramètre est un facteur d’échelle pour la quantité de mémoire souhaitée pour l’exécution de scénarios de test.  La valeur par défaut est 1. Par exemple, cette ligne de commande définit le facteur d’échelle à 2 :

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofilepath"></a>VCPROFILE_PATH

Utilisez le **VCPROFILE_PATH** variable d’environnement pour spécifier le répertoire pour créer les fichiers .pgc. Par défaut, les fichiers .pgc sont créés dans le même répertoire que le fichier binaire profilé. Toutefois, si le chemin d’accès absolu du fichier binaire n’existe pas, as ne peut être le cas lorsque vous exécutez des scénarios de profil sur un autre ordinateur sur lequel le fichier binaire a été généré, vous pouvez définir **VCPROFILE_PATH** à un chemin d’accès qui existe sur l’ordinateur cible.

### <a name="vcprofilepath-syntax"></a>Syntaxe VCPROFILE_PATH

> **set VCPROFILE_PATH**[**=**_path_]

Définir le *chemin d’accès* paramètre vers le chemin du répertoire dans lequel ajouter les fichiers .pgc. Par exemple, cette ligne de commande définit le dossier à C:\profile :

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>Voir aussi

[Optimisations guidées par profil](profile-guided-optimizations.md)<br/>
[/GENPROFILE et /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](reference/useprofile.md)<br/>
