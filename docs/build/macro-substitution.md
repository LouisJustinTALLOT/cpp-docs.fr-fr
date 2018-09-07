---
title: Substitution de macro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f71ef2e1a8f337a4cd415169b6f9d817042f19a
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894393"
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