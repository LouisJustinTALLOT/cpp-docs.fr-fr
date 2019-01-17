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
ms.openlocfilehash: 8936789f4e3c9349e9d79616c8506c044dc79f70
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220398"
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
|`_IOFBF`|Mise en mémoire tampon totale : la mémoire tampon spécifiée dans l’appel à `setvbuf` est utilisée et sa taille est spécifiée dans l’appel `setvbuf`. Si le pointeur de la mémoire tampon est **NULL**, une mémoire tampon de la taille spécifiée automatiquement allouée est utilisée.|
|`_IOLBF`|Comme pour `_IOFBF`.|
|`_IONBF`|Aucune mémoire tampon n’est utilisée, quels que soient les arguments dans l’appel à `setvbuf`.|

## <a name="see-also"></a>Voir aussi

[setbuf](../c-runtime-library/reference/setbuf.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
