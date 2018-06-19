---
title: Compilateur avertissement (niveau 2) C4309 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4309
dev_langs:
- C++
helpviewer_keywords:
- C4309
ms.assetid: cb3f41ef-fd8a-4def-baa1-924e751fca68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3cb98faf0c84210deb1a4c5164959d2ba4c08db9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300145"
---
# <a name="compiler-warning-level-2-c4309"></a>Avertissement du compilateur (niveau 2) C4309
'conversion' : troncation de valeur de constante  
  
 La conversion de type génère une constante dépasse l’espace alloué pour celle-ci. Vous devrez peut-être utiliser un type plus grand pour la constante.  
  
 L’exemple suivant génère l’erreur C4309 :  
  
```  
// C4309.cpp  
// compile with: /W2  
int main()  
{  
   char c = 128;   // C4309  
}  
```