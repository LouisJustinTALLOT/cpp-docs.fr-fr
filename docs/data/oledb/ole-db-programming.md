---
title: Programmation OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB [C++]
- data access [C++], OLE DB programming
- OLE DB [C++], about OLE DB
ms.assetid: 52a80d66-17a9-43a1-9b90-392ae43cea2b
ms.openlocfilehash: ac74f94b4cdc738237c2994646f7602f7f5118ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361241"
---
# <a name="ole-db-programming"></a>Programmation OLE DB

Microsoft OLE DB est une technologie héritée ; pour les nouvelles applications, il est l’API accès aux données requises pour les serveurs SQL liés. Toutes les autres nouvelles applications doivent utiliser ODBC. Le fournisseur OLE DB actuel pour SQL Server est SQLNCLI11. DLL. Le fournisseur est toujours transaction dans SQL Server 2016. Cette documentation s’adresse aux développeurs chargés de la maintenant des applications existantes qui utilisent déjà OLE DB.

Les modèles OLE DB sont des modèles C++ qui facilitent l'utilisation de la technologie de base de données OLE DB haute performance en fournissant des classes qui implémentent de nombreuses interfaces OLE DB couramment utilisées. Cette bibliothèque de modèles est divisée en modèles de consommateurs et en modèles de fournisseurs.

Visual C++ prend également en charge des Assistants pour créer des applications de départ OLE DB.

En outre, vous pouvez utiliser des attributs pour implémenter les modèles du consommateur OLE DB.

|Pour en savoir plus sur les sujets suivants|Voir|
|-------------------------|---------|
|Utilisation des modèles du consommateur OLE DB (rubriques conceptuelles)|[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)|
|Utilisation des modèles du fournisseur OLE DB (rubriques conceptuelles)|[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)|
|Classes et macros des modèles OLE DB|[Référence des modèles OLE DB](../../data/oledb/ole-db-templates.md) (Visual C++)|
|Attributs du consommateur OLE DB|[Attributs du consommateur OLE DB](../../windows/ole-db-consumer-attributes.md)|
|Interfaces OLE DB|[Référence du programmeur OLE DB](/sql/connect/oledb/oledb-driver-for-sql-server) (dans le Kit de développement logiciel Windows)|
|Exemples de modèles OLE DB|[Exemples de modèles OLE DB](https://github.com/Microsoft/VCSamples)|
|Vue d'ensemble de la programmation de l'accès aux données (Visual C++)|[Programmation d’accès aux données](../../data/data-access-programming-mfc-atl.md)|
|Rubriques sur les concepts d'ODBC|[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)|

## <a name="see-also"></a>Voir aussi

[Accès aux données](../data-access-in-cpp.md)