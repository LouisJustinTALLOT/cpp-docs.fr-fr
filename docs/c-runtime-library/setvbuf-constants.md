---
title: setvbuf, constantes
ms.date: 11/04/2016
f1_keywords:
- _IOFBF
- _IONBF
- _IOLBF
helpviewer_keywords:
- _IOFBF constant
- IOFBF constant
- IONBF constant
- _IOLBF constant
- IOLBF constant
- _IONBF constant
ms.assetid: a6ec4dd5-1f24-498c-871a-e874cd28d33c
ms.openlocfilehash: 661cf64c71e06c222503388df198d47429566602
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523804"
---
# <a name="setvbuf-constants"></a>setvbuf, constantes

## <a name="syntax"></a>Syntaxe

```

#include <stdio.h>
```

## <a name="remarks"></a>Notes

Ces constantes représentent le type de mémoire tampon pour `setvbuf`.

Les valeurs possibles sont données par les constantes manifestes suivantes :

|Constante|Signification|
|--------------|-------------|
|`_IOFBF`|Mise en mémoire tampon complète : la mémoire tampon spécifiée dans l’appel à `setvbuf` est utilisée et sa taille est spécifiée dans l’appel `setvbuf`. Si le pointeur de la mémoire tampon est **NULL**, une mémoire tampon de la taille spécifiée automatiquement allouée est utilisée.|
|`_IOLBF`|Comme pour `_IOFBF`.|
|`_IONBF`|Aucune mémoire tampon n’est utilisée, quels que soient les arguments dans l’appel à `setvbuf`.|

## <a name="see-also"></a>Voir aussi

[setbuf](../c-runtime-library/reference/setbuf.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)