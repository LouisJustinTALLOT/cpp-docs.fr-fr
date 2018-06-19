---
title: Erreur du compilateur C3902 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3902
dev_langs:
- C++
helpviewer_keywords:
- C3902
ms.assetid: feb3bb29-f836-4d77-ba71-3876f7f4f216
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0430ab95ae4884c420a3f7153fbbbbc4f7931675
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278195"
---
# <a name="compiler-error-c3902"></a>Erreur du compilateur C3902
'accesseur' : type du dernier paramètre doit être 'type'  
  
 Le type du dernier paramètre d’au moins une méthode set doit correspondre au type de la propriété. Pour plus d'informations, consultez [property](../../windows/property-cpp-component-extensions.md).  
  
 L’exemple suivant génère l’erreur C3902 :  
  
```  
// C3902.cpp  
// compile with: /clr /c  
using namespace System;  
ref class X {  
   property String ^Name {  
      void set(int);   // C3902  
      // try the following line instead  
      // void set(String^){}  
   }  
  
   property double values[int,int] {  
      void set(int, int, float);   // C3902  
      // try the following line instead  
      // void set(int, int, double){}  
   }  
};  
```