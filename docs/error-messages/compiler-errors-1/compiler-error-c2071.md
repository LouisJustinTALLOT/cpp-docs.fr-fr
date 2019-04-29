---
title: Erreur du compilateur C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 95344b5ef675f566f433dfeaed9dee5c38ef77d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303345"
---
# <a name="compiler-error-c2071"></a>Erreur du compilateur C2071

'identificateur' : classe de stockage non conforme

`identifier` a été déclaré avec un non valide [classe de stockage](../../c-language/c-storage-classes.md). Cette erreur peut survenir quand plusieurs classes de stockage sont spécifiées pour un même identificateur ou quand la définition est incompatible avec la déclaration de la classe de stockage.

Pour résoudre ce problème, identifiez la classe de stockage prévue de l’identificateur, par exemple, `static` ou `extern`— et corrigez la déclaration pour faire correspondre.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C2071.

```
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

```
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```