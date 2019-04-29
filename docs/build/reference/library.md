---
title: LIBRARY
ms.date: 11/04/2016
f1_keywords:
- LIBRARY
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
ms.openlocfilehash: b43f269726e8925abeefd41aab0edfd57b071035
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291091"
---
# <a name="library"></a>LIBRARY

Indique à LINK pour créer une DLL. En même temps, LINK crée une bibliothèque d’importation, sauf si un fichier .exp est utilisé dans la build.

```
LIBRARY [library][BASE=address]
```

## <a name="remarks"></a>Notes

Le *bibliothèque* argument spécifie le nom de la DLL. Vous pouvez également utiliser le [/OUT](out-output-file-name.md) option de l’éditeur de liens pour spécifier le nom de sortie de la DLL.

La BASE =*adresse* argument définit l’adresse de base du système d’exploitation utilise pour charger la DLL. Cet argument remplace l’emplacement de la DLL par défaut de 0 x 10000000. Consultez la description de la [/de BASE](base-base-address.md) option pour plus d’informations sur les adresses de base.

N’oubliez pas d’utiliser le [/DLL](dll-build-a-dll.md) option de l’éditeur de liens quand vous générez une DLL.

## <a name="see-also"></a>Voir aussi

[Règles s’appliquant aux instructions de définition de module](rules-for-module-definition-statements.md)
