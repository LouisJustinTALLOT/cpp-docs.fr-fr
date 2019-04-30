---
title: Avertissement du compilateur (niveau 3) C4240
ms.date: 11/04/2016
f1_keywords:
- C4240
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
ms.openlocfilehash: fe5306cc7909138fea0159553b53c2adc6a46dc0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402214"
---
# <a name="compiler-warning-level-3-c4240"></a>Avertissement du compilateur (niveau 3) C4240

extension non standard utilisée : accès à 'classname' défini maintenant comme 'spécificateur d’accès,' précédemment, il a été défini pour être le spécificateur d’accès

Sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), vous ne pouvez pas modifier l’accès à une classe imbriquée. Sous les extensions Microsoft par défaut (/Ze), vous pouvez avec cet avertissement.

## <a name="example"></a>Exemple

```
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