---
title: Erreur du compilateur C2993
ms.date: 11/04/2016
f1_keywords:
- C2993
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
ms.openlocfilehash: 5aa0d27b2d469f53ec521f587172398b7d4c2d1b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761229"
---
# <a name="compiler-error-c2993"></a>Erreur du compilateur C2993

'identificateur' : type non conforme pour le paramètre de modèle sans type’paramètre'

Vous ne pouvez pas déclarer un modèle avec un argument de structure ou d’Union. Utilisez des pointeurs pour passer des structures et des unions en tant que paramètres de modèle.

L’exemple suivant génère l’C2993 :

```cpp
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

Cette erreur est également générée en raison du travail de mise en conformité du compilateur effectué dans Visual Studio .NET 2003 : les paramètres de modèle sans type à virgule flottante ne sont plus autorisés. La C++ norme n’autorise pas les paramètres de modèle sans type à virgule flottante.

S’il s’agit d’un modèle de fonction, utilisez un argument de fonction pour passer le paramètre de modèle sans type à virgule flottante (ce code sera valide dans les versions Visual Studio .NET 2003 et Visual C++Studio .net de Visual). S’il s’agit d’un modèle de classe, il n’existe pas de solution de contournement facile.

```cpp
// C2993b.cpp
// compile with: /c
template<class T, float f> void func(T) {}   // C2993

// OK
template<class T>   void func2(T, float) {}
```
