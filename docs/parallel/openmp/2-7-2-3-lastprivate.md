---
title: 2.7.2.3 lastprivate | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08f331862d6e48b1c0882382285ddffa9699e79c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687340"
---
# <a name="2723-lastprivate"></a>2.7.2.3 lastprivate
Le `lastprivate` clause fournit un sur-ensemble de la fonctionnalité fournie par le `private` clause. La syntaxe de la `lastprivate` clause est comme suit :  
  
```  
lastprivate(variable-list)  
```  
  
 Les variables spécifiées dans le *variable-list* ont `private` sémantique de la clause. Lorsqu’un `lastprivate` clause apparaît sur la directive qui identifie une construction de partage de travail, la valeur de chaque `lastprivate` variable à partir de la manière séquentielle dernière itération de la boucle associée, ou la directive de section dernière lexicalement, est assignée à la objet d’origine de la variable. Une valeur assignée aux variables qui ne sont pas par la dernière itération de la **pour** ou **parallèles pour**, ou par la section lexicalement dernier de la **sections** ou  **sections parallèles** directive, ont des valeurs indéterminées après la construction. Non assignés sous-objets ont également une valeur indéterminée après la construction.  
  
 Les restrictions à le `lastprivate` clause sont les suivantes :  
  
-   Toutes les restrictions pour `private` s’appliquent.  
  
-   Une variable avec un type de classe qui est spécifiée en tant que `lastprivate` doit avoir un opérateur d’assignation de copie accessible et non équivoque.  
  
-   Les variables qui sont privés dans une région parallèle ou qui apparaissent dans le `reduction` clause d’un **parallèle** directive ne peut pas être spécifiée dans un `lastprivate` clause sur une directive de partage de travail qui est lié à la construction parallèle.