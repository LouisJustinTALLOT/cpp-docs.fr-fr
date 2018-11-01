---
title: VERSION (C/C++)
ms.date: 11/04/2016
f1_keywords:
- VERSION
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
ms.openlocfilehash: 98758da627390ba4c7e852905457527a343baccc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667374"
---
# <a name="version-cc"></a>VERSION (C/C++)

Indique à LINK d’insérer un nombre dans l’en-tête du fichier .exe ou DLL.

```
VERSION major[.minor]
```

## <a name="remarks"></a>Notes

Le *majeure* et *mineure* arguments sont des nombres décimaux compris entre 0 et 65 535. La valeur par défaut est la version 0.0.

Vous pouvez spécifier un numéro de version est avec la [informations de Version](../../build/reference/version-version-information.md) (/ VERSION) option.

## <a name="see-also"></a>Voir aussi

[Règles s’appliquant aux instructions de définition de module](../../build/reference/rules-for-module-definition-statements.md)