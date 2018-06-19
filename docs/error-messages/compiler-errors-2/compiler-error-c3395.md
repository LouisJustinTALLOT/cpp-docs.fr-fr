---
title: Erreur du compilateur C3395 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3395
dev_langs:
- C++
helpviewer_keywords:
- C3395
ms.assetid: 26a9ebc9-ed97-47ce-b436-19aa2bcf6e50
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 202162ecac8907852ca621599f5306884e59ae98
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254308"
---
# <a name="compiler-error-c3395"></a>Erreur du compilateur C3395
'fonction' : __declspec (dllexport) ne peut pas être appliqué à une fonction avec la \__clrcall convention d’appel  
  
 `__declspec(dllexport)` et [__clrcall](../../cpp/clrcall.md) ne sont pas compatibles.  Pour plus d’informations, consultez [dllexport, dllimport](../../cpp/dllexport-dllimport.md).  
  
 L’exemple suivant génère l’erreur C3395 :  
  
```  
// C3395.cpp  
// compile with: /clr /c  
  
__declspec(dllexport) void __clrcall Test(){}   // C3395  
void __clrcall Test2(){}   // OK  
__declspec(dllexport) void Test3(){}   // OK  
```