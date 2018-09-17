---
title: Caractères spéciaux dans les Macros | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55a94001e2f912049518120911c25ae64afa24da
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721422"
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

[Définition d’une macro NMAKE](../build/defining-an-nmake-macro.md)