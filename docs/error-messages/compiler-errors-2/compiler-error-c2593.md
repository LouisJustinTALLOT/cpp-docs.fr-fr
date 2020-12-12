---
description: 'En savoir plus sur : erreur du compilateur C2593'
title: Erreur du compilateur C2593
ms.date: 11/04/2016
f1_keywords:
- C2593
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
ms.openlocfilehash: 849cd79b1d469d957cf1bde499ce66bd54a64074
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120163"
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

Cette erreur peut être causée par la sérialisation d’une variable à virgule flottante à l’aide d’un `CArchive` objet. Le compilateur identifie l' `<<` opérateur comme ambigu. Les seuls types C++ primitifs qui `CArchive` peuvent être sérialisés sont les types de taille fixe `BYTE` , `WORD` , `DWORD` et `LONG` . Tous les types d’entiers doivent être castés en l’un de ces types pour la sérialisation. Les types à virgule flottante doivent être archivés à l’aide de la `CArchive::Write()` fonction membre.

L’exemple suivant montre comment archiver une variable à virgule flottante ( `f` ) à archiver `ar` :

```
ar.Write(&f, sizeof( float ));
```
