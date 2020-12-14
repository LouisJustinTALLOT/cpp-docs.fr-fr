---
description: 'En savoir plus sur : substitution de macro'
title: Substitution macro
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
ms.openlocfilehash: 5e1531afb210b4671632bca2540bfc7562653139
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199179"
---
# <a name="macro-substitution"></a>Substitution macro

Lorsque *nommacro* est appelé, chaque occurrence de *Chaîne1* dans sa chaîne de définition est remplacée par *Chaîne2*.

## <a name="syntax"></a>Syntaxe

```
$(macroname:string1=string2)
```

## <a name="remarks"></a>Notes

La substitution de macro est sensible à la casse et est littérale ; *Chaîne1* et *Chaîne2* ne peuvent pas appeler de macros. La substitution ne modifie pas la définition d’origine. Vous pouvez remplacer du texte dans n’importe quelle macro prédéfinie, à l’exception de [$$@](filename-macros.md) .

Aucun espace ou tabulation ne précède le signe deux-points ; tout après le signe deux-points est interprété comme littéral. Si *string2* a la valeur null, toutes les occurrences de *string1* sont supprimées de la chaîne de définition de la macro.

## <a name="see-also"></a>Voir aussi

[Utilisation d’une macro NMAKE](using-an-nmake-macro.md)
