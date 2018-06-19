---
title: Opérateur charizing (#@) | Documents Microsoft
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
ms.openlocfilehash: e9e0c0d140d937b7359ff3abf9c0eae145a89210
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912730"
---
# <a name="charizing-operator-"></a>Opérateur charizing (#@)
**Section spécifique à Microsoft**  
  
 L’opérateur charizing peut être utilisé uniquement avec des arguments de macros. Si **#@** précède un paramètre formel dans la définition de la macro, l’argument réel est placé entre guillemets simples et traité comme un caractère lorsque la macro est développée. Par exemple :  
  
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