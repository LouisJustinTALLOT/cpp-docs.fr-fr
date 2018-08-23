---
title: Opérateur charizing (#@) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#@'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6aa18936497f0415da331697aceb26f26345500
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42541377"
---
# <a name="charizing-operator-"></a>Opérateur charizing (#@)
**Section spécifique à Microsoft**  
  
L’opérateur charizing peut être utilisé uniquement avec des arguments de macros. Si `#@` précède un paramètre formel dans la définition de la macro, l’argument réel est placé entre guillemets simples et traité comme un caractère lorsque la macro est développée. Exemple :  
  
```  
#define makechar(x)  #@x  
```  
  
provoque le développement de l'instruction  
  
```  
a = makechar(b);  
```  
  
à développer en  
  
```  
a = 'b';  
```  
  
Le guillemet simple ne peut pas être utilisé avec l'opérateur charizing.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 
[Opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md)