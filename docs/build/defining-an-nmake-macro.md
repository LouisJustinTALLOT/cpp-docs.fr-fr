---
title: Définition d’une Macro NMAKE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c266a0be1c5ff16b719e9055f79b377d13ffbf3c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715705"
---
# <a name="defining-an-nmake-macro"></a>Définition d'une macro NMAKE

## <a name="syntax"></a>Syntaxe

```

macroname=string
```

## <a name="remarks"></a>Notes

Le *nom_macro* est une combinaison de lettres, des chiffres et des traits de soulignement (_) jusqu'à 1 024 caractères et respecte la casse. Le *nom_macro* peut contenir une macro appelée. Si *nom_macro* se compose entièrement d’une macro appelée, la macro appelée ne peut pas être null ou non définie.

Le `string` peut être une séquence de zéro ou plusieurs caractères. Une chaîne null contient zéro caractères ou uniquement des espaces ou des tabulations. Le `string` peut contenir un appel de macro.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Caractères spéciaux dans les macros](../build/special-characters-in-macros.md)

[Macros nulles et non définies](../build/null-and-undefined-macros.md)

[Où définir des macros](../build/where-to-define-macros.md)

[Priorité dans les définitions de macro](../build/precedence-in-macro-definitions.md)

## <a name="see-also"></a>Voir aussi

[NMAKE et les macros](../build/macros-and-nmake.md)