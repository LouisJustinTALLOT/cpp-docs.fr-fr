---
title: Erreur du compilateur C2754
ms.date: 11/04/2016
f1_keywords:
- C2754
helpviewer_keywords:
- C2754
ms.assetid: 1cab66c5-da9d-4b81-b7fb-9cdc48ff1ccc
ms.openlocfilehash: 179cbaf65bf6440a13da6b35c073af981b074c71
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759566"
---
# <a name="compiler-error-c2754"></a>Erreur du compilateur C2754

'spécialisation' : une spécialisation partielle ne peut pas avoir un paramètre de modèle sans type dépendant

Une tentative a été faite pour spécialiser partiellement une classe de modèle qui a un paramètre de modèle sans type dépendant. Cela n'est pas autorisé.

L’exemple suivant génère l’C2754 :

```cpp
// C2754.cpp
// compile with: /c

template<class T, T t>
struct A {};

template<class T, int N>
struct B {};

template<class T> struct A<T,5> {};   // C2754
template<> struct A<int,5> {};   // OK
template<class T> struct B<T,5> {};   // OK
```
