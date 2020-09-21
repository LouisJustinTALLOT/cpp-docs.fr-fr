---
title: Erreur du compilateur C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 7619d968379bfc35e98bd87071b75296d10c382c
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743280"
---
# <a name="compiler-error-c2071"></a>Erreur du compilateur C2071

'identificateur' : classe de stockage non conforme

`identifier` a été déclaré avec une [classe de stockage](../../c-language/c-storage-classes.md)non valide. Cette erreur peut survenir quand plusieurs classes de stockage sont spécifiées pour un même identificateur ou quand la définition est incompatible avec la déclaration de la classe de stockage.

Pour résoudre ce problème, comprenez la classe de stockage prévue de l’identificateur (par exemple, **`static`** ou **`extern`** ) et corrigez la déclaration pour qu’elle corresponde.

## <a name="examples"></a>Exemples

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

L'exemple suivant génère l'erreur C2071.

```cpp
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```
