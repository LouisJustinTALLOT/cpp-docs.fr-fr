---
title: Erreur du compilateur C2506 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2506
dev_langs:
- C++
helpviewer_keywords:
- C2506
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5369a6a5bf904f7a7492037fbad4df44de92e66
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228516"
---
# <a name="compiler-error-c2506"></a>Erreur du compilateur C2506
'membre' : '__declspec (modifier)' ne peut pas être appliqué à ce symbole  
  
 Vous ne pouvez pas déclarer par processus ou par domaine d’application pour les membres statiques d’une classe managée.  
  
 Pour plus d'informations, voir [appdomain](../../cpp/appdomain.md) .  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C2506.  
  
```  
// C2506.cpp  
// compile with: /clr /c  
ref struct R {  
   __declspec(process) static int n;   // C2506  
   int o;   // OK  
};  
```