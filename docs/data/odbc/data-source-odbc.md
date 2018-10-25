---
title: Source de données (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 39c017113d6f3da0041b5e460666af955c27b0fa
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066147"
---
# <a name="data-source-odbc"></a>Source de données (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

En termes de base de données, une source de données est un ensemble spécifique de données, les informations requises pour accéder à ces données et l’emplacement de la source de données, qui peut être décrits à l’aide d’un nom de source de données. Pour utiliser la classe [CDatabase](../../mfc/reference/cdatabase-class.md), la source de données doit être celui que vous avez configuré via l’administrateur de base de données connectivité ODBC (Open). Exemples de sources de données incluent une base de données distante en cours d’exécution sur Microsoft SQL Server via un réseau ou un fichier Microsoft Access dans un répertoire local. À partir de votre application, vous pouvez accéder à n’importe quelle source de données pour lequel vous avez un pilote ODBC.

Vous pouvez avoir une ou plusieurs sources de données actives dans votre application en même temps, chacun représenté par un `CDatabase` objet. Vous pouvez également avoir plusieurs connexions simultanées à n’importe quelle source de données. Vous pouvez vous connecter à distance, ainsi qu’à des sources de données locales, selon les pilotes que vous avez installé et les fonctionnalités de vos pilotes ODBC. Pour plus d’informations sur les sources de données et l’administrateur ODBC, consultez [ODBC](../../data/odbc/odbc-basics.md) et [administrateur ODBC](../../data/odbc/odbc-administrator.md).

Les rubriques suivantes expliquent plus sur les sources de données :

- [Source de données : gestion des connexions (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)

- [Source de données : détermination du schéma de la source de données (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)

## <a name="see-also"></a>Voir aussi

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)