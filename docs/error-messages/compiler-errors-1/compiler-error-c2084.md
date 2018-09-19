---
title: Erreur du compilateur C2084 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2084
dev_langs:
- C++
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09ce703b6908257e37c2b7ff1b2714f1426f941f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052105"
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