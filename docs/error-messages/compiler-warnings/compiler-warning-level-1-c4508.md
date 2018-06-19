---
title: Compilateur avertissement (niveau 1) C4508 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4508
dev_langs:
- C++
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53f152c2f3573e5f3bd7b8e9be0603ed6d3f11bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283194"
---
# <a name="compiler-warning-level-1-c4508"></a>Avertissement du compilateur (niveau 1) C4508
'fonction' : fonction doit retourner une valeur ; 'void' pris par défaut de type de retour  
  
 La fonction n’a aucun type de retour spécifié. Dans ce cas, C4430 doit également déclencher et le compilateur implémente le correctif signalé par l’erreur C4430 (valeur par défaut est de type int).  
  
 Pour résoudre cet avertissement, déclarer explicitement le type de retour des fonctions.  
  
 L’exemple suivant génère C4508 :  
  
```  
// C4508.cpp  
// compile with: /W1 /c  
#pragma warning (disable : 4430)  
func() {}   // C4508  
void func2() {}   // OK  
```