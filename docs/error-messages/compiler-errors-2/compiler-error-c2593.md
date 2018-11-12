---
title: Erreur du compilateur C2593
ms.date: 11/04/2016
f1_keywords:
- C2593
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
ms.openlocfilehash: c358553a36104b5c389076f5a5ce02f94f85e85a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667309"
---
# <a name="compiler-error-c2593"></a>Erreur du compilateur C2593

'identificateur de l’opérateur' est ambigu

Plusieurs opérateurs possibles est défini pour un opérateur surchargé.

Cette erreur peut être résolue si vous utilisez un cast explicite sur un ou plusieurs paramètres réels.

L’exemple suivant génère l’erreur C2593 :

```
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

Cette erreur peut être provoquée par la sérialisation d’une variable à virgule flottante à l’aide un `CArchive` objet. Le compilateur identifie le `<<` opérateur comme ambiguë. Le C++ primitifs uniquement les types qui `CArchive` peut sérialiser sont les types de taille fixe `BYTE`, `WORD`, `DWORD`, et `LONG`. Tous les types d’entier doivent être castés en un de ces types pour la sérialisation. Les types à virgule flottante doivent être archivés à l’aide de la `CArchive::Write()` fonction membre.

L’exemple suivant montre comment archiver une variable à virgule flottante (`f`) à archive `ar`:

```
ar.Write(&f, sizeof( float ));
```