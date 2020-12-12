---
description: 'En savoir plus sur : bibliothèque'
title: LIBRARY
ms.date: 11/04/2016
f1_keywords:
- LIBRARY
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
ms.openlocfilehash: 3d8c63f323568949cf2fb30935d2557755346422
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199530"
---
# <a name="library"></a>LIBRARY

Indique à LINK de créer une DLL. En même temps, LINK crée une bibliothèque d’importation, à moins qu’un fichier. exp ne soit utilisé dans la Build.

```
LIBRARY [library][BASE=address]
```

## <a name="remarks"></a>Notes

L’argument *Library* spécifie le nom de la dll. Vous pouvez également utiliser l’option de l’éditeur de liens [/out](out-output-file-name.md) pour spécifier le nom de sortie de la dll.

L’argument BASE =*Address* définit l’adresse de base utilisée par le système d’exploitation pour charger la dll. Cet argument remplace l’emplacement par défaut de la DLL 0x10000000. Pour plus d’informations sur les adresses de base, consultez la description de l’option [/base](base-base-address.md) .

N’oubliez pas d’utiliser l’option [/dll](dll-build-a-dll.md) de l’éditeur de liens lorsque vous générez une dll.

## <a name="see-also"></a>Voir aussi

[Règles pour les instructions Module-Definition](rules-for-module-definition-statements.md)
