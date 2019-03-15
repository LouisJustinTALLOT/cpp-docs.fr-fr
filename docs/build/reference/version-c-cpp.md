---
title: VERSION (C/C++)
ms.date: 11/04/2016
f1_keywords:
- VERSION
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
ms.openlocfilehash: abc0b751440d09dcaad7e449d7b151b479c51911
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815149"
---
# <a name="version-cc"></a>VERSION (C/C++)

Indique à LINK d’insérer un nombre dans l’en-tête du fichier .exe ou DLL.

```
VERSION major[.minor]
```

## <a name="remarks"></a>Notes

Le *majeure* et *mineure* arguments sont des nombres décimaux compris entre 0 et 65 535. La valeur par défaut est la version 0.0.

Vous pouvez spécifier un numéro de version est avec la [informations de Version](version-version-information.md) (/ VERSION) option.

## <a name="see-also"></a>Voir aussi

[Règles s’appliquant aux instructions de définition de module](rules-for-module-definition-statements.md)
