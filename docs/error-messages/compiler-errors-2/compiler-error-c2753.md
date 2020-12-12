---
description: 'En savoir plus sur : erreur du compilateur C2753'
title: Erreur du compilateur C2753
ms.date: 11/04/2016
f1_keywords:
- C2753
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
ms.openlocfilehash: d7888086f81f26092d41be440f75ef60400229ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174401"
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
