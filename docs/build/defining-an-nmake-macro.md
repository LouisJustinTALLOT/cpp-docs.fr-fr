---
title: Définition d'une macro NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
ms.openlocfilehash: 6eb7c2f7759bda21f1424cef91b1dc814ba8d8ba
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424104"
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
