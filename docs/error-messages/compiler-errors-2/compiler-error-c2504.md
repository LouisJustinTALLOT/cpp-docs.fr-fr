---
title: Erreur du compilateur C2504 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2504
dev_langs:
- C++
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bac0f8f28955af172590535568289182c3489d6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229514"
---
# <a name="compiler-error-c2504"></a>Erreur du compilateur C2504
'classe' : classe non définie de base  
  
 La classe de base est déclarée mais jamais définie.  Causes possibles :  
  
1.  Fichier include manquant.  
  
2.  Classe de base externe non déclarée avec [extern](../../cpp/using-extern-to-specify-linkage.md).  
  
 L’exemple suivant génère l’erreur C2504 :  
  
```  
// C2504.cpp  
// compile with: /c  
class A;  
class B : public A {};   // C2504  
```  
  
 BIEN  
  
```  
class C{};  
class D : public C {};  
```