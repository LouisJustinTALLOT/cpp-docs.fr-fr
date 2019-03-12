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
ms.openlocfilehash: 28c9debf7e51d06cb9a625bb0a52d578ce3142c6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742657"
---
# <a name="setvbuf-constants"></a>setvbuf, constantes

## <a name="syntax"></a>Syntaxe

```
#include <stdio.h>
```

## <a name="remarks"></a>Remarques

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
