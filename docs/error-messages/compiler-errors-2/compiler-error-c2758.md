---
title: Erreur du compilateur C2758 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2758
dev_langs:
- C++
helpviewer_keywords:
- C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34cce7840f888a4377440299a4dc5ac38ee6a1d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2758"></a>Erreur du compilateur C2758
'membre' : un membre de type référence const doit être initialisé  
  
 L'erreur du compilateur C2758 survient quand le constructeur n'initialise pas un membre du type de référence dans une liste d'initialiseurs. Le compilateur laisse le membre non défini. Les variables du membre de référence doivent être initialisées quand elles sont déclarées ou se voir attribuer une valeur dans la liste d'initialisation du constructeur.  
  
 L'exemple suivant génère l'erreur C2758 :  
  
```  
// C2758.cpp  
// Compile by using: cl /W3 /c C2758.cpp  
struct A {  
   const int i;  
  
   A(int n) { };   // C2758  
   // try the following line instead  
   // A(int n) : i{n} {};  
};  
```