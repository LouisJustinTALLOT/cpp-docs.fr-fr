---
description: 'En savoir plus sur : erreur du compilateur C3445'
title: Erreur du compilateur C3445
ms.date: 04/10/2017
f1_keywords:
- C3445
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
ms.openlocfilehash: 992c0e4f6e8b068bf6c038a6a5f58b45dd80a3c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316032"
---
# <a name="compiler-error-c3445"></a>Erreur du compilateur C3445

> l’initialisation de copie de liste de'*type*'ne peut pas utiliser un constructeur explicite

Selon la norme ISO C++ 17, le compilateur est tenu de prendre en compte un constructeur explicite pour la résolution de surcharge dans l’initialisation de copie-liste, mais doit déclencher une erreur si cette surcharge est réellement choisie.

À compter de Visual Studio 2017, le compilateur détecte les erreurs liées à la création d’objets à l’aide d’une liste d’initialiseurs qui n’a pas été trouvée par Visual Studio 2015. Ces erreurs peuvent entraîner des blocages ou un comportement non défini au moment de l’exécution.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3445.

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

Pour corriger l’erreur, utilisez l’initialisation directe à la place :

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
