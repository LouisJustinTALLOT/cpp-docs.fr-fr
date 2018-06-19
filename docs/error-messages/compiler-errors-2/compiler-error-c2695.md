---
title: Erreur du compilateur C2695 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2695
dev_langs:
- C++
helpviewer_keywords:
- C2695
ms.assetid: 3f6f2091-c38b-40ea-ab6c-f1846f5702d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67dc97688dddde37323f25b96bd8bbc596660e2f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231215"
---
# <a name="compiler-error-c2695"></a>Erreur du compilateur C2695
'fonction1' : fonction virtuelle de substitution diffère de 'fonction2' que par la convention d’appel  
  
 La signature d’une fonction dans une classe dérivée ne peut pas substituer une fonction dans une classe de base et modifier la convention d’appel.  
  
 L’exemple suivant génère l’erreur C2695 :  
  
```  
// C2695.cpp  
class C {  
   virtual void __fastcall func();  
};  
  
class D : public C {  
   virtual void __clrcall func();   // C2695  
};  
```