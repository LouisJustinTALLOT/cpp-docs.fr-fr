---
title: 2.7.2.2 firstprivate | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b8e44ca52ba1f76d5b3791a1d08301bf06e7eab
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687398"
---
# <a name="2722-firstprivate"></a>2.7.2.2 firstprivate
Le **firstprivate** clause fournit un sur-ensemble de la fonctionnalité fournie par le **privé** clause. La syntaxe de la **firstprivate** clause est comme suit :  
  
```  
firstprivate(variable-list)  
```  
  
 Les variables spécifiées dans *variable-list* ont **privé** sémantique clause, comme décrit dans [Section 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) page 25. L’initialisation ou la construction qui se passe comme si elle a été réalisée une fois par thread, avant l’exécution du thread de la construction. Pour un **firstprivate** clause sur une construction parallèle, la valeur initiale du nouvel objet privé est la valeur de l’objet d’origine existe immédiatement avant la construction parallèle pour le thread qu’elle rencontre. Pour un **firstprivate** clause sur une construction de partage de travail, la valeur initiale du nouvel objet privée pour chaque thread qui exécute la construction de partage de travail est la valeur de l’objet d’origine qui existe avant le point dans le temps qui le même thread rencontre la construction de partage de travail. En outre, pour les objets C++, le nouvel objet privé pour chaque thread est construite à partir de l’objet d’origine de copie.  
  
 Les restrictions à le **firstprivate** clause sont les suivantes :  
  
-   Une variable spécifiée dans un **firstprivate** clause ne doit pas avoir un type incomplet ou un type référence.  
  
-   Une variable avec un type de classe qui est spécifiée en tant que **firstprivate** doit avoir un constructeur de copie accessible et non équivoque.  
  
-   Variables qui sont privés dans une région parallèle ou qui apparaissent dans le **réduction** clause d’une **parallèles** directive ne peut pas être spécifiée dans un **firstprivate** dans la clause un directive de partage de travail qui est liée à la construction parallèle.