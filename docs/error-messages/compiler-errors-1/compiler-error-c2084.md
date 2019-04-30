---
title: Erreur du compilateur C2084
ms.date: 11/04/2016
f1_keywords:
- C2084
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
ms.openlocfilehash: 9aaf3a88e63234dfb842e4b48afd6e55595e96ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391918"
---
# <a name="compiler-error-c2084"></a>Erreur du compilateur C2084

fonction '*fonction*' a déjà un corps

La fonction a déjà été définie.

Dans les versions de Visual C++ antérieures à Visual Studio 2002,

- Le compilateur accepte plusieurs spécialisations de modèle résolu sur le même type, bien que les définitions supplémentaires ne seraient jamais disponibles. Le compilateur détecte maintenant ces définitions multiples.

- `__int32` et `int` étaient traitées comme des types distincts. Le compilateur traite désormais `__int32` comme synonyme de `int`. Cela signifie que le compilateur détecte plusieurs définitions si une fonction est surchargée sur les deux `__int32` et `int` et génère une erreur.

## <a name="example"></a>Exemple

L’exemple suivant génère C2084 :

```cpp
// C2084.cpp
void Func(int);
void Func(int) {}   // define function
void Func(int) {}   // C2084 second definition
```

Pour corriger cette erreur, supprimez la définition en double :

```
// C2084b.cpp
// compile with: /c
void Func(int);
void Func(int) {}
```