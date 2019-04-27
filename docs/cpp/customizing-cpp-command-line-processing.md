---
title: Personnalisation du traitement de ligne de commande C++
ms.date: 11/04/2016
f1_keywords:
- _setenvp
- _setargv
helpviewer_keywords:
- command line [C++], processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line [C++], processing arguments
- suppressing environment processing
- _setenvp function
ms.assetid: aae01cbb-892b-48b8-8e1f-34f22421f263
ms.openlocfilehash: da1b3bdd6392b144f9315add4c19de14c1d14d41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154689"
---
# <a name="customizing-c-command-line-processing"></a>Personnalisation du traitement de ligne de commande C++

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

Si votre programme ne prend pas d’arguments de ligne de commande, vous pouvez économiser une petite quantité d’espace en supprimant l’utilisation de la routine de bibliothèque qui exécute le traitement de ligne de commande. Cette routine est appelée `_setargv` et est décrit dans [développement des caractères génériques](../cpp/wildcard-expansion.md). Pour supprimer son utilisation, définissez une routine qui ne fait rien dans le fichier contenant le `main` de fonction et nommez-le `_setargv`. L’appel à `_setargv` est ensuite satisfait par votre définition de `_setargv`, et la version de la bibliothèque n’est pas chargée.

De même, si vous n’accédez jamais à la table d’environnement via le `envp` argument, vous pouvez fournir votre propre routine vide à utiliser à la place de `_setenvp`, la routine de traitement de l’environnement. Comme avec la `_setargv` (fonction), `_setenvp` doit être déclarée comme **extern « C »**.

Votre programme peut effectuer des appels à la `spawn` ou `exec` famille des routines de la bibliothèque Runtime C. Le cas échéant, vous ne devez pas supprimer la routine de traitement de l'environnement, car cette routine est utilisée pour transmettre un environnement du processus parent au processus enfant.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[main : démarrage du programme](../cpp/main-program-startup.md)