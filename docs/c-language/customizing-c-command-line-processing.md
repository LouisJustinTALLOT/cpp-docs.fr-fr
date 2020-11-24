---
title: Personnalisation du traitement de ligne de commande C
description: Comment supprimer `main` la gestion des paramètres d’environnement et des arguments de fonction dans le code de démarrage du Runtime.
ms.date: 11/19/2020
helpviewer_keywords:
- _spawn functions
- command line, processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line, processing arguments
- suppressing environment processing
- _exec function
ms.openlocfilehash: fc306172491cd401caeecb3c87c0711f8b4ef911
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483293"
---
# <a name="customizing-c-command-line-processing"></a>Personnalisation du traitement de ligne de commande C

Si votre programme ne prend pas d’arguments de ligne de commande, vous pouvez supprimer la routine de traitement de ligne de commande pour économiser une petite quantité d’espace. Pour supprimer son utilisation, incluez le *`noarg.obj`* fichier (pour `main` et `wmain` ) dans les **`/link`** Options du compilateur ou la **`LINK`** ligne de commande.

De même, si vous n’accédez jamais à la table d’environnement via l' *`envp`* argument, vous pouvez supprimer la routine de traitement de l’environnement interne. Pour supprimer son utilisation, incluez le *`noenv.obj`* fichier (pour `main` et `wmain` ) dans les **`/link`** Options du compilateur ou la **`LINK`** ligne de commande.

Pour plus d’informations sur les options de l’éditeur de liens de démarrage du runtime, consultez [options de liaison](../c-runtime-library/link-options.md).

Votre programme peut effectuer des appels à `spawn` la `exec` famille ou des routines dans la bibliothèque Runtime C. Si c’est le cas, vous ne devez pas supprimer la routine de traitement de l’environnement, car elle est utilisée pour passer un environnement du processus parent au processus enfant.

## <a name="see-also"></a>Voir aussi

[`main` fonction et exécution du programme](../c-language/main-function-and-program-execution.md)\
[Options de liaison](../c-runtime-library/link-options.md).
