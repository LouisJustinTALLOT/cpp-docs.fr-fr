---
title: Avertissement du compilateur (niveau 4) C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: 1ff669512f85dfed9bab307c2986e7858285461d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161384"
---
# <a name="compiler-warning-level-4-c4207"></a>Avertissement du compilateur (niveau 4) C4207

extension non standard utilisée : forme de l’initialiseur étendu

Avec les extensions Microsoft (/Ze), vous pouvez initialiser un tableau de `char` non dimensionné à l’aide d’une chaîne entre accolades.

## <a name="example"></a>Exemple

```c
// C4207.c
// compile with: /W4
char c[] = { 'a', 'b', "cdefg" }; // C4207

int main()
{
}
```

Ces initialisations ne sont pas valides sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
