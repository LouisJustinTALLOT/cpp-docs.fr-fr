---
title: Erreur du compilateur C2084
ms.date: 11/04/2016
f1_keywords:
- C2084
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
ms.openlocfilehash: 881ae051b2779fe674b31b64a7cbe7be7cf63705
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757889"
---
# <a name="compiler-error-c2084"></a>Erreur du compilateur C2084

la fonction'*Function*'a déjà un corps

La fonction a déjà été définie.

Avant Visual Studio 2002,

- Le compilateur accepte plusieurs spécialisations de modèle qui se sont résolues vers le même type réel, bien que les définitions supplémentaires ne soient jamais disponibles. Le compilateur détecte maintenant ces plusieurs définitions.

- `__int32` et `int` ont été traités comme des types distincts. Le compilateur traite désormais `__int32` comme synonyme de `int`. Cela signifie que le compilateur détecte plusieurs définitions si une fonction est surchargée à la fois sur `__int32` et `int` et génère une erreur.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2084 :

```cpp
// C2084.cpp
void Func(int);
void Func(int) {}   // define function
void Func(int) {}   // C2084 second definition
```

Pour corriger cette erreur, supprimez la définition en double :

```cpp
// C2084b.cpp
// compile with: /c
void Func(int);
void Func(int) {}
```
