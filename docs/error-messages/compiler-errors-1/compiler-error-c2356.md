---
title: Erreur du compilateur C2356 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2356
dev_langs:
- C++
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9dfb13f388c6c40c6c1853ab8e87b2e39edbc1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33195202"
---
# <a name="compiler-error-c2356"></a>Erreur du compilateur C2356
un segment d’initialisation ne doit pas changer au cours de l’unité de traduction  
  
 Causes possibles :  
  
-   `#pragma init_seg` précédé par un code d’initialisation de segments  
  
-   `#pragma init_seg` précédé par un autre `#pragma init_seg`  
  
 Pour résoudre, déplacez le code d’initialisation de segments au début du module. Si plusieurs zones doivent être initialisées, déplacez-les dans des modules séparés.  
  
 L’exemple suivant génère l’erreur C2356 :  
  
```  
// C2356.cpp  
#pragma warning(disable : 4075)  
  
int __cdecl myexit(void (__cdecl *)());  
int __cdecl myexit2(void (__cdecl *)());  
  
#pragma init_seg(".mine$m",myexit)  
#pragma init_seg(".mine$m",myexit2)   // C2356  
```