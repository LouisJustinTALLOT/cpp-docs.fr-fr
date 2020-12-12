---
description: 'En savoir plus sur : VERSION (C/C++)'
title: VERSION (C/C++)
ms.date: 11/04/2016
f1_keywords:
- VERSION
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
ms.openlocfilehash: 1a63435c752220ab9fef54628ab101a14ef58582
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176390"
---
# <a name="version-cc"></a>VERSION (C/C++)

Indique à LINK de placer un nombre dans l’en-tête du fichier. exe ou de la DLL.

```
VERSION major[.minor]
```

## <a name="remarks"></a>Notes

Les arguments *major* et *Minor* sont des nombres décimaux compris entre 0 et 65 535. La valeur par défaut est la version 0,0.

Une méthode équivalente pour spécifier un numéro de version est avec l’option [informations sur la version](version-version-information.md) (/version).

## <a name="see-also"></a>Voir aussi

[Règles pour les instructions Module-Definition](rules-for-module-definition-statements.md)
