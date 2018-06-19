---
title: Erreur du compilateur C2243 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2243
dev_langs:
- C++
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16bc95540488b0723869c735b7fc80b15f6e763b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172587"
---
# <a name="compiler-error-c2243"></a>Erreur du compilateur C2243
La conversion 'type de conversion' de 'type1' en 'type2' existe, mais n'est pas accessible  
  
 La protection d'accès (`protected` ou `private`) a empêché la conversion d'un pointeur vers une classe dérivée en pointeur vers la classe de base.  
  
 L'exemple suivant génère l'erreur C2243 :  
  
```  
// C2243.cpp  
// compile with: /c  
class B {};  
class D : private B {};  
class E : public B {};  
  
D d;  
B *p = &d;   // C2243  
  
E e;  
B *p2 = &e;  
```  
  
 Les classes de base avec un accès `protected` ou `private` ne sont pas accessibles aux clients de la classe dérivée. Ces niveaux de contrôle d'accès permettent d'indiquer que la classe de base est un détail d'implémentation qui doit être invisible pour les clients. Utilisez une dérivation publique si vous souhaitez que les clients de la classe dérivée aient accès à une conversion implicite d'un pointeur de la classe dérivée en pointeur vers la classe de base.