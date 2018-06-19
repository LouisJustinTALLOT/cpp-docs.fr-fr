---
title: Erreur du compilateur C2570 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2570
dev_langs:
- C++
helpviewer_keywords:
- C2570
ms.assetid: d65d0b32-2fac-464a-bcdf-0ebcedf3bf32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b870ddd8bb162f4f65bd3200c397f912249304b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228301"
---
# <a name="compiler-error-c2570"></a>Erreur du compilateur C2570
'identificateur' : union ne peut pas avoir de classes de base  
  
 Une union dérive d’une classe, structure ou union. Cette opération n’est pas autorisée. Déclarez le type dérivé en tant que classe ou structure à la place.  
  
 L’exemple suivant génère l’erreur C2570 :  
  
```  
// C2570.cpp  
// compile with: /c  
class base {};  
union hasPubBase : public base {};   // C2570  
union hasNoBase {};   // OK  
```