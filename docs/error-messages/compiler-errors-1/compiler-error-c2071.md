---
title: Erreur du compilateur C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: cd815bf90b135f65072a56911c7c4b0f054fcfec
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87210070"
---
# <a name="compiler-error-c2071"></a>Erreur du compilateur C2071

'identificateur' : classe de stockage non conforme

`identifier`a été déclaré avec une [classe de stockage](../../c-language/c-storage-classes.md)non valide. Cette erreur peut survenir quand plusieurs classes de stockage sont spécifiées pour un même identificateur ou quand la définition est incompatible avec la déclaration de la classe de stockage.

Pour résoudre ce problème, comprenez la classe de stockage prévue de l’identificateur (par exemple, **`static`** ou **`extern`** ) et corrigez la déclaration pour qu’elle corresponde.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C2071.

```cpp
// C2071.cpp
// compile with: /c
struct C {
   extern int i;   // C2071
};
struct D {
   int i;   // OK, no extern on an automatic
};
```

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C2071.

```cpp
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```
