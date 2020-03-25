---
title: Accès à ODBC et SQL
ms.date: 11/04/2016
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
ms.openlocfilehash: 0b590ce9309cbbe95285001cc5befe70a1d1961f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213328"
---
# <a name="access-to-odbc-and-sql"></a>Accès à ODBC et SQL

Le bibliothèque MFC (Microsoft Foundation Class) encapsule de nombreux appels d’API Windows tout en vous permettant d’appeler directement toute fonction API Windows. Les classes de base de données offrent la même flexibilité en ce qui concerne l’API ODBC. Alors que les classes de base de données vous protègent de la complexité d’ODBC, vous pouvez appeler des fonctions API ODBC directement depuis n’importe où dans votre programme.

De même, les classes de base de données vous évitent d’avoir à travailler avec [SQL](../../data/odbc/sql.md), mais vous pouvez utiliser directement SQL si vous le souhaitez. Vous pouvez personnaliser des objets Recordset en passant une instruction SQL personnalisée (ou en définissant des parties de l’instruction par défaut) lorsque vous ouvrez le Recordset. Vous pouvez également effectuer des appels SQL directement à l’aide de la fonction membre [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) de la classe [CDatabase](../../mfc/reference/cdatabase-class.md).

Pour plus d’informations, consultez [ODBC : appel direct de fonctions API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) et [SQL : appels SQL directs (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md).

## <a name="see-also"></a>Voir aussi

[ODBC et MFC](../../data/odbc/odbc-and-mfc.md)
