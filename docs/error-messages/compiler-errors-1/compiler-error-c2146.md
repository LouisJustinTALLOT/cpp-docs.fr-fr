---
title: Erreur du compilateur C2146
ms.date: 11/04/2016
f1_keywords:
- C2146
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
ms.openlocfilehash: 8dc7b521243c4eafdc22fab851812b6c12b004cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755913"
---
# <a name="compiler-error-c2146"></a>Erreur du compilateur C2146

erreur de syntaxe : absence de’Token’avant l’identificateur’identifier'

Le compilateur attendait `token` et a trouvé `identifier` à la place.  Causes possibles :

1. Erreur d’orthographe ou de mise en majuscules.

1. Spécificateur de type manquant dans la déclaration de l’identificateur.

Cette erreur peut être due à une erreur typographique. L’erreur [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) précède généralement cette erreur.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2146.

```cpp
// C2146.cpp
class CDeclaredClass {};

class CMyClass {
   CUndeclared m_myClass;   // C2146
   CDeclaredClass m_myClass2;   // OK
};

int main() {
   int x;
   int t x;   // C2146 : missing semicolon before 'x'
}
```

## <a name="example"></a>Exemple

Cette erreur peut également être générée en raison du travail de conformité du compilateur pour Visual Studio .NET 2003 : mot clé `typename` manquant.

L’exemple suivant compile dans Visual Studio .NET 2002, mais échoue dans Visual Studio .NET 2003 :

```cpp
// C2146b.cpp
// compile with: /c
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};

template <typename T>
X<T>::Y func() { }   // C2146

// OK
template <typename T>
typename X<T>::Y func() { }
```

## <a name="example"></a>Exemple

Vous verrez également cette erreur en raison du travail de conformité du compilateur pour Visual Studio .NET 2003 : les spécialisations explicites ne trouvent plus de paramètres de modèle à partir du modèle principal.

L’utilisation de `T` à partir du modèle principal n’est pas autorisée dans la spécialisation explicite. Pour que le code soit valide dans Visual Studio .NET 2003 et Visual Studio .NET, remplacez toutes les instances du paramètre de modèle dans la spécialisation par le type explicitement spécialisé.

L’exemple suivant compile dans Visual Studio .NET, mais échoue dans Visual Studio .NET 2003 :

```cpp
// C2146_c.cpp
// compile with: /c
template <class T>
struct S;

template <>
struct S<int> {
   T m_t;   // C2146
   int m_t2;   // OK
};
```
