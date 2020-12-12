---
description: 'En savoir plus sur : utilisation d’une macro NMAKE'
title: Utilisation d'une macro NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
ms.openlocfilehash: 14a1856b411bf7608b94caacb1b0b078dd1f5577
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247005"
---
# <a name="using-an-nmake-macro"></a>Utilisation d'une macro NMAKE

Pour utiliser une macro, mettez son nom entre parenthèses précédé d’un signe dollar ($), comme suit.

## <a name="syntax"></a>Syntaxe

```
$(macroname)
```

## <a name="remarks"></a>Notes

Aucun espace n’est autorisé. Les parenthèses sont facultatives si *nommacro* est un caractère unique. La chaîne de définition remplace $ (*nommacro*); une macro non définie est remplacée par une chaîne NULL.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Substitution de macro](macro-substitution.md)

## <a name="see-also"></a>Voir aussi

[NMAKE et les macros](macros-and-nmake.md)
