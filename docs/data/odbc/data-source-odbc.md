---
description: 'En savoir plus sur : source de données (ODBC)'
title: Source de données (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
ms.openlocfilehash: 655ba48414a733c6f2704d51c0e2bf1d4edf3ff4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255676"
---
# <a name="data-source-odbc"></a>Source de données (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

En termes de base de données, une source de données est un ensemble spécifique de données, les informations requises pour accéder à ces données et l’emplacement de la source de données, qui peut être décrit à l’aide d’un nom de source de données. Pour utiliser la classe [CDatabase](../../mfc/reference/cdatabase-class.md), la source de données doit être celle que vous avez configurée via l’administrateur Open Database Connectivity (ODBC). Voici quelques exemples de sources de données : une base de données distante s’exécutant sur Microsoft SQL Server sur un réseau ou un fichier Microsoft Access dans un répertoire local. À partir de votre application, vous pouvez accéder à n’importe quelle source de données pour laquelle vous disposez d’un pilote ODBC.

Vous pouvez avoir une ou plusieurs sources de données actives dans votre application en même temps, chacune représentée par un `CDatabase` objet. Vous pouvez également disposer de plusieurs connexions simultanées à n’importe quelle source de données. Vous pouvez vous connecter à des sources de données locales et distantes, en fonction des pilotes installés et des fonctionnalités de vos pilotes ODBC. Pour plus d’informations sur les sources de données et l’administrateur ODBC, consultez [ODBC](../../data/odbc/odbc-basics.md) and [ODBC Administrator](../../data/odbc/odbc-administrator.md).

Les rubriques suivantes expliquent plus en détail les sources de données :

- [Source de données : gestion des connexions (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)

- [Source de données : détermination du schéma de la source de données (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)

## <a name="see-also"></a>Voir aussi

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
