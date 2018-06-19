---
title: Erreur du compilateur C2725 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2725
dev_langs:
- C++
helpviewer_keywords:
- C2725
ms.assetid: 13cd5b1b-e906-4cd8-9b2b-510d587c665a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a32f2a3255aa0d23f3164d01c0168365ad55c660
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236816"
---
# <a name="compiler-error-c2725"></a>Erreur du compilateur C2725
'exception' : impossible de lever ou d'intercepter un objet managé ou WinRT par valeur ou référence  
  
 Le type d'une exception managée ou WinRT était incorrect.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant génère l'erreur C2725 et montre comment la corriger :  
  
```  
// C2725.cpp  
// compile with: /clr  
ref class R {  
public:  
   int i;  
};  
  
int main() {  
   R % r1 = *gcnew R;  
   throw r1;   // C2725  
  
   R ^ r2 = gcnew R;  
   throw r2;   // OK     
}  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant génère l'erreur C2725 et montre comment la corriger :  
  
```  
// C2725b.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   try {}  
   catch( System::Exception%) {}   // C2725  
   // try the following line instead  
   // catch( System::Exception ^e) {}  
}  
```  
