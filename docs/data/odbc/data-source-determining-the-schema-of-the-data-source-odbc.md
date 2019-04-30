---
title: 'Source de données : Détermination du schéma de la Source de données (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
ms.openlocfilehash: c419a3ac2d870e6a85675492ee6c9b726427a0e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395974"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>Source de données : Détermination du schéma de la Source de données (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Pour définir les membres de données dans votre `CRecordset` objets, vous devez connaître le schéma de la source de données auquel vous vous connectez. Détermination du schéma d’une source de données, vous devez obtenir une liste des tables de la source de données, une liste de colonnes dans chaque table, le type de données de chaque colonne et l’existence de tous les index.

## <a name="see-also"></a>Voir aussi

[Source de données (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Source de données : Gestion des connexions (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)