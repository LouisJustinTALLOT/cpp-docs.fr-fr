---
title: 2.7.2.7 copyin | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ee711bfb24e7a2a1cbada1a7e01a243e204f4a8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689374"
---
# <a name="2727-copyin"></a>2.7.2.7 copyin
Le **copyin** clause fournit un mécanisme pour attribuer la même valeur pour **threadprivate** variables pour chaque thread dans l’équipe de l’exécution de la région parallèle. Pour chaque variable spécifiée dans un **copyin** clause, la valeur de la variable dans le thread principal de l’équipe est copiée, comme lors d’affectation, pour les copies de thread privé au début de la région parallèle. La syntaxe de la **copyin** clause est comme suit :  
  
```  
  
copyin(  
variable-list  
)  
  
```  
  
 Les restrictions à le **copyin** clause sont les suivantes :  
  
-   Une variable qui est spécifiée dans le **copyin** clause doit avoir un opérateur d’assignation de copie accessible et non équivoque.  
  
-   Une variable qui est spécifiée dans le **copyin** clause doit être un **threadprivate** variable.