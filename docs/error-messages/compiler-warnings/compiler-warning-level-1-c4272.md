---
title: Compilateur avertissement (niveau 1) C4272 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4272
dev_langs:
- C++
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6de736c3226a9d3377769b65604a458c08e25df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277197"
---
# <a name="compiler-warning-level-1-c4272"></a>Avertissement du compilateur (niveau 1) C4272
'fonction' : est marqué comme __declspec (dllimport) ; Précisez une convention d’appel native lors de l’importation d’une fonction.  
  
 Il s’agit d’une erreur pour exporter une fonction marquée avec la [__clrcall](../../cpp/clrcall.md) convention d’appel et le compilateur émet cet avertissement si vous essayez d’importer une fonction marquée `__clrcall`.  
  
 L’exemple suivant génère l’erreur C4272 :  
  
```  
// C4272.cpp  
// compile with: /c /W1 /clr  
__declspec(dllimport) void __clrcall Test();   // C4272  
__declspec(dllimport) void Test2();   // OK  
```