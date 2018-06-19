---
title: Erreur du compilateur C3354 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3354
dev_langs:
- C++
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b4bcc36580a453932068350f01b53c5f09f2d69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257353"
---
# <a name="compiler-error-c3354"></a>Erreur du compilateur C3354
'fonction' : la fonction utilisée pour créer un délégué ne peut pas avoir un type de retour 'type'  
  
 Les types suivants ne sont pas des types de retour valides pour un `delegate`:  
  
-   Pointeur vers fonction  
  
-   Pointeur vers membre  
  
-   Pointeur vers fonction membre  
  
-   Référence vers fonction  
  
-   Référence vers fonction membre  
  
 L’exemple suivant génère l’erreur C3354 :  
  
```  
// C3354_2.cpp  
// compile with: /clr /c  
using namespace System;  
typedef void ( *VoidPfn )();  
  
delegate VoidPfn func(); // C3354  
// try the following line instead  
// delegate  void func();  
```  
