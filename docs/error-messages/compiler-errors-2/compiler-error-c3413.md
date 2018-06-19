---
title: Erreur du compilateur C3413 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3413
dev_langs:
- C++
helpviewer_keywords:
- C3413
ms.assetid: de6c9b05-c373-4bd8-8cb0-12c2cd2e5674
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afe7d444a755d053dcd73d02cb964510c7ce3324
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252971"
---
# <a name="compiler-error-c3413"></a>Erreur du compilateur C3413
'nom' : instanciation explicite non valide  
  
 Le compilateur a détecté une instanciation explicite incorrecte.  
  
 L’exemple suivant génère l’erreur C3413 :  
  
```  
// C3413.cpp  
template  
class MyClass {};   // C3413  
```  
  
 Solution possible :  
  
```  
// C3413b.cpp  
// compile with: /c  
template <class T>  
class MyClass {};  
  
template <>  
class MyClass<int> {};  
```