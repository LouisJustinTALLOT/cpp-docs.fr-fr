---
title: Compilateur avertissement (niveau 4) C4408 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4408
dev_langs:
- C++
helpviewer_keywords:
- C4408
ms.assetid: 8488a186-ed1d-425c-aaeb-c72472c1da68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 640a3de24921186bd441b8f8b9bc5f3dcd7e5810
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297578"
---
# <a name="compiler-warning-level-4-c4408"></a>Avertissement du compilateur (niveau 4) C4408
anonymousstruct ou une union n’a déclaré aucune donnée membre  
  
 Un struct ou une union anonyme doit avoir au moins un membre de données.  
  
 L'exemple suivant génère l'avertissement C4408 :  
  
```  
// C4408.cpp  
// compile with: /W4 /LD  
static union  
{  
   // int i;  
};  
// a named union can have no data members  
// } MyUnion;  
```