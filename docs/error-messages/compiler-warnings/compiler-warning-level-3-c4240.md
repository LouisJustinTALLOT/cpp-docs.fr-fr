---
title: Avertissement du compilateur (niveau 3) C4240
ms.date: 11/04/2016
f1_keywords:
- C4240
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
ms.openlocfilehash: 3636e902e8d6ecd34cdc3e1135761c8595dc5998
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051756"
---
# <a name="compiler-warning-level-3-c4240"></a>Avertissement du compilateur (niveau 3) C4240

extension non standard utilisée : accès à’ClassName’défini à présent comme’spécificateur d’accès', précédemment défini comme’spécificateur d’accès'

Sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)), vous ne pouvez pas modifier l’accès à une classe imbriquée. Sous les extensions Microsoft par défaut (/Ze), vous pouvez, avec cet avertissement.

## <a name="example"></a>Exemple

```cpp
// C4240.cpp
// compile with: /W3
class X
{
private:
   class N;
public:
   class N
   {   // C4240
   };
};

int main()
{
}
```