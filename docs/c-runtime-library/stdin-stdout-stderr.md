---
description: 'En savoir plus sur : stdin, stdout, stderr'
title: stdin, stdout, stderr
ms.date: 10/23/2018
f1_keywords:
- stdin
- stderr
- stdout
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
ms.openlocfilehash: ba31487c472bd714560e919f45ec9e9aa5acd717
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235721"
---
# <a name="stdin-stdout-stderr"></a>stdin, stdout, stderr

## <a name="syntax"></a>Syntaxe

```
FILE *stdin;
FILE *stdout;
FILE *stderr;
#include <stdio.h>
```

## <a name="remarks"></a>Notes

Il s’agit des flux standard pour l’entrée, la sortie et la sortie d’erreur.

Par défaut, une entrée standard est en lecture à partir du clavier, tandis que la sortie standard et l’erreur standard sont affichées à l’écran.

Les pointeurs de flux suivants sont disponibles pour accéder aux flux standard :

|Pointeur|STREAM|
|-------------|------------|
|`stdin`|Entrée standard|
|`stdout`|Sortie standard|
|`stderr`|Erreur standard|

Ces pointeurs peuvent être utilisés comme arguments pour fonctions. Certaines fonctions, telles que [getchar](../c-runtime-library/reference/getchar-getwchar.md) et [putchar](../c-runtime-library/reference/putchar-putwchar.md), utilisent `stdin` et `stdout` automatiquement.

Ces pointeurs sont des constantes et il n’est pas possible de leur affecter de nouvelles valeurs. La fonction [freopen](../c-runtime-library/reference/freopen-wfreopen.md) peut être utilisée pour rediriger les flux vers des fichiers sur disque ou d’autres appareils. Le système d’exploitation vous permet de rediriger l’entrée et la sortie standard d’un programme au niveau de la commande.

## <a name="see-also"></a>Voir aussi

[E/S de flux](../c-runtime-library/stream-i-o.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
