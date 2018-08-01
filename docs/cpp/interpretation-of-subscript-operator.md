---
title: Interprétation de l’opérateur d’indice | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- subscript operator [C++], interpretation of
- arrays [C++], subscripting
- interpreting subscript operators [C++]
- operators [C++], interpretation of subscript
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75659730198e09a172625c54bfcbdd54b7a9f857
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404786"
---
# <a name="interpretation-of-subscript-operator"></a>Interprétation de l'opérateur Indice
Comme d’autres opérateurs, l’opérateur d’indice (**[]**) peut être redéfini par l’utilisateur. Le comportement par défaut de l'opérateur d'indice, s'il n'est pas surchargé, est de combiner le nom d'un tableau et l'indice à l'aide de la méthode suivante :  
  
 \*((*nom de tableau*) + (*indice*))  
  
 Comme dans toute addition qui implique des types pointeur, la mise à l'échelle est exécutée automatiquement pour ajuster la taille du type. Par conséquent, la valeur résultante n’est pas *indice* octets à partir de l’origine de *nom de tableau*; au lieu de cela, il est le *indice*-ième élément du tableau. (Pour plus d’informations sur cette conversion, consultez [opérateurs additifs](../cpp/additive-operators-plus-and.md).)  
  
 De même, pour des tableaux multidimensionnels, l'adresse est dérivée à l'aide de la méthode suivante :  
  
 **((**   
 ***nom de tableau* ) + ()**   
 ***indice* 1***max*2  *\* max*3 *.. .max*n) **+** *indice*2  *\* max*3 *.. .max*n).   . . *+* *indice*n))  
  
## <a name="see-also"></a>Voir aussi  
 [Tableaux](../cpp/arrays-cpp.md)