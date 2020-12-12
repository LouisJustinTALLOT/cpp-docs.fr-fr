---
description: 'En savoir plus sur : nom (C/C++)'
title: NAME (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: 7444aa20539b47b1f04d17a266a0b65a552af3f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137772"
---
# <a name="name-cc"></a>NAME (C/C++)

Spécifie un nom pour le fichier de sortie principal.

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>Notes

Une méthode équivalente pour spécifier un nom de fichier de sortie est avec l’option de l’éditeur de liens [/out](out-output-file-name.md) , et une méthode équivalente pour définir l’adresse de base est avec l’option de l’éditeur de liens [/base](base-base-address.md) . Si les deux sont spécifiés,/OUT remplace **Name**.

Si vous générez une DLL, le nom n’affecte que le nom de la DLL.

## <a name="see-also"></a>Voir aussi

[Règles pour les instructions Module-Definition](rules-for-module-definition-statements.md)
