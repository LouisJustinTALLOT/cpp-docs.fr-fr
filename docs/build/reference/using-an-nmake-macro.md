---
title: Utilisation d'une macro NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
ms.openlocfilehash: fb3b154ba8b30bbfc9a6c7c6b37720e5c60d6327
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825774"
---
# <a name="using-an-nmake-macro"></a>Utilisation d'une macro NMAKE

Pour utiliser une macro, mettez son nom entre parenthèses précédées du signe dollar ($) comme suit.

## <a name="syntax"></a>Syntaxe

```
$(macroname)
```

## <a name="remarks"></a>Notes

Sans les espaces sont autorisés. Les parenthèses sont facultatives si *nom_macro* est un caractère unique. La chaîne de définition remplace $(*nom_macro*) ; une macro non définie est remplacée par une chaîne null.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Substitution de macro](macro-substitution.md)

## <a name="see-also"></a>Voir aussi

[NMAKE et les macros](macros-and-nmake.md)
