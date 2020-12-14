---
description: 'En savoir plus sur : erreur du compilateur C3850'
title: Erreur du compilateur C3850
ms.date: 09/05/2018
f1_keywords:
- C3850
helpviewer_keywords:
- C3850
ms.assetid: 028f3a37-f3ad-4ebc-9168-3cdea47524d4
ms.openlocfilehash: 9563ee8b4ebb2f8c08b67ff88401ef2e3022a03a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255338"
---
# <a name="compiler-error-c3850"></a>Erreur du compilateur C3850

> '*char*' : un nom de caractère universel spécifie un caractère non valide

## <a name="remarks"></a>Notes

Les caractères représentés en tant que noms de caractères universels doivent représenter des points de code Unicode valides dans la plage 0-10FFFF. Un nom de caractère universel ne peut pas contenir une valeur dans la plage de substitution Unicode, D800-DFFF, ou une paire de substitution encodée. Le compilateur génère automatiquement la paire de substitution à partir d’un point de code valide.

Dans le code compilé en tant que C, un nom de caractère universel ne peut pas représenter un caractère dans la plage 0000-009F, incluse, avec les exceptions de 0024 (' $ '), 0040 (' \@ ') et 0060 (' ' ').

Dans du code compilé en C++, un nom de caractère universel peut utiliser n’importe quel point de code Unicode valide dans un littéral de chaîne ou de caractère. En dehors d’un littéral, un nom de caractère universel ne peut pas représenter un caractère de contrôle dans les plages 0000-001F ou 007F-009F (plages inclusives), ou un membre du jeu de caractères sources de base.  Pour plus d'informations, consultez [Character Sets](../../cpp/character-sets.md).

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
