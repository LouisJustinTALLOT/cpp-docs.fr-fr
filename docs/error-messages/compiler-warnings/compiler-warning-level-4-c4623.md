---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4623'
title: Avertissement du compilateur (niveau 4) C4623
ms.date: 11/04/2016
f1_keywords:
- C4623
helpviewer_keywords:
- C4623
ms.assetid: e630d8d0-f6ea-469c-a74f-07b027587225
ms.openlocfilehash: 3e10b83af1ba38d50307abdc87f3fde3b9b30417
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134236"
---
# <a name="compiler-warning-level-4-c4623"></a>Avertissement du compilateur (niveau 4) C4623

'`derived class`' : le constructeur par défaut a été défini de manière implicite comme supprimé, car un constructeur par défaut de la classe de base est inaccessible ou supprimé

Un constructeur n'était pas accessible dans une classe de base et n'a pas été généré pour la classe dérivée. Toute tentative pour créer un objet de ce type dans la pile provoquera une erreur du compilateur.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

## <a name="example"></a>Exemple

L'exemple suivant génère l'avertissement C4623.

```cpp
// C4623.cpp
// compile with: /W4
#pragma warning(default : 4623)
class B {
   B();
};

class C {
public:
   C();
};

class D : public B {};   // C4623 - to fix, make B's constructor public
class E : public C {};   // OK - class C constructor is public

int main() {
   // D d;  will cause an error
}
```
