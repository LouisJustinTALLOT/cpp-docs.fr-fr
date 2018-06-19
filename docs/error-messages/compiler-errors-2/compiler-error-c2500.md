---
title: Erreur du compilateur C2500 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2500
dev_langs:
- C++
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c05ffd59e415375dd3c7f94ae9bc377c0fc2b9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229220"
---
# <a name="compiler-error-c2500"></a>Erreur du compilateur C2500
'identificateur1' : 'identificateur2' est déjà une classe de base directe  
  
 Une classe ou une structure apparaît plusieurs fois dans une liste de classes de base.  
  
 Une base directe est celui mentionné dans la liste de base. Une base indirecte est une classe de base de l’une des classes dans la liste de base.  
  
 Une classe ne peut pas être spécifiée plusieurs fois en tant que classe de base directe. Une classe peut être utilisée comme classe de base indirecte plusieurs fois.  
  
 L’exemple suivant génère C2500 :  
  
```  
// C2500.cpp  
// compile with: /c  
class A {};  
class B : public A, public A {};    // C2500  
  
// OK  
class C : public A {};  
class D : public A {};  
class E : public C, public D {};  
```