---
title: Erreur du compilateur C2500 | Microsoft Docs
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
ms.openlocfilehash: 9b7e24ca520796b63171fe63c2bf841fe8776845
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026671"
---
# <a name="compiler-error-c2500"></a>Erreur du compilateur C2500

'identificateur1' : 'identificateur2' est déjà une classe de base directe

Une classe ou structure apparaît plusieurs fois dans une liste de classes de base.

Une base directe est celui mentionné dans la liste de base. Une base indirecte est une classe de base de l’une des classes dans la liste de base.

Une classe ne peut pas être spécifiée plusieurs fois en tant que classe de base directe. Une classe peut être utilisée en tant que classe de base indirecte plusieurs fois.

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