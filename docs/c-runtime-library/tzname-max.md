---
title: TZNAME_MAX | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- TZNAME_MAX
dev_langs:
- C++
helpviewer_keywords:
- TZNAME_MAX constant
ms.assetid: e2286cb8-751d-4557-9650-5c4b98a8f7be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc44ff3178493132c1b8d5dc168cee6be4c5bc56
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990150"
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
