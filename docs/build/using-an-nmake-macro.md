---
title: Utilisation d'une macro NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
ms.openlocfilehash: a5f0fb9b13c5d5647b8f4ee382951df6282e8d68
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415641"
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

[Substitution de macro](../build/macro-substitution.md)

## <a name="see-also"></a>Voir aussi

[NMAKE et les macros](../build/macros-and-nmake.md)
