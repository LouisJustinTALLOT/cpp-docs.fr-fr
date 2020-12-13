---
description: 'En savoir plus sur : erreur du compilateur C2524'
title: Erreur du compilateur C2524
ms.date: 11/04/2016
f1_keywords:
- C2524
helpviewer_keywords:
- C2524
ms.assetid: e71d17f5-2fc2-416b-8dbd-e9bed85eb33a
ms.openlocfilehash: 94e974674a5e244168499a50304a07264d23e618
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151136"
---
# <a name="compiler-error-c2524"></a>Erreur du compilateur C2524

'destructeur' : un destructeur/finaliseur doit avoir une liste de paramètres’void'

Le destructeur ou le finaliseur comportait une liste de paramètres qui n’est pas [void](../../cpp/void-cpp.md). Les autres types de paramètres ne sont pas autorisés.

## <a name="examples"></a>Exemples

Le code suivant reproduit C2524.

```cpp
// C2524.cpp
// compile with: /c
class A {
   A() {}
   ~A(int i) {}    // C2524
   // try the following line instead
   // ~A() {}
};
```

Le code suivant reproduit C2524.

```cpp
// C2524_b.cpp
// compile with: /clr /c
ref struct I1 {
protected:
   !I1(int i);   // C2524
   // try the following line instead
   // !I1();
};
```
