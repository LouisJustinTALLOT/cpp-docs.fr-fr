---
description: 'En savoir plus sur : noinline'
title: noinline
ms.date: 11/04/2016
f1_keywords:
- noinline_cpp
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
ms.openlocfilehash: bc1241307e143a2de81cc99e6a934c83dcf89d23
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195383"
---
# <a name="noinline"></a>noinline

**Spécifique à Microsoft**

**`__declspec(noinline)`** indique au compilateur de ne jamais incorporer une fonction membre particulière (fonction dans une classe).

Il peut être préférable de ne pas incorporer une fonction si elle est petite et non essentielle pour les performances de votre code. Autrement dit, s'il s'agit d'une petite fonction et qu'il est probable qu'elle sera rarement appelée, comme par exemple une fonction qui gère une condition d'erreur.

N’oubliez pas que si une fonction est marquée **`noinline`** , la fonction appelante est plus petite et, par conséquent, elle est candidate à l’incorporation du compilateur.

```cpp
class X {
   __declspec(noinline) int mbrfunc() {
      return 0;
   }   // will not inline
};
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Inline, __inline, \_ _forceinline](inline-functions-cpp.md)
