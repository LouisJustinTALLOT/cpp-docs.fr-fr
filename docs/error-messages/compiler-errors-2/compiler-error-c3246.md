---
title: Erreur du compilateur C3246 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3246
dev_langs:
- C++
helpviewer_keywords:
- C3246
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb7feedafc4c965912bcb8ee022601e52d0c0f3a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253250"
---
# <a name="compiler-error-c3246"></a>Erreur du compilateur C3246
'classe' : ne peut pas hériter de 'type', car il a été déclaré comme 'sealed'  
  
Une classe marquée [sealed](../../windows/sealed-cpp-component-extensions.md) ne peut pas être la classe de base d’autres classes.  
  
L’exemple suivant génère l’erreur C3246 :  
  
```  
// C3246_2.cpp  
// compile with: /clr /LD  
ref class X sealed {};  
  
ref class Y : public X {}; // C3246  
```  
