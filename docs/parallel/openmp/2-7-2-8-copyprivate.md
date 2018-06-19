---
title: 2.7.2.8 copyprivate | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c809f297da5059a98915e8055dfe23f45074366f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691601"
---
# <a name="2728-copyprivate"></a>2.7.2.8 copyprivate
Le **copyprivate** clause fournit un mécanisme pour utiliser une variable privée pour diffuser une valeur à partir d’un membre d’une équipe aux autres membres. Il est plutôt que d’utiliser une variable partagée pour la valeur lorsque fournissant cette variable partagée serait difficile (par exemple, dans une récursivité nécessitant une variable différente à chaque niveau). Le **copyprivate** clause peut uniquement apparaître sur le **unique** directive.  
  
 La syntaxe de la **copyprivate** clause est comme suit :  
  
```  
  
copyprivate(  
variable-list  
)  
  
```  
  
 L’effet de la **copyprivate** clause sur les variables dans sa liste de variable se produit après l’exécution du bloc structuré associé à la **unique** construire et avant les threads dans le équipe ont quitté la barrière à la fin de la construction. Puis, dans tous les autres threads de l’équipe, pour chaque variable dans le *liste de la variable*, cette variable devient définie (comme avec affectation) avec la valeur correspondantes variable dans le thread qui a exécuté la construction de structure bloc.  
  
 Restrictions à le **copyprivate** clause sont les suivantes :  
  
-   Une variable qui est spécifiée dans le **copyprivate** clause ne doit pas figurer dans un **privé** ou **firstprivate** clause pour le même **unique**la directive.  
  
-   Si un **unique** directive avec un **copyprivate** clause est rencontrée dans l’étendue dynamique d’une région parallèle, toutes les variables spécifiées dans le **copyprivate** clause doit être privé dans le contexte englobant.  
  
-   Une variable qui est spécifiée dans le **copyprivate** clause doit avoir un opérateur d’assignation de copie et non équivoque accessible.