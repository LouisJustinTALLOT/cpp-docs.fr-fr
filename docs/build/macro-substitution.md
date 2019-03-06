---
title: Substitution macro
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
ms.openlocfilehash: d82aed5a34b7cafad0e40146470972dc6ff02424
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414679"
---
# <a name="macro-substitution"></a>Substitution macro

Lorsque *nom_macro* est appelé, chaque occurrence de *string1* dans sa définition de la chaîne est remplacée par *string2*.

## <a name="syntax"></a>Syntaxe

```
$(macroname:string1=string2)
```

## <a name="remarks"></a>Notes

Substitution de macro respecte la casse et est littérale ; *string1* et *string2* ne peut pas appeler des macros. Substitution ne modifie pas la définition d’origine. Vous pouvez remplacer le texte dans une macro prédéfinie à l’exception [ $$@ ](../build/filename-macros.md).

Aucune espaces ou des tabulations, faites précéder le signe deux-points ; ceux-ci sont interprétés en tant que littéral. Si *string2* est null, toutes les occurrences de *string1* sont supprimés de la chaîne de définition de macro.

## <a name="see-also"></a>Voir aussi

[Utilisation d’une macro NMAKE](../build/using-an-nmake-macro.md)
