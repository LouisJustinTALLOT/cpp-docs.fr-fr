---
title: 'Source de données : détermination du schéma de la source de données (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
ms.openlocfilehash: ed6500c5718cf90b39600b12659a3090fe9532ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580754"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>Source de données : détermination du schéma de la source de données (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Pour définir les membres de données dans votre `CRecordset` objets, vous devez connaître le schéma de la source de données auquel vous vous connectez. Détermination du schéma d’une source de données, vous devez obtenir une liste des tables de la source de données, une liste de colonnes dans chaque table, le type de données de chaque colonne et l’existence de tous les index.

## <a name="see-also"></a>Voir aussi

[Source de données (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Source de données : gestion des connexions (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)