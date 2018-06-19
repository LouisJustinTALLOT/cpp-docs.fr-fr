---
title: Erreur du compilateur C2150 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2150
dev_langs:
- C++
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7dc7a84ff666fdc17f0abeec690a548f216ce975
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170146"
---
# <a name="compiler-error-c2150"></a>Erreur du compilateur C2150
  
> '*identificateur*' : champ de bits doit être de type 'int', 'signed int' ou 'unsigned int'  
  
 Le type de base pour un champ de bits doit être `int`, `signed int`, ou `unsigned int`.  
  
## <a name="example"></a>Exemple  
  
 Cet exemple montre comment vous pouvez rencontrer l’erreur C2150, et comment vous pouvez la corriger :  
  
```cpp  
// C2150.cpp  
// compile with: /c  
struct A {  
   float a : 8;    // C2150  
   int i : 8;      // OK  
};  
```