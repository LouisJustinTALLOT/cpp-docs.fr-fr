---
description: 'En savoir plus sur : erreur du compilateur C2071'
title: Erreur du compilateur C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: ec5a08150b322ca5ce3a973a4e65d71ed410e25b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323192"
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
