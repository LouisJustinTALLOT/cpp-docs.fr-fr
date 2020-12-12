---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4207'
title: Avertissement du compilateur (niveau 4) C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: fe442f71789533227a68a2f9059291de207e277b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173218"
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
