---
title: noinline
ms.date: 11/04/2016
f1_keywords:
- noinline_cpp
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
ms.openlocfilehash: e155726ad1f2f3f6f0501d3aebf7fa14e620d6bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377398"
---
# <a name="noinline"></a>noinline

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

**noinline** indique au compilateur de ne jamais inline une fonction membre particulière (fonction dans une classe).

Il peut être préférable de ne pas incorporer une fonction si elle est petite et non essentielle pour les performances de votre code. Autrement dit, s'il s'agit d'une petite fonction et qu'il est probable qu'elle sera rarement appelée, comme par exemple une fonction qui gère une condition d'erreur.

N’oubliez pas que si une fonction est marquée **noinline**, la fonction appelante sera plus petits et par conséquent, elle-même un candidat pour l’incorporation du compilateur.

```cpp
class X {
   __declspec(noinline) int mbrfunc() {
      return 0;
   }   // will not inline
};
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[inline, __inline, \__forceinline](inline-functions-cpp.md)
