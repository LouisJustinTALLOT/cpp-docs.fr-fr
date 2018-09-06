---
title: Erreur du compilateur C3850 | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3850
dev_langs:
- C++
helpviewer_keywords:
- C3850
ms.assetid: 028f3a37-f3ad-4ebc-9168-3cdea47524d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: daa4b6128672b47891c563acfd4399952a17e7e6
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894536"
---
# <a name="compiler-error-c3850"></a>Erreur du compilateur C3850

> «*char*' : un nom de caractère universel spécifie un caractère non valide

## <a name="remarks"></a>Notes

Les caractères représentés en tant que noms de caractères universels doivent représenter des points de code Unicode valides dans la plage 0-10FFFF. Un nom de caractère universel ne peut pas contenir une valeur dans la plage de substitution Unicode, D800-DFFF, ou une paire de substitution encodée. Le compilateur génère automatiquement la paire de substitution à partir d’un point de code valide.

Dans le code compilé en C, un nom de caractère universel ne peut pas représenter un caractère dans la plage 0000-009F, inclus, à l’exception de 0024 (« $»), 0040 («\@») et 0060 ('' ').

Dans du code compilé en C++, un nom de caractère universel peut utiliser n’importe quel point de code Unicode valide dans un littéral de chaîne ou de caractère. En dehors d’un littéral, un nom de caractère universel ne peut pas représenter un caractère de contrôle dans les plages 0000-001F ou 007F-009F (plages inclusives), ou un membre du jeu de caractères sources de base.  Pour plus d’informations, consultez [jeux de caractères](../../cpp/character-sets.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3850, et montre comment la corriger :

```cpp
// C3850.cpp
int main() {
   int \u0019 = 0;   // C3850, not in allowed range for an identifier
   const wchar_t * wstr_bad  = L"\UD840DC8A"; // C3850, UCN is surrogate pair
   const wchar_t * wstr_good = L"\U0002008A"; // Okay, UCN is valid code point
}
```