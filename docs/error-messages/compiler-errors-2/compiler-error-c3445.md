---
title: Erreur du compilateur C3445
ms.date: 04/10/2017
f1_keywords:
- C3445
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
ms.openlocfilehash: 2eddeb5a56c953ca0864e29187fbe28c53bdee24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328643"
---
# <a name="compiler-error-c3445"></a>Erreur du compilateur C3445

> Copy-list-initialization de «*type*' ne peut pas utiliser un constructeur explicite

Selon la norme ISO C ++ 17 standard, le compilateur est requis pour prendre en compte un constructeur explicite pour la résolution de surcharge dans copy-list-initialization, mais doit générer une erreur si cette surcharge est choisie.

À partir de Visual Studio 2017, le compilateur recherche des erreurs liées à la création d’objets à l’aide d’une liste d’initialiseurs qui n’ont pas été trouvés par Visual Studio 2015. Ces erreurs risque d’incidents ou d’un comportement non défini lors de l’exécution.

## <a name="example"></a>Exemple

L’exemple suivant génère C3445.

```cpp
// C3445.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 };     // error C3445: copy-list-initialization of
                      //     'A' cannot use an explicit constructor
}
```

Pour corriger cette erreur, utilisez à la place une initialisation directe :

```cpp
// C3445b.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1{ 1 };
}
```
