---
description: 'En savoir plus sur : erreur du compilateur C2500'
title: Erreur du compilateur C2500
ms.date: 11/04/2016
f1_keywords:
- C2500
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
ms.openlocfilehash: 39d1ab0876470b443d4444a3c583cc0993c98325
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275969"
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
