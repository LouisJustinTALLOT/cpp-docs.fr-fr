---
title: Accès à ODBC et SQL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 25e9533752e47e5cf3ea50e594a23b99e19355ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="access-to-odbc-and-sql"></a>Accès à ODBC et SQL
La bibliothèque Microsoft Foundation Class encapsule de nombreux appels d’API Windows et vous permet également d’appeler directement toute fonction API Windows. Les classes de base de données vous donnent la flexibilité même en ce qui concerne l’API ODBC. Alors que les classes de base de données vous évitent de la complexité d’ODBC, vous pouvez appeler des fonctions API ODBC directement à partir de n’importe où dans votre programme.  
  
 De même, les classes de base de données vous évitent d’avoir à fonctionnent avec [SQL](../../data/odbc/sql.md), mais vous pouvez utiliser SQL directement si vous le souhaitez. Vous pouvez personnaliser des objets recordset en passant une instruction SQL personnalisée (ou en définissant des parties de l’instruction par défaut) lorsque vous ouvrez le jeu d’enregistrements. Vous pouvez également effectuer des appels SQL directement à l’aide de la [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) fonction membre de classe [CDatabase](../../mfc/reference/cdatabase-class.md).  
  
 Pour plus d’informations, consultez [ODBC : appel direct de fonctions API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) et [SQL : appels SQL directs (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [ODBC et MFC](../../data/odbc/odbc-and-mfc.md)