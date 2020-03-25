---
title: Avertissement du compilateur (niveau 4) C4032
ms.date: 11/04/2016
f1_keywords:
- C4032
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
ms.openlocfilehash: 84bfef28de2899a216616a6a5d9fb15422f2afec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185410"
---
# <a name="compiler-warning-level-4-c4032"></a>Avertissement du compilateur (niveau 4) C4032

le paramètre formel’Number’a un type différent lors de sa promotion

Le type de paramètre n’est pas compatible, par le biais des promotions par défaut, avec le type dans une déclaration précédente.

Il s’agit d’une erreur en C ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) et d’un avertissement sous les extensions Microsoft (/Ze).

## <a name="example"></a>Exemple

```c
// C4032.c
// compile with: /W4
void func();
void func(char);   // C4032, char promotes to int

int main()
{
}
```
