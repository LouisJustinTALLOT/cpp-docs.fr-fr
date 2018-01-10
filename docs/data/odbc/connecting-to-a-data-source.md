---
title: "Connexion à une Source de données | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 08872f9e1034c50ca1468d6834f3a44dc06c1ebe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="connecting-to-a-data-source"></a>Connexion à une source de données
Une source de données ODBC est un ensemble spécifique de données, les informations requises pour accéder aux données et l’emplacement de la source de données, ce qui peut être décrite à l’aide d’un nom de source de données. Du point de vue de votre programme, la source de données inclut les données, le SGBD, le réseau (le cas échéant) et ODBC.  
  
 Pour accéder aux données fournies par une source de données, votre programme devez d’abord établir une connexion à la source de données. Tout accès aux données est géré via cette connexion.  
  
 Connexions de source de données sont encapsulées par la classe [CDatabase](../../mfc/reference/cdatabase-class.md). Lorsqu’un `CDatabase` objet est connecté à une source de données, vous pouvez :  
  
-   Construire [jeux d’enregistrements](../../mfc/reference/crecordset-class.md), qui sélectionnent des enregistrements à partir des tables ou des requêtes.  
  
-   Gérer les [transactions](../../data/odbc/transaction-odbc.md), traitement par lot mises à jour par conséquent, tous les validée dans la source de données à la fois (ou toute la transaction est restaurée pour que la source de données est inchangée), si la source de données prend en charge le niveau requis de transactions.  
  
-   Exécuter directement [SQL](../../data/odbc/sql.md) instructions.  
  
 Lorsque vous avez terminé de travailler avec une connexion de source de données, vous fermez le `CDatabase` objet et détruire ou de le réutiliser pour une nouvelle connexion. Pour plus d’informations sur les connexions de source de données, consultez [Source de données (ODBC)](../../data/odbc/data-source-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [ODBC et MFC](../../data/odbc/odbc-and-mfc.md)