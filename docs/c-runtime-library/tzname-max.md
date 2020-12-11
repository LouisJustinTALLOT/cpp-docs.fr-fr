---
description: 'En savoir plus sur : TZNAME_MAX'
title: TZNAME_MAX
ms.date: 10/22/2018
f1_keywords:
- TZNAME_MAX
helpviewer_keywords:
- TZNAME_MAX constant
ms.assetid: e2286cb8-751d-4557-9650-5c4b98a8f7be
ms.openlocfilehash: 1c426c82bd198998169c385366ae5188cabd02d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162129"
---
# <a name="tzname_max"></a>TZNAME_MAX

**Obsolète**. La longueur de chaîne maximale autorisée pour une variable de nom de fuseau horaire. Cette macro a été définie dans \<limits.h> dans Visual Studio 2012 et versions antérieures. Elle n’est pas définie dans Visual Studio 2013 et versions ultérieures. Pour obtenir la longueur nécessaire pour contenir le nom du fuseau horaire actuel, utilisez [_get_tzname](../c-runtime-library/reference/get-tzname.md).

## <a name="syntax"></a>Syntaxe

```
#include <limits.h>
```

## <a name="see-also"></a>Voir aussi

[Constantes environnementales](../c-runtime-library/environmental-constants.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)
