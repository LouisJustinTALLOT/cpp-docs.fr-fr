---
title: Avertissement du compilateur (niveau 4) C4623
ms.date: 11/04/2016
f1_keywords:
- C4623
helpviewer_keywords:
- C4623
ms.assetid: e630d8d0-f6ea-469c-a74f-07b027587225
ms.openlocfilehash: 4d0dd9aec19fb21870a1233cd3b713337fa15aaa
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990632"
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
