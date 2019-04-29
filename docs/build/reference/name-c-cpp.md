---
title: NAME (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: d0813befc622db72e095c449794405fc5d58465b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320576"
---
# <a name="name-cc"></a>NAME (C/C++)

Spécifie un nom pour le fichier de sortie principal.

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>Notes

Méthode équivalente pour spécifier un nom de fichier de sortie est avec la [/OUT](out-output-file-name.md) option de l’éditeur de liens et pour définir l’adresse de base d’une manière équivalente est avec la [/de BASE](base-base-address.md) option de l’éditeur de liens. Si les deux sont spécifiés, / OUT remplace **nom**.

Si vous générez une DLL, le nom n’affecte que le nom de la DLL.

## <a name="see-also"></a>Voir aussi

[Règles s’appliquant aux instructions de définition de module](rules-for-module-definition-statements.md)
