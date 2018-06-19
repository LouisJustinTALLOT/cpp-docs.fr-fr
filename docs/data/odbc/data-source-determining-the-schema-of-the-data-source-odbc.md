---
title: 'Source de données : Détermination du schéma de la Source de données (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6da4067766eddab40bac75ee73d825dc5886dd0f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088275"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>Source de données : détermination du schéma de la source de données (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Pour définir les membres de données dans votre `CRecordset` objets, vous devez connaître le schéma de la source de données à laquelle vous vous connectez. Détermination du schéma d’une source de données, vous devez obtenir une liste des tables de la source de données, une liste de colonnes dans chaque table, le type de données de chaque colonne et l’existence de tous les index.  
  
## <a name="see-also"></a>Voir aussi  
 [Source de données (ODBC)](../../data/odbc/data-source-odbc.md)   
 [Source de données : gestion des connexions (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)