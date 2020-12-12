---
description: 'En savoir plus sur les constantes suivantes : setvbuf'
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
ms.openlocfilehash: 375c692f4437bd60c84e37c857e078d9386ffb1c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277009"
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
