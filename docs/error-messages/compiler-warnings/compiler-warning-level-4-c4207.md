---
title: Avertissement du compilateur (niveau 4) C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: e694f96d7f6271686d1b2a19e5a12e5e08e1cfbe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219948"
---
# <a name="compiler-warning-level-4-c4207"></a>Avertissement du compilateur (niveau 4) C4207

extension non standard utilisée : forme de l’initialiseur étendu

Avec les extensions Microsoft (/Ze), vous pouvez initialiser un tableau non dimensionné de **`char`** à l’aide d’une chaîne entre accolades.

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
