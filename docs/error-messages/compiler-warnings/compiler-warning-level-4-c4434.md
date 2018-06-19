---
title: Compilateur avertissement (niveau 4) C4434 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4434
dev_langs:
- C++
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c639fa1cc89266fd9cc2935d88132ceae225a85e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293411"
---
# <a name="compiler-warning-level-4-c4434"></a>Avertissement du compilateur (niveau 4) C4434
un constructeur de classe doit avoir un accès privé ; la modification d’un accès privé  
  
 L’erreur C4434 indique que le compilateur a modifié l’accessibilité d’un constructeur statique. Les constructeurs statiques doivent avoir un accès privé, car ils sont uniquement destinés à être appelé par le common language runtime. Pour plus d’informations, consultez [constructeurs statiques](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4434.  
  
```  
// C4434.cpp  
// compile with: /W4 /c /clr  
public ref struct R {  
   static R(){}   // C4434  
};  
```