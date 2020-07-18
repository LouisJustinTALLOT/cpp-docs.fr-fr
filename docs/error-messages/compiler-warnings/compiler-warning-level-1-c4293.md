---
title: Avertissement du compilateur (niveau 1) C4293
description: Décrit les causes de l’avertissement du compilateur MSVC C4293 et montre comment le résoudre.
ms.date: 07/15/2020
f1_keywords:
- C4293
helpviewer_keywords:
- C4293
ms.assetid: babecd96-eb51-41a5-9835-462c7a46dbad
ms.openlocfilehash: 3b5a05d4a744b084f1cc34210a5374962064e85d
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446474"
---
# <a name="compiler-warning-level-1-c4293"></a>Avertissement du compilateur (niveau 1) C4293

> '*opérateur*' : nombre de décalages négatif ou trop important, comportement non défini

Si un nombre de décalages est négatif ou trop grand, le comportement de l’image résultante n’est pas défini.

## <a name="remarks"></a>Remarques

Pour résoudre ce problème, vous pouvez utiliser un cast sur le premier opérande pour le développer jusqu’à la taille du type de résultat.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4293 et montre comment la corriger :

```cpp
// C4293.cpp
// compile with: /c /W1
unsigned __int64 combine (unsigned lo, unsigned hi)
{
   return (hi << 32) | lo;   // C4293

   // In C, try the following line instead:
   // return ( (unsigned __int64)hi << 32) | lo;
   // In C++, try this line instead:
   // return (static_cast<unsigned __int64>(hi) << 32) | lo;
}
```
