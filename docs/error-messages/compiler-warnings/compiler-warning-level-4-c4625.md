---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4625'
title: Avertissement du compilateur (niveau 4) C4625
ms.date: 11/04/2016
f1_keywords:
- C4625
helpviewer_keywords:
- C4625
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
ms.openlocfilehash: 1b154e1f2e52c21affd47c1b0fc30d29b290269e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134223"
---
# <a name="compiler-warning-level-4-c4625"></a>Avertissement du compilateur (niveau 4) C4625

'classe dérivée' : le constructeur de copie a été défini de manière implicite comme supprimé car un constructeur de copie de la classe de base est inaccessible ou supprimé

Un constructeur de copie a été supprimé ou n'était pas accessible dans une classe de base, et il n'a donc pas été généré pour une classe dérivée. Toute tentative pour copier un objet de ce type provoquera une erreur du compilateur.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C4625 et montre comment la corriger.

```cpp
// C4625.cpp
// compile with: /W4 /c
#pragma warning(default : 4625)

struct A {
   A() {}

private:
   A(const A&) {}
};

struct C : private virtual A {};
struct B :  C {};   // C4625 no copy constructor

struct D : A {};
struct E :  D {};   // OK
```
