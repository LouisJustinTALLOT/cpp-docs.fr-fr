---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4032'
title: Avertissement du compilateur (niveau 4) C4032
ms.date: 11/04/2016
f1_keywords:
- C4032
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
ms.openlocfilehash: 1c150bff398bbd2d6e5f1a8d21211f4c6b4cb6bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262098"
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
