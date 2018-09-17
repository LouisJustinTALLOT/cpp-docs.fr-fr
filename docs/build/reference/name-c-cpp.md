---
title: NOM (C/C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- name
dev_langs:
- C++
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc37a96e50c6cd5bae2cc60661db04f3b92d162b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715752"
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