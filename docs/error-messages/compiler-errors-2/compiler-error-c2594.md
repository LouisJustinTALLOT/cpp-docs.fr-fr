---
title: Erreur du compilateur C2594 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2594
dev_langs: C++
helpviewer_keywords: C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d4cca18672aad77e051ff4428dc115c53cd5ddad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2594"></a>Erreur du compilateur C2594
'opérateur' : conversions ambiguës de 'type1' en 'type2'  
  
 Aucune conversion de *type1* à *type2* a été plus directe qu’une autre. Nous vous suggérons deux solutions possibles à la conversion de *type1* à *type2*. La première option consiste à définir une conversion directe de *type1* à *type2*, et la deuxième option consiste à spécifier une séquence de conversions de *type1* à  *type2*.  
  
 L’exemple suivant génère l’erreur C2594. La résolution suggérée pour l’erreur est une séquence de conversions :  
  
```  
// C2594.cpp  
// compile with: /c  
struct A{};  
struct I1 : A {};  
struct I2 : A {};  
struct D : I1, I2 {};  
  
A *f (D *p) {  
   return (A*) (p);    // C2594  
  
// try the following line instead  
// return static_cast<A *>(static_cast<I1 *>(p));  
}  
```