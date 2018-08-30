---
title: Compilateur avertissement (niveau 1) C4311 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4311
dev_langs:
- C++
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adfd27a116ae5747a2dd899ce51c38f01055f356
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218538"
---
# <a name="compiler-warning-level-1-c4311"></a>Avertissement du compilateur (niveau 1) C4311
'variable' : troncation de pointeur de 'type' à 'type'  
  
 Cet avertissement détecte les problèmes de troncation de pointeur 64 bits. Par exemple, si le code est compilé pour une architecture 64 bits, la valeur d'un pointeur (64 bits) est tronquée si elle est affectée à un `int` (32 bits). Pour plus d’informations, consultez [règles d’utilisation des pointeurs](/windows/desktop/WinProg64/rules-for-using-pointers).  
  
 Pour plus d’informations sur les causes courantes de l’avertissement C4311, consultez [erreurs de compilateur communes](/windows/desktop/WinProg64/common-compiler-errors).  
  
 L'exemple de code suivant génère l'avertissement C4311 quand il est compilé pour une cible 64 bits, puis indique comment le corriger :  
  
```  
// C4311.cpp  
// compile by using: cl /W1 C4311.cpp  
int main() {  
   void* p = &p;  
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets  
   unsigned long long j = (unsigned long long) p;   // OK  
}  
  
```