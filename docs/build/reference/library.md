---
title: LIBRARY
ms.date: 11/04/2016
f1_keywords:
- LIBRARY
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
ms.openlocfilehash: 73609be698719da05fff357ba80200c49f598add
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422662"
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
