---
title: Erreur du compilateur C2388 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2388
dev_langs:
- C++
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38ce3de47355dea18f2c2deca8cfe07cde4d313f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198662"
---
# <a name="compiler-error-c2388"></a>Erreur du compilateur C2388
'symbole' : un symbole ne peut pas être déclaré avec les deux __declspec(appdomain) et \__declspec(process)  
  
 Le `appdomain` et `process` `__declspec` modificateurs ne peuvent pas être utilisés sur le même symbole. Le stockage d’une variable existe par processus ou par domaine d’application.  
  
 Pour plus d’informations, consultez [appdomain](../../cpp/appdomain.md) et [process](../../cpp/process.md).  
  
 L’exemple suivant génère l’erreur C2388 :  
  
```  
// C2388.cpp  
// compile with: /clr /c  
__declspec(process) __declspec(appdomain) int i;   // C2388  
__declspec(appdomain) int i;   // OK  
```