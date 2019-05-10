---
title: Erreur du compilateur C2146
ms.date: 11/04/2016
f1_keywords:
- C2146
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
ms.openlocfilehash: f00de0ce491d517da11f251b89ccb9a7ae66b77d
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447267"
---
# <a name="compiler-error-c2146"></a>Erreur du compilateur C2146

Erreur de syntaxe : absence de 'jeton' avant l’identificateur 'identificateur'

Le compilateur attendu `token` et trouvé `identifier` à la place.  Causes possibles :

1. Erreur d’orthographe ou de mise en majuscules.

1. Spécificateur de type manquant dans la déclaration de l’identificateur.

Cette erreur peut être dû à une faute de frappe. Erreur [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) précède généralement cette erreur.

## <a name="example"></a>Exemple

L’exemple suivant génère C2146.

```
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

Cette erreur peut également être due à la mise en conformité du compilateur pour Visual Studio .NET 2003 : manquant `typename` mot clé.

L’exemple suivant se compile dans Visual Studio .NET 2002, mais échoue dans Visual Studio .NET 2003 :

```
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

Vous recevez également cette erreur en raison du travail la conformité du compilateur pour Visual Studio .NET 2003 : des spécialisations explicites ne trouve plus les paramètres de modèle à partir du modèle principal.

L’utilisation de `T` à partir du modèle principal n’est pas autorisée dans la spécialisation explicite. Pour le code soit valide dans le Visual Studio .NET 2003 et Visual Studio .NET, remplacez toutes les instances du paramètre de modèle dans la spécialisation par le type explicitement spécialisé.

L’exemple suivant se compile dans Visual Studio .NET, mais échoue dans Visual Studio .NET 2003 :

```
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