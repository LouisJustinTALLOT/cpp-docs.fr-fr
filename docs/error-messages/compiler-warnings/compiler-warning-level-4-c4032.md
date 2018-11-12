---
title: Compilateur avertissement (niveau 4) C4032
ms.date: 11/04/2016
f1_keywords:
- C4032
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
ms.openlocfilehash: fa1602d63ed9822725fea8e1b842929f221d3926
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657299"
---
# <a name="compiler-warning-level-4-c4032"></a>Compilateur avertissement (niveau 4) C4032

paramètre formel 'nombre' a un type différent lors de sa promotion

Le type de paramètre n’est pas compatible, par le biais des promotions par défaut, avec le type dans une déclaration précédente.

Il s’agit d’une erreur en C ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) et un avertissement sous extensions Microsoft (/Ze).

## <a name="example"></a>Exemple

```
// C4032.c
// compile with: /W4
void func();
void func(char);   // C4032, char promotes to int

int main()
{
}
```