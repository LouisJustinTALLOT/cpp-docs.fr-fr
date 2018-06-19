---
title: Erreur du compilateur C2070 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2070
dev_langs:
- C++
helpviewer_keywords:
- C2070
ms.assetid: 4c8dea63-1227-4aba-be26-2462537f86fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8eaf9ee345543fe838358c345e68874eecadd72
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33165176"
---
# <a name="compiler-error-c2070"></a>Erreur du compilateur C2070
'type' : opérande sizeof non conforme  
  
 Le [sizeof](../../cpp/sizeof-operator.md) opérateur requiert un nom d’expression ou de type.  
  
 L’exemple suivant génère l’erreur C2070 :  
  
```  
// C2070.cpp  
void func() {}  
int main() {  
   int a;  
   a = sizeof(func);   // C2070  
}  
```  
  
 Solution possible :  
  
```  
// C2070b.cpp  
void func() {}  
int main() {  
   int a;  
   a = sizeof(a);  
}  
```