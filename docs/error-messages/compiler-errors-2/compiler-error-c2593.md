---
title: Erreur du compilateur C2593
ms.date: 11/04/2016
f1_keywords:
- C2593
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
ms.openlocfilehash: 2a385e35376ddce528678980705595bfb98aca95
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759345"
---
# <a name="compiler-error-c2593"></a>Erreur du compilateur C2593

'operator identifier’est ambigu

Plus d’un opérateur possible est défini pour un opérateur surchargé.

Cette erreur peut être résolue si vous utilisez un cast explicite sur un ou plusieurs paramètres réels.

L’exemple suivant génère l’C2593 :

```cpp
// C2593.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};
void operator+( X, X );
void operator+( A, B );
D d;

int main() {
   d +  d;         // C2593, D has an A, B, and X
   (X)d + (X)d;    // OK, uses operator+( X, X )
}
```

Cette erreur peut être causée par la sérialisation d’une variable à virgule flottante à l’aide d’un objet `CArchive`. Le compilateur identifie l’opérateur `<<` comme ambigu. Les seuls types C++ primitifs que `CArchive` pouvez sérialiser sont les types de taille fixe `BYTE`, `WORD`, `DWORD`et `LONG`. Tous les types d’entiers doivent être castés en l’un de ces types pour la sérialisation. Les types à virgule flottante doivent être archivés à l’aide de la fonction membre `CArchive::Write()`.

L’exemple suivant montre comment archiver une variable à virgule flottante (`f`) pour archiver des `ar`:

```
ar.Write(&f, sizeof( float ));
```
