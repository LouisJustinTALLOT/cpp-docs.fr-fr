---
title: 'Source de données : Détermination du schéma de la Source de données (ODBC) | Microsoft Docs'
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
ms.openlocfilehash: b5ba9789226e54c9607e85caaa5e8af3f157f02d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052636"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>Source de données : détermination du schéma de la source de données (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Pour définir les membres de données dans votre `CRecordset` objets, vous devez connaître le schéma de la source de données auquel vous vous connectez. Détermination du schéma d’une source de données, vous devez obtenir une liste des tables de la source de données, une liste de colonnes dans chaque table, le type de données de chaque colonne et l’existence de tous les index.

## <a name="see-also"></a>Voir aussi

[Source de données (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Source de données : gestion des connexions (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)