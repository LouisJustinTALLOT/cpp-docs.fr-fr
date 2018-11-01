---
title: Erreur du compilateur C2993
ms.date: 11/04/2016
f1_keywords:
- C2993
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
ms.openlocfilehash: 5be4836332f67f2064f60a3b058db159a18ca1e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605022"
---
# <a name="compiler-error-c2993"></a>Erreur du compilateur C2993

'identificateur' : type non conforme pour le paramètre de modèle sans type 'paramètre'

Vous ne pouvez pas déclarer un modèle avec une structure ou un argument d’union. Utiliser des pointeurs pour passer des structures et unions en tant que paramètres de modèle.

L’exemple suivant génère l’erreur C2993 :

```
// C2993.cpp
// compile with: /c
// C2993 expected
struct MyStruct {
   int a;char b;
};

template <class T, struct MyStruct S>   // C2993

// try the following line instead
// template <class T, struct MyStruct * S>
class CMyClass {};
```

Cette erreur sera également être due à la mise en conformité du compilateur dans Visual Studio .NET 2003 : les paramètres de modèle sans type ne sont plus autorisés à virgule flottante. La norme C++ n’autorise pas les paramètres de modèle sans type à virgule flottante.

Dans le cas d’un modèle de fonction, utilisez un argument de fonction à passer dans flottante point de paramètre de modèle sans type (ce code sera valide dans les versions de Visual Studio .NET 2003 et Visual Studio .NET de Visual C++). Dans le cas d’un modèle de classe, il n’existe aucune solution simple.

```
// C2993b.cpp
// compile with: /c
template<class T, float f> void func(T) {}   // C2993

// OK
template<class T>   void func2(T, float) {}
```