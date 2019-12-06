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
ms.openlocfilehash: 1541840521695658b5c4d809ba7e11767b1330a2
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857552"
---
# <a name="customizing-c-command-line-processing"></a>Personnalisation du traitement de ligne de commande C++

**Section spécifique de Microsoft**

Si votre programme ne prend pas d’arguments de ligne de commande, vous pouvez économiser une petite quantité d’espace en supprimant l’utilisation de la routine de bibliothèque qui exécute le traitement de ligne de commande. Cette routine est appelée `_setargv` et est décrite dans [extension des caractères génériques](../cpp/wildcard-expansion.md). Pour supprimer son utilisation, définissez une routine qui ne fait rien dans le fichier contenant la fonction `main`, et nommez-la `_setargv`. L’appel à `_setargv` est ensuite satisfait par votre définition de `_setargv`, et la version de la bibliothèque n’est pas chargée.

De même, si vous n’accédez jamais à la table d’environnement via l’argument `envp`, vous pouvez fournir votre propre routine vide à utiliser à la place de `_setenvp`, la routine de traitement de l’environnement. À l’instar de la fonction `_setargv`, `_setenvp` doit être déclaré comme **extern "C"** .

Votre programme peut effectuer des appels à la famille de routines `spawn` ou `exec` dans la bibliothèque Runtime C. Le cas échéant, vous ne devez pas supprimer la routine de traitement de l'environnement, car cette routine est utilisée pour transmettre un environnement du processus parent au processus enfant.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[main : démarrage du programme](../cpp/main-program-startup.md)