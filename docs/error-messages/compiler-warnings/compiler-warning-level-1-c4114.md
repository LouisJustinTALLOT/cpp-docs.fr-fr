---
title: Compilateur avertissement (niveau 1) C4114 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4114
dev_langs: C++
helpviewer_keywords: C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7b2c75e8222655404dbda9fdc751c57fdf4982a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4114"></a>Compilateur avertissement (niveau 1) C4114
même qualificateur de type utilisé plusieurs fois  
  
 Une définition ou déclaration de type utilise un qualificateur de type (**const**, `volatile`, **signé**, ou `unsigned`) plusieurs fois. Cela déclenche un avertissement avec les extensions Microsoft (/Ze) et une erreur sous compatibilité ANSI (/Za).  
  
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