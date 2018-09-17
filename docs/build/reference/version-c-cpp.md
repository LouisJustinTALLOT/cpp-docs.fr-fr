---
title: VERSION (C/C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VERSION
dev_langs:
- C++
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7330d979e841d952f7e800e52ae762256ede6808
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718300"
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