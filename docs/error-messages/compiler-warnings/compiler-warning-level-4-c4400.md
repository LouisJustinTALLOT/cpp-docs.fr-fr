---
title: Compilateur avertissement (niveau 4) C4400 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4400
dev_langs:
- C++
helpviewer_keywords:
- C4400
ms.assetid: f135fe98-4f92-4e07-9d71-2621b36ee755
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7164b323e5108b44ea40da699ffb906508f731a2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299381"
---
# <a name="compiler-warning-level-4-c4400"></a>Avertissement du compilateur (niveau 4) C4400
'type' : les qualificateurs const/volatile pour ce type ne sont pas pris en charge.  
  
 Le [const](../../cpp/const-cpp.md)et [volatile](../../cpp/volatile-cpp.md)qualificateurs ne fonctionnent pas avec les variables de types common language runtime.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C4400.  
  
```  
// C4400.cpp  
// compile with: /clr /W4  
// C4401 expected  
using namespace System;  
#pragma warning (disable : 4101)  
int main() {  
   const String^ str;   // C4400  
   volatile String^ str2;   // C4400  
}  
```