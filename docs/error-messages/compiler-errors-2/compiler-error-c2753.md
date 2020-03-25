---
title: Erreur du compilateur C2753
ms.date: 11/04/2016
f1_keywords:
- C2753
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
ms.openlocfilehash: ea2901c998ac1a44ad142779e7ce48bfffff66c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202148"
---
# <a name="compiler-error-c2753"></a>Erreur du compilateur C2753

'*template*' : une spécialisation partielle ne peut pas correspondre à la liste d’arguments pour le modèle principal

Si la liste d’arguments template correspond à la liste de paramètres, le compilateur la traite comme le même modèle. Le fait de définir deux fois le même modèle n’est pas autorisé.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2753 et montre un moyen de le corriger :

```cpp
// C2753.cpp
// compile with: cl /c C2753.cpp
template<class T>
struct A {};

template<class T>
struct A<T> {};   // C2753
// try the following line instead
// struct A<int> {};

template<class T, class U, class V, class W, class X>
struct B {};
```
