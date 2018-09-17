---
title: BIBLIOTHÈQUE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- LIBRARY
dev_langs:
- C++
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43b14e8e8ff4871ba4319c7f4fac5545e72e710b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723552"
---
# <a name="library"></a>LIBRARY

Indique à LINK pour créer une DLL. En même temps, LINK crée une bibliothèque d’importation, sauf si un fichier .exp est utilisé dans la build.

```
LIBRARY [library][BASE=address]
```

## <a name="remarks"></a>Notes

Le *bibliothèque* argument spécifie le nom de la DLL. Vous pouvez également utiliser le [/OUT](../../build/reference/out-output-file-name.md) option de l’éditeur de liens pour spécifier le nom de sortie de la DLL.

La BASE =*adresse* argument définit l’adresse de base du système d’exploitation utilise pour charger la DLL. Cet argument remplace l’emplacement de la DLL par défaut de 0 x 10000000. Consultez la description de la [/de BASE](../../build/reference/base-base-address.md) option pour plus d’informations sur les adresses de base.

N’oubliez pas d’utiliser le [/DLL](../../build/reference/dll-build-a-dll.md) option de l’éditeur de liens quand vous générez une DLL.

## <a name="see-also"></a>Voir aussi

[Règles s’appliquant aux instructions de définition de module](../../build/reference/rules-for-module-definition-statements.md)