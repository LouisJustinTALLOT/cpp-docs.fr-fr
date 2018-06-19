---
title: Erreur du compilateur C2637 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2637
dev_langs:
- C++
helpviewer_keywords:
- C2637
ms.assetid: 58d94447-eb96-4d8f-a690-dd78d322462e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4cc17927f3d0c161192ece8509599b48e4a5d16
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231546"
---
# <a name="compiler-error-c2637"></a>Erreur du compilateur C2637
'identificateur' : ne peut pas modifier les pointeurs sur données membres  
  
 Un pointeur vers un membre de données ne peut pas avoir une convention d’appel. Pour résoudre, supprimez la convention d’appel ou déclarer un pointeur vers une fonction membre.  
  
 L’exemple suivant génère l’erreur C2637 :  
  
```  
// C2637.cpp  
// compile with: /c  
struct S {};  
int __stdcall S::*pms1;   // C2637  
  
// OK  
int S::*pms2;  
int (__stdcall S::*pms3)(...);  
```