---
title: Caractères spéciaux dans les macros
ms.date: 11/04/2016
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
ms.openlocfilehash: aac7b07500d2a129194e7234210a590cb5d0f19a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825451"
---
# <a name="special-characters-in-macros"></a>Caractères spéciaux dans les macros

Le signe dièse (#) après qu’une définition indique un commentaire. Pour spécifier un signe dièse littéral dans une macro, utilisez un accent circonflexe (^), comme dans ^ #.

Un signe dollar ($) spécifie un appel de macro. Pour spécifier un $ littéral, utilisez $$.

Pour étendre une définition pour une nouvelle ligne, terminez la ligne par une barre oblique inverse (\\). Lorsque la macro est appelée, le caractère barre oblique inverse et saut de ligne est remplacé par un espace. Pour spécifier une barre oblique inverse littérale à la fin de la ligne, faites-le précéder d’un signe insertion (^), ou faites-le suivre avec un spécificateur de commentaire (#).

Pour spécifier un caractère de saut de ligne littéral, terminez la ligne avec un accent circonflexe (^), comme dans :

```
CMDS = cls^
dir
```

## <a name="see-also"></a>Voir aussi

[Définition d’une macro NMAKE](defining-an-nmake-macro.md)
