---
title: L’erreur C2711 erreur de compilateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2711
dev_langs:
- C++
helpviewer_keywords:
- C2711
ms.assetid: 9df9f808-7419-4e63-abdd-e6538ff0871f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb2e5c904d7f6d865b94ea4fb4ba65be4c974f8b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234273"
---
# <a name="compiler-error-c2711"></a>Erreur C2711 erreur de compilateur
'fonction' : cette fonction ne peut pas être compilé comme code managé, utilisez #pragma unmanaged  
  
 Certaines instructions empêche le compilateur de générer le code MSIL pour la fonction englobante.  
  
 L’exemple suivant génère l’erreur C2711 :  
  
```  
// C2711.cpp  
// compile with: /clr  
// processor: x86  
using namespace System;  
value struct V {  
   static const t = 10;  
};  
  
void bar() {  
   V::t;  
   __asm int 3   // C2711 inline asm can't be compiled managed  
}  
```