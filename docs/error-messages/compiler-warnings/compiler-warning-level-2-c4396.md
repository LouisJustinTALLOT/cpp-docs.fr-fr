---
title: Avertissement du compilateur (niveau 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: fec6875fdb2e8a60e71fe08da1ed4e8fa82e4641
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206040"
---
# <a name="compiler-warning-level-2-c4396"></a>Avertissement du compilateur (niveau 2) C4396

'nom' : le spécificateur inline ne peut pas être utilisé lorsqu’une déclaration friend se réfère à une spécialisation d’un modèle de fonction

Une spécialisation d’un modèle de fonction ne peut spécifier aucun des spécificateurs [inline](../../cpp/inline-functions-cpp.md) . Le compilateur émet l’avertissement C4396 et ignore le spécificateur inline.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez **`inline`** le **`__inline`** spécificateur, ou **`__forceinline`** de la déclaration de la fonction friend.

## <a name="example"></a>Exemple

L’exemple de code suivant montre une déclaration de fonction friend non valide avec un **`inline`** spécificateur.

```cpp
// C4396.cpp
// compile with: /W2 /c

class X;
template<class T> void Func(T t, int i);

class X {
    friend inline void Func<char>(char t, int i);  //C4396
// try the following line instead
//    friend void Func<char>(char t, int i);
    int i;
};
```
