---
title: Erreur du compilateur C2377 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2377
dev_langs:
- C++
helpviewer_keywords:
- C2377
ms.assetid: f7660965-bf4c-4cd9-8307-1bd7016678a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7d76b94ef099c2ac84ee7f048539ed56549d2e0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33195254"
---
# <a name="compiler-error-c2377"></a>Erreur du compilateur C2377
'identificateur' : redéfinition ; un typedef ne peut pas être surchargé avec un autre symbole  
  
 Un identificateur `typedef` est redéfini.  
  
 L’exemple suivant génère l’erreur C2377 :  
  
```  
// C2377.cpp  
// compile with: /c  
typedef int i;  
int i;   // C2377  
int j;   // OK  
```