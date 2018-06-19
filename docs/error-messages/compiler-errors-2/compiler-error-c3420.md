---
title: Erreur du compilateur C3420 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3420
dev_langs:
- C++
helpviewer_keywords:
- C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d7614d07cf98ae9fe857809bf9400d36a48ab0b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255056"
---
# <a name="compiler-error-c3420"></a>Erreur du compilateur C3420
'finalizer' : un finaliseur ne peut pas être virtuel  
  
 Un finaliseur peut uniquement être appelé de façon non virtuelle depuis son type englobant. Ainsi, il est incorrect de déclarer un finaliseur virtuel.  
  
 Pour plus d’informations, consultez [destructeurs et finaliseurs dans Comment : définir et consommer des classes et structs (C + c++ / CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3420.  
  
```  
// C3420.cpp  
// compile with: /clr /c  
ref class R {  
   virtual !R() {}   // C3420  
};  
```