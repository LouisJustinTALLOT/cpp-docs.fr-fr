---
title: À l’aide d’une Macro NMAKE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0b68a5f3128b5d3780895f8080411819ed9b538
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712586"
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