---
description: 'En savoir plus sur : caractères spéciaux dans les macros'
title: Caractères spéciaux dans les macros
ms.date: 11/04/2016
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
ms.openlocfilehash: 569aedbc474f660894b723f9356355e2360a4e61
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224658"
---
# <a name="special-characters-in-macros"></a>Caractères spéciaux dans les macros

Un signe dièse (#) après une définition spécifie un commentaire. Pour spécifier un signe dièse littéral dans une macro, utilisez le signe insertion (^), comme dans ^ #.

Un signe dollar ($) spécifie un appel de macro. Pour spécifier un littéral $, utilisez $ $.

Pour étendre une définition à une nouvelle ligne, terminez la ligne par une barre oblique inverse ( \\ ). Lorsque la macro est appelée, la barre oblique inverse plus le caractère de saut de ligne est remplacé par un espace. Pour spécifier une barre oblique inverse littérale à la fin de la ligne, faites-la précéder d’un signe d’insertion (^) ou faites-le suivre d’un spécificateur de commentaire (#).

Pour spécifier un caractère de saut de ligne littéral, terminez la ligne par un signe insertion (^), comme suit :

```
CMDS = cls^
dir
```

## <a name="see-also"></a>Voir aussi

[Définition d’une macro NMAKE](defining-an-nmake-macro.md)
