---
title: Programmation OLE DB | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB [C++]
- data access [C++], OLE DB programming
- OLE DB [C++], about OLE DB
ms.assetid: 52a80d66-17a9-43a1-9b90-392ae43cea2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fb77c5b7d7f6de91f74e83c395d0fcc13ebf70e0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="ole-db-programming"></a>Programmation OLE DB
Microsoft OLE DB est une technologie héritée ; pour les nouvelles applications, il est l’API d’accès données requises pour les serveurs liés SQL. Toutes les autres nouvelles applications doivent utiliser ODBC. Le fournisseur OLE DB actuel pour SQL Server est SQLNCLI11. DLL. Le fournisseur est toujours celle de SQL Server 2016. Cette documentation s’adresse aux développeurs chargés de la maintenance des applications existantes qui utilisent déjà OLE DB.
  
 Les modèles OLE DB sont des modèles C++ qui facilitent l'utilisation de la technologie de base de données OLE DB haute performance en fournissant des classes qui implémentent de nombreuses interfaces OLE DB couramment utilisées. Cette bibliothèque de modèles est divisée en modèles de consommateurs et en modèles de fournisseurs.  
  
 Visual C++ prend également en charge des Assistants pour créer des applications de départ OLE DB.  
  
 En outre, vous pouvez utiliser des attributs pour implémenter les modèles de consommateurs OLE DB.  
  
|Pour en savoir plus sur|Voir|  
|-------------------------|---------|  
|Utilisation des modèles du consommateur OLE DB (rubriques conceptuelles)|[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)|  
|Utilisation des modèles du fournisseur OLE DB (rubriques conceptuelles)|[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)|  
|Classes et macros des modèles OLE DB|[Référence des modèles OLE DB](../../data/oledb/ole-db-templates.md) (Visual C++)|  
|Attributs du consommateur OLE DB|[Attributs du consommateur OLE DB](../../windows/ole-db-consumer-attributes.md)|  
|Interfaces OLE DB|[Référence du programmeur OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx) (dans le Kit de développement logiciel Windows)|  
|Exemples de modèles OLE DB|[Exemples de modèles OLE DB](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c)| 
|Vue d'ensemble de la programmation de l'accès aux données (Visual C++)|[Programmation d’accès aux données](../../data/data-access-programming-mfc-atl.md)|  
|Rubriques sur les concepts d'ODBC|[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)|  

  
## <a name="see-also"></a>Voir aussi  
 [Accès aux données](../data-access-in-cpp.md)