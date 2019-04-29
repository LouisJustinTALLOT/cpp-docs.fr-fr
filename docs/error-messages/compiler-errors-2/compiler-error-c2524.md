---
title: Erreur du compilateur C2524
ms.date: 11/04/2016
f1_keywords:
- C2524
helpviewer_keywords:
- C2524
ms.assetid: e71d17f5-2fc2-416b-8dbd-e9bed85eb33a
ms.openlocfilehash: 369aa5f21c072472808ffba06c3bc5c5e608ac22
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282181"
---
# <a name="compiler-error-c2524"></a>Erreur du compilateur C2524

'destructeur' : un destructeur/finaliseur doit avoir une liste de paramètres 'void'

Le destructeur ou finaliseur avait une liste de paramètres qui n’est pas [void](../../cpp/void-cpp.md). Autres types de paramètres ne sont pas autorisés.

## <a name="example"></a>Exemple

Le code suivant reproduit l’erreur C2524.

```
// C2524.cpp
// compile with: /c
class A {
   A() {}
   ~A(int i) {}    // C2524
   // try the following line instead
   // ~A() {}
};
```

## <a name="example"></a>Exemple

Le code suivant reproduit l’erreur C2524.

```
// C2524_b.cpp
// compile with: /clr /c
ref struct I1 {
protected:
   !I1(int i);   // C2524
   // try the following line instead
   // !I1();
};
```