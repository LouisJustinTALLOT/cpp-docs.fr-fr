---
title: Erreur du compilateur C3271 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3271
dev_langs:
- C++
helpviewer_keywords:
- C3271
ms.assetid: 16d8bd1d-2e30-4c6a-a07f-0c4f3342fab5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9dc8389c934169bac2a990127be7a273a2db18ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251688"
---
# <a name="compiler-error-c3271"></a>Erreur du compilateur C3271
'membre' : valeur 'valeur' non valide pour l’attribut FieldOffset  
  
 Un nombre négatif a été passé à l’attribut **FieldOffset** .  
  
 L’exemple suivant génère l’erreur C3271 :  
  
```  
// C3271.cpp  
// compile with: /clr /c  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[StructLayout(LayoutKind::Explicit)]  
value class MyStruct1 {  
   public: [FieldOffset(0)] int a;  
   public: [FieldOffset(-1)] long b;   // C3271  
};  
```  
