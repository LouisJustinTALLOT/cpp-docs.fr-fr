---
title: Erreur du compilateur C2776 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2776
dev_langs:
- C++
helpviewer_keywords:
- C2776
ms.assetid: 9d80addc-62c7-40fc-a2cc-60303abb87df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afbf3c48e5445d101408c2539cc077071b639044
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233766"
---
# <a name="compiler-error-c2776"></a>Erreur du compilateur C2776
une seule méthode 'get' peut être spécifiée par propriété  
  
 Vous pouvez spécifier un seul `get` de fonction dans le [propriété](../../cpp/property-cpp.md) attributs étendus. Cette erreur se produit lorsque plusieurs `get` fonctions sont spécifiées.  
  
 L’exemple suivant génère l’erreur C2776 :  
  
```  
// C2776.cpp  
struct A {  
   __declspec(property(get=GetProp,get=GetPropToo))  
   // try the following line instead  
   // __declspec(property(get=GetProp))  
      int prop;   // C2776  
   int GetProp(void);  
   int GetPropToo(void);  
};  
```