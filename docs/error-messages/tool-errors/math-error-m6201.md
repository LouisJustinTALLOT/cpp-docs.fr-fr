---
title: "Erreur mathématique M6201 | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: M6201
dev_langs: C++
helpviewer_keywords: M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 17de7fab7b41a5a8acc2fed2f3c8185f66aadd9c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-m6201"></a>Erreur mathématique M6201
'fonction' : erreur _DOMAIN  
  
 Un argument de la fonction était en dehors du domaine de valeurs d’entrée valides pour cette fonction.  
  
## <a name="example"></a>Exemple  
  
```  
result = sqrt(-1.0)   // C statement  
result = SQRT(-1.0)   !  FORTRAN statement  
```  
  
 Cette erreur appelle la `_matherr` fonction avec le type d’erreur, le nom de fonction et ses arguments. Vous pouvez réécrire la `_matherr` afin de personnaliser la gestion de certaines erreurs mathématiques à virgule flottante d’exécution.