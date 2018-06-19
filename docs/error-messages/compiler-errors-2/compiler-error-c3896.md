---
title: Erreur du compilateur C3896 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3896
dev_langs:
- C++
helpviewer_keywords:
- C3896
ms.assetid: eb8be0f6-5b4e-4d71-8285-8a2a94f8ba29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcc60c09d6fd99e56f0261409099e56713604a76
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269736"
---
# <a name="compiler-error-c3896"></a>Erreur du compilateur C3896
'membre' : initialiseur incorrect : cette donnée membre littérale ne peut être initialisée qu’avec 'nullptr'  
  
 A [littéral](../../windows/literal-cpp-component-extensions.md) membre de données a été initialisé de manière incorrecte.  Consultez [nullptr](../../windows/nullptr-cpp-component-extensions.md) pour plus d’informations.  
  
 L’exemple suivant génère l’erreur C3896 :  
  
```  
// C3896.cpp  
// compile with: /clr /c  
ref class R{};  
  
value class V {  
   literal R ^ r = "test";   // C3896  
   literal R ^ r2 = nullptr;   // OK  
};  
```