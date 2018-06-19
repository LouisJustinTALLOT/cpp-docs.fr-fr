---
title: Erreur mathématique M6201 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6201
dev_langs:
- C++
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6a15e841cfc8daf1abdafc9997698807e7356af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332063"
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