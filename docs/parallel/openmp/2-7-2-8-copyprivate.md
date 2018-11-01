---
title: 2.7.2.8 copyprivate
ms.date: 11/04/2016
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
ms.openlocfilehash: d4df1b4216014d3cd15be1480d2f83334fddb72d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622909"
---
# <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

Le **copyprivate** clause fournit un mécanisme pour utiliser une variable privée pour diffuser une valeur à partir d’un membre d’une équipe aux autres membres. Il est une alternative à l’utilisation d’une variable partagée pour la valeur lors de la fourniture de ce type d’une variable partagée serait difficile (par exemple, dans une récursivité nécessitant une variable différente à chaque niveau). Le **copyprivate** clause peut apparaître uniquement sur le **unique** directive.

La syntaxe de la **copyprivate** clause se présente comme suit :

```

copyprivate(
variable-list
)

```

L’effet de la **copyprivate** clause sur les variables dans sa liste de variable se produit après l’exécution du bloc structuré associé à la **unique** construire et avant que des threads dans la équipe ont quitté la barrière à la fin de la construction. Ensuite, dans tous les autres threads dans l’équipe, pour chaque variable dans le *variable-list*, cette variable devient définie (par affectation) avec la valeur correspondante variable dans le thread qui a exécuté la construction de structure bloc.

Restrictions pour le **copyprivate** clause sont les suivantes :

- Une variable qui est spécifiée dans le **copyprivate** clause ne doit pas apparaître dans un **privé** ou **firstprivate** clause pour le même **unique**directive.

- Si un **unique** directive avec un **copyprivate** clause est rencontrée dans l’étendue dynamique d’une région parallèle, toutes les variables spécifiées dans le **copyprivate** clause doit être privée dans le contexte englobant.

- Une variable qui est spécifiée dans le **copyprivate** clause doit avoir un opérateur d’assignation de copie non équivoque accessible.