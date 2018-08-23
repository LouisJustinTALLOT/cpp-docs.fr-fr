---
title: Compilateur avertissement (niveau 1) C4114 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4114
dev_langs:
- C++
helpviewer_keywords:
- C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9969f58b24defdb3dfa8a96437769d0b19e4569e
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "42541051"
---
# <a name="compiler-warning-level-1-c4114"></a>Compilateur avertissement (niveau 1) C4114
même qualificateur de type utilisé plusieurs fois  
  
 Une définition ou déclaration de type utilise un qualificateur de type (**const**, **volatile**, **signé**, ou **non signé**) plusieurs fois. Cela provoque un avertissement avec les extensions Microsoft (/Ze) et une erreur sous compatibilité ANSI (/Za).  
  
 L’exemple suivant génère l’erreur C4114 :  
  
```  
// C4114.cpp  
// compile with: /W1 /c  
volatile volatile int i;   // C4114  
```  
  
 L’exemple suivant génère l’erreur C4114 :  
  
```  
// C4114_b.cpp  
// compile with: /W1 /c  
static const int const * ii;   // C4114  
static const int * const iii;   // OK  
```
