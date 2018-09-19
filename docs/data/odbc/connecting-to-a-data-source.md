---
title: Connexion à une Source de données | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4be8214ad036d67a02ce4b9c5935d3deb92252c1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061095"
---
# <a name="connecting-to-a-data-source"></a>Connexion à une source de données

Une source de données ODBC est un ensemble spécifique de données, les informations requises pour accéder à ces données et l’emplacement de la source de données, qui peut être décrits à l’aide d’un nom de source de données. Du point de vue de votre programme, la source de données inclut les données, le SGBD, le réseau (le cas échéant) et ODBC.  
  
Pour accéder aux données fournies par une source de données, votre programme devez d’abord établir une connexion à la source de données. Tous les accès de données est géré via cette connexion.  
  
Connexions de source de données sont encapsulées par la classe [CDatabase](../../mfc/reference/cdatabase-class.md). Quand un `CDatabase` objet est connecté à une source de données, vous pouvez :  
  
- Construire [recordsets](../../mfc/reference/crecordset-class.md), qui sélectionnent des enregistrements à partir des tables ou des requêtes.  
  
- Gérer [transactions](../../data/odbc/transaction-odbc.md), traitement par lot mises à jour afin que tous les validée dans la source de données à la fois (ou toute la transaction est restaurée pour que la source de données demeure inchangée) : si la source de données prend en charge le niveau requis de transactions.  
  
- Exécuter directement des [SQL](../../data/odbc/sql.md) instructions.  
  
Lorsque vous avez terminé le travail avec une connexion de source de données, vous fermez le `CDatabase` objet et détruire ou réutiliser pour une nouvelle connexion. Pour plus d’informations sur les connexions de source de données, consultez [Source de données (ODBC)](../../data/odbc/data-source-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  

[ODBC et MFC](../../data/odbc/odbc-and-mfc.md)