---
title: stdin, stdout, stderr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- stdin
- stderr
- stdout
dev_langs:
- C++
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a36d5fd60a19222e6f802e5a14037fb01ff865f5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071976"
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

|Pointeur|Flux|
|-------------|------------|
|`stdin`|Entrée standard|
|**stdout**|Objet de flux de sortie standard|
|`stderr`|Erreur standard|

Ces pointeurs peuvent être utilisés comme arguments pour fonctions. Certaines fonctions, telles que **getchar** et `putchar`, utilisent `stdin` et **stdout** automatiquement.

Ces pointeurs sont des constantes et il n’est pas possible de leur affecter de nouvelles valeurs. La fonction `freopen` peut être utilisée pour rediriger les flux vers des fichiers sur disque ou d’autres appareils. Le système d’exploitation vous permet de rediriger l’entrée et la sortie standard d’un programme au niveau de la commande.

## <a name="see-also"></a>Voir aussi

[E/S de flux](../c-runtime-library/stream-i-o.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)