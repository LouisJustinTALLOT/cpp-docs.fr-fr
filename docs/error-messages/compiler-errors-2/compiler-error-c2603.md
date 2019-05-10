---
title: Erreur du compilateur C2603
ms.date: 11/04/2016
f1_keywords:
- C2603
helpviewer_keywords:
- C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
ms.openlocfilehash: e4540180058c890a1dec9c4060f796f1f044c934
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447998"
---
# <a name="compiler-error-c2603"></a>Erreur du compilateur C2603

> «*fonction*» : Trop d’objets static de portée de bloc avec constructeur/destructeurs dans la fonction

Dans les versions de Microsoft C++ compilateur avant Visual Studio 2015, ou lorsque le [/Zc:threadSafeInit-](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) option du compilateur est spécifiée, il existe une limite de 31 sur le nombre d’objets statiques, vous pouvez avoir dans extérieurement visible fonction inline.

Pour résoudre ce problème, nous vous recommandons d’adopter une version plus récente de Microsoft C++ ensemble d’outils du compilateur, ou, si possible, supprimez l’option de compilateur /Zc:threadSafeInit-. Si ce n’est pas possible, envisagez de combiner vos objets statiques. Si les objets sont du même type, envisagez d’utiliser un tableau statique unique de ce type et référencer des membres individuels en fonction des besoins.

## <a name="example"></a>Exemple

Le code suivant génère C2603 et montre une façon de résoudre le problème :

```cpp
// C2603.cpp
// Compile by using: cl /W4 /c /Zc:threadSafeInit- C2603.cpp
struct C { C() {} };
extern inline void f1() {
    static C C01, C02, C03, C04, C05, C06, C07, C08, C09, C10;
    static C C11, C12, C13, C14, C15, C16, C17, C18, C19, C20;
    static C C21, C22, C23, C24, C25, C26, C27, C28, C29, C30, C31;
    static C C32;   // C2603 Comment this line out to avoid error
}
```
