---
description: 'En savoir plus sur : définition d’une macro NMAKE'
title: Définition d'une macro NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
ms.openlocfilehash: 133e05cac2a236a38f6b2d1e719f1b66fd73760d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201636"
---
# <a name="defining-an-nmake-macro"></a>Définition d'une macro NMAKE

## <a name="syntax"></a>Syntaxe

```

macroname=string
```

## <a name="remarks"></a>Notes

*Nommacro* est une combinaison de lettres, de chiffres et de traits de soulignement (_) jusqu’à 1 024 caractères, et respecte la casse. L’objet *nommacro* peut contenir une macro appelée. Si *nommacro* se compose entièrement d’une macro appelée, la macro appelée ne peut pas être null ou non définie.

`string`Peut être n’importe quelle séquence de zéro ou plusieurs caractères. Une chaîne NULL ne contient aucun caractère ou uniquement des espaces ou des tabulations. `string`Peut contenir un appel de macro.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Caractères spéciaux dans les macros](special-characters-in-macros.md)

[Macros null et non définies](null-and-undefined-macros.md)

[Où définir des macros](where-to-define-macros.md)

[Priorité dans les définitions de macros](precedence-in-macro-definitions.md)

## <a name="see-also"></a>Voir aussi

[NMAKE et les macros](macros-and-nmake.md)
