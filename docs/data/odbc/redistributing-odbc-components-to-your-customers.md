---
description: 'En savoir plus sur : redistribution des composants ODBC à vos clients'
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
ms.openlocfilehash: 02840156d648507065e0cadb1b8fa2b9c8146a7a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204314"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>Redistribution des composants ODBC à vos clients

Si vous incorporez les fonctionnalités des programmes d’administration ODBC dans votre application, vous devez également distribuer aux utilisateurs les fichiers qui exécutent ces programmes. Ces fichiers ODBC résident dans le répertoire \OS\System du CD-ROM Visual C++. Le fichier REDISTRB. wri et le contrat de licence dans le même répertoire contiennent une liste de fichiers ODBC que vous pouvez redistribuer.

Consultez la documentation relative aux pilotes ODBC que vous prévoyez d’envoyer. Vous devez déterminer les dll et autres fichiers à expédier. Vous devez également lire [redistribution des composants ODBC à vos clients](../../data/odbc/redistributing-odbc-components-to-your-customers.md), qui explique comment redistribuer les composants ODBC.

En outre, vous devez inclure un autre fichier dans la plupart des cas. La Odbccr32.dll est la bibliothèque de curseurs ODBC. Cette bibliothèque donne aux pilotes de niveau 1 la possibilité de faire défiler vers l’avant et vers l’arrière. Il offre également la possibilité de prendre en charge des instantanés. Pour plus d’informations sur la bibliothèque de curseurs ODBC, consultez [ODBC : bibliothèque de curseurs ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

Les rubriques suivantes fournissent plus d’informations sur l’utilisation d’ODBC avec les classes de base de données :

- [ODBC : bibliothèque de curseurs ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)

- [ODBC : configuration d’une source de données ODBC](../../data/odbc/odbc-configuring-an-odbc-data-source.md)

- [ODBC : appel direct de fonctions API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)

## <a name="see-also"></a>Voir aussi

[Notions de base relatives à ODBC](../../data/odbc/odbc-basics.md)<br/>
[Administrateur ODBC](../../data/odbc/odbc-administrator.md)
