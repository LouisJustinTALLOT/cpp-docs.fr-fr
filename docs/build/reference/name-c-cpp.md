---
title: NAME (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: c4888b8f9b6dba4b826f2ee7dda7529a4bdf1586
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414497"
---
# <a name="name-cc"></a>NAME (C/C++)

Spécifie un nom pour le fichier de sortie principal.

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>Notes

Méthode équivalente pour spécifier un nom de fichier de sortie est avec la [/OUT](../../build/reference/out-output-file-name.md) option de l’éditeur de liens et pour définir l’adresse de base d’une manière équivalente est avec la [/de BASE](../../build/reference/base-base-address.md) option de l’éditeur de liens. Si les deux sont spécifiés, / OUT remplace **nom**.

Si vous générez une DLL, le nom n’affecte que le nom de la DLL.

## <a name="see-also"></a>Voir aussi

[Règles s’appliquant aux instructions de définition de module](../../build/reference/rules-for-module-definition-statements.md)
