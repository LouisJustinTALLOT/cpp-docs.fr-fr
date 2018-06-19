---
title: Compilateur avertissement (niveau 1) C4965 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4965
dev_langs:
- C++
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b731393471097fd3ba02979a48cd59513eaea9fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291900"
---
# <a name="compiler-warning-level-1-c4965"></a>Avertissement du compilateur (niveau 1) C4965
boxing implicite de l’entier 0 ; utilisez nullptr ou un cast explicite  
  
 Visual C++ propose un boxing implicite de types valeur. Une instruction qui a entraîné une attribution de null à l’aide des Extensions managées pour C++ devient alors une assignation à un type int converti.  
  
 Pour plus d’informations, consultez [Boxing](../../windows/boxing-cpp-component-extensions.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4965 :.  
  
```  
// C4965.cpp  
// compile with: /clr /W1  
int main() {  
   System::Object ^o = 0;   // C4965  
  
   // the previous line is the same as the following line  
   // using Managed Extensions for C++  
   // System::Object *o = __box(0);  
  
   // OK  
   System::Object ^o2 = nullptr;  
   System::Object ^o3 = safe_cast<System::Object^>(0);  
}  
```