---
title: Avertissement du compilateur (niveau 4) C4214
ms.date: 11/04/2016
f1_keywords:
- C4214
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
ms.openlocfilehash: 70dadb7d424352fbde8c5904053b22fe7cc6b77e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161280"
---
# <a name="compiler-warning-level-4-c4214"></a>Avertissement du compilateur (niveau 4) C4214

extension non standard utilisée : types de champs de bits autres que int

Avec les extensions Microsoft par défaut (/Ze), les membres de structure de champ de valeurs peuvent être de n’importe quel type entier.

## <a name="example"></a>Exemple

```c
// C4214.c
// compile with: /W4
struct bitfields
{
   unsigned short j:4;  // C4214
};

int main()
{
}
```

Ces champs de bits ne sont pas valides sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
