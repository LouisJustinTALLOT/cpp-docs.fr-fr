---
title: Erreur du compilateur C2507 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2507
dev_langs:
- C++
helpviewer_keywords:
- C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82bd4fb028712093a44ada4ae58e97c2fbcf7eed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230533"
---
# <a name="compiler-error-c2507"></a>Erreur du compilateur C2507
'identificateur' : modificateurs virtuels sur la classe de base trop nombreux  
  
 Une classe ou une structure est déclarée en tant que `virtual` plusieurs fois. Seul `virtual` modificateur peut apparaître pour chaque classe dans une liste de classes de base.  
  
 L’exemple suivant génère l’erreur C2507 :  
  
```  
// C2507.cpp  
// compile with: /c  
class A {};  
class B : virtual virtual public A {};   // C2507  
class C : virtual public A {};   // OK  
```