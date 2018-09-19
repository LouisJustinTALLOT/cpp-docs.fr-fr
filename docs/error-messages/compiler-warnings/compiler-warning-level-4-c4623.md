---
title: Compilateur avertissement (niveau 4) C4623 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4623
dev_langs:
- C++
helpviewer_keywords:
- C4623
ms.assetid: e630d8d0-f6ea-469c-a74f-07b027587225
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: beb890483db5ef9e979f6eb790f811ae6822e42b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118594"
---
# <a name="compiler-warning-level-4-c4623"></a>Avertissement du compilateur (niveau 4) C4623

'`derived class`' : le constructeur par défaut a été défini de manière implicite comme supprimé, car un constructeur par défaut de la classe de base est inaccessible ou supprimé

Un constructeur n'était pas accessible dans une classe de base et n'a pas été généré pour la classe dérivée. Toute tentative pour créer un objet de ce type dans la pile provoquera une erreur du compilateur.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

## <a name="example"></a>Exemple

L'exemple suivant génère l'avertissement C4623.

```
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