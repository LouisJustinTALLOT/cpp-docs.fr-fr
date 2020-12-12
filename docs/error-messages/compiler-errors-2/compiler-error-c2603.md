---
description: 'En savoir plus sur : erreur du compilateur C2603'
title: Erreur du compilateur C2603
ms.date: 11/04/2016
f1_keywords:
- C2603
helpviewer_keywords:
- C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
ms.openlocfilehash: e28ea581c4c1417972cddc0ce558bd518acb8889
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208786"
---
# <a name="compiler-error-c2603"></a>Erreur du compilateur C2603

> '*fonction*' : trop d’objets static de portée de bloc avec constructeur/destructeurs dans la fonction

Dans les versions du compilateur Microsoft C++ antérieures à Visual Studio 2015, ou lorsque l’option [de compilateur/Zc : threadSafeInit](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) est spécifiée, il existe une limite de 31 sur le nombre d’objets statiques que vous pouvez avoir dans une fonction inline visible de l’extérieur.

Pour résoudre ce problème, nous vous recommandons d’adopter une version plus récente de l’ensemble d’outils du compilateur Microsoft C++, ou, si possible, de supprimer l’option de compilateur/Zc : threadSafeInit-. Si ce n’est pas possible, envisagez de combiner vos objets statiques. Si les objets sont du même type, envisagez d’utiliser un tableau statique unique de ce type et référencez les membres individuels selon les besoins.

## <a name="example"></a>Exemple

Le code suivant génère C2603 et montre une façon de le résoudre :

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
