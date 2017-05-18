---
title: "C3320 d’erreur du compilateur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3320
dev_langs:
- C++
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: 4b4acfe97e38cf13e336b7c58ffc868c69cf7a09
ms.contentlocale: fr-fr
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3320"></a>Erreur du compilateur C3320
'type' : le type ne peut pas avoir le même nom que la propriété 'name' du module  
  
Un défini par l’utilisateur type exporté (UDT), qui peut être un struct, classe, enum ou union, ne peut pas avoir le même nom que le paramètre passé à la [module](../../windows/module-cpp.md) propriété du nom de l’attribut.  
  
## <a name="example"></a>Exemple  
L’exemple suivant génère l’erreur C3320 :  
  
```cpp  
// C3320.cpp  
#include "unknwn.h"  
[module(name="xx")];  
  
[export] struct xx {   // C3320  
// Try the following line instead  
// [export] struct yy {  
   int i;  
};  
```
