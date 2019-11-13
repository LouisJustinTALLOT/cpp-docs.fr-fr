---
title: Avertissement du compilateur (niveau 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: e874e00d44eef29240cca55541837facfcf64495
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052041"
---
# <a name="compiler-warning-level-2-c4396"></a>Avertissement du compilateur (niveau 2) C4396

'nom' : le spécificateur inline ne peut pas être utilisé lorsqu’une déclaration friend se réfère à une spécialisation d’un modèle de fonction

Une spécialisation d’un modèle de fonction ne peut spécifier aucun des spécificateurs [inline](../../cpp/inline-functions-cpp.md) . Le compilateur émet l’avertissement C4396 et ignore le spécificateur inline.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez le spécificateur `inline`, `__inline`ou `__forceinline` de la déclaration de la fonction friend.

## <a name="example"></a>Exemple

L’exemple de code suivant montre une déclaration de fonction friend non valide avec un spécificateur `inline` .

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