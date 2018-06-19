---
title: Erreur du compilateur C3865 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3865
dev_langs:
- C++
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99a872d4cf7ed285a0798461c77adf904cfa3e71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275497"
---
# <a name="compiler-error-c3865"></a>Erreur du compilateur C3865
'convention_appel' : peut uniquement être utilisé sur des fonctions membres natives  
  
 Une convention d’appel a été utilisé sur une fonction qui a été soit une fonction globale ou une fonction membre managée. La convention d’appel peut être utilisé uniquement sur une fonction membre (non managée) native.  
  
 Pour plus d’informations, consultez [Conventions d’appel](../../cpp/calling-conventions.md).  
  
 L’exemple suivant génère l’erreur C3865 :  
  
```  
// C3865.cpp  
// compile with: /clr  
// processor: x86  
void __thiscall Func(){}   // C3865  
  
// OK  
struct MyType {  
   void __thiscall Func(){}  
};  
```