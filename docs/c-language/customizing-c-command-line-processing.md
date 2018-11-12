---
title: Personnalisation du traitement de ligne de commande C
ms.date: 11/04/2016
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
ms.assetid: c20fa11d-b35b-4f3e-93b6-2cd5a1c3c993
ms.openlocfilehash: 9f7bc78c20aee4b91bf00fefd2615ba1a6611010
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623595"
---
# <a name="customizing-c-command-line-processing"></a>Personnalisation du traitement de ligne de commande C

Si votre programme ne prend pas d’arguments de ligne de commande, vous pouvez économiser une petite quantité d’espace en supprimant l’utilisation de la routine de bibliothèque qui exécute le traitement de ligne de commande. Cette routine est appelée **_setargv** (ou **_wsetargv** dans l’environnement à caractères larges), comme décrit dans [Développement les arguments génériques](../c-language/expanding-wildcard-arguments.md). Pour supprimer son utilisation, définissez une routine qui n'exécute aucune opération dans le fichier contenant la fonction **principale** et nommez-la **_setargv** (ou **_wsetargv** dans l'environnement à caractères larges). L'appel de **_setargv** ou **_wsetargv** est ensuite satisfait par votre définition de **_setargv** ou **_wsetargv**, et la version de la bibliothèque n'est pas chargée.

De même, si vous n’accédez jamais à la table d’environnement via l’argument `envp`, vous pouvez fournir votre propre routine vide à utiliser à la place de **_setenvp** (ou **_wsetenvp**), la routine de traitement de l’environnement.

Si votre programme effectue des appels à la famille **_spawn** ou **_exec** des routines de la bibliothèque Runtime C, vous ne devez pas supprimer la routine de traitement de l'environnement, car cette routine est utilisée pour transmettre un environnement du processus de génération dynamique au nouveau processus.

## <a name="see-also"></a>Voir aussi

[Fonction main et exécution du programme](../c-language/main-function-and-program-execution.md)