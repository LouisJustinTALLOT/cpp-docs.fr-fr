---
title: TZNAME_MAX
ms.date: 10/22/2018
f1_keywords:
- TZNAME_MAX
helpviewer_keywords:
- TZNAME_MAX constant
ms.assetid: e2286cb8-751d-4557-9650-5c4b98a8f7be
ms.openlocfilehash: 71e5becd39f49d86573483c5451a9a2415d84181
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750934"
---
# <a name="tznamemax"></a>TZNAME_MAX

**Obsolète**. La longueur de chaîne maximale autorisée pour une variable de nom de fuseau horaire. Cette macro était définie dans \<limits.h> dans Visual Studio 2012 et versions antérieures. Elle n’est pas définie dans Visual Studio 2013 et versions ultérieures. Pour obtenir la longueur nécessaire pour contenir le nom du fuseau horaire actuel, utilisez [_get_tzname](../c-runtime-library/reference/get-tzname.md).

## <a name="syntax"></a>Syntaxe

```
#include <limits.h>
```

## <a name="see-also"></a>Voir aussi

[Constantes d’environnement](../c-runtime-library/environmental-constants.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)
