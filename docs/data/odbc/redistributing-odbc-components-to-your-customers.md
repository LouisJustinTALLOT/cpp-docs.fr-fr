---
title: Redistribution des composants ODBC à vos clients
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
ms.openlocfilehash: 1a6ec6f5fdd3c32080d357ca58d31ccea271b7a4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040086"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>Redistribution des composants ODBC à vos clients

Si vous incorporez la fonctionnalité des programmes de l’administrateur ODBC dans votre application, vous devez également distribuer à vos utilisateurs les fichiers qui exécutent ces programmes. Ces fichiers ODBC se trouvent dans le répertoire \OS\System du CD-ROM Visual C++. Le fichier Redistrb.wri et le contrat de licence dans le même répertoire contiennent une liste des fichiers ODBC que vous pouvez redistribuer.

Consultez la documentation pour les pilotes ODBC que vous prévoyez d’expédier. Vous devez déterminer quelles DLL et autres fichiers à expédier. Vous devez également lire [redistribution des composants ODBC à vos clients](../../data/odbc/redistributing-odbc-components-to-your-customers.md), qui explique comment redistribuer des composants ODBC.

En outre, vous devez inclure un autre fichier dans la plupart des cas. Le Odbccr32.dll est la bibliothèque de curseurs ODBC. Cette bibliothèque permet de pilotes de niveau 1 de défilement vers l’avant et vers l’arrière. Il offre également la fonctionnalité de prise en charge des captures instantanées. Pour plus d’informations sur la bibliothèque de curseurs ODBC, consultez [ODBC : La bibliothèque de curseurs ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

Les rubriques suivantes fournissent plus d’informations sur l’utilisation de ODBC avec les classes de base de données :

- [ODBC : La bibliothèque de curseurs ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)

- [ODBC : Configuration d’une Source de données ODBC](../../data/odbc/odbc-configuring-an-odbc-data-source.md)

- [ODBC : Appel direct de fonctions API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)

## <a name="see-also"></a>Voir aussi

[Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)<br/>
[Administrateur ODBC](../../data/odbc/odbc-administrator.md)