---
title: Erreur du compilateur C2500
ms.date: 11/04/2016
f1_keywords:
- C2500
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
ms.openlocfilehash: 152546fce8f3ee63f8b95595bff052f18cd4ebda
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746966"
---
# <a name="compiler-error-c2500"></a>Erreur du compilateur C2500

'identificateur1 ' : 'identificateur2 'est déjà une classe de base directe

Une classe ou une structure apparaît plusieurs fois dans une liste de classes de base.

Une base directe est un mentionné dans la liste de base. Une base indirecte est une classe de base de l’une des classes de la liste de base.

Une classe ne peut pas être spécifiée plus d’une fois en tant que classe de base directe. Une classe peut être utilisée plusieurs fois en tant que classe de base indirecte.

L’exemple suivant génère l’C2500 :

```cpp
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```
