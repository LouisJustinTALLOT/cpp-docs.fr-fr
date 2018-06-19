---
title: 'SQL : SQL et Types de données C++ (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6a137c4f648f518420d06f5cbd98ea189a030aee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095406"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL : types de données SQL et C++ (ODBC)
> [!NOTE]
>  Ces informations s’appliquent aux classes ODBC MFC. Si vous travaillez avec les classes DAO MFC, consultez la rubrique « Comparaison de Microsoft Jet Database Engine SQL et ANSI SQL » dans l’aide de DAO.  
  
 Le tableau suivant mappe les types de données SQL ANSI pour les types de données C++. Cela augmente les informations du langage C données dans l’annexe D de la *ODBC SDK* *de référence du programmeur* sur le CD-ROM MSDN Library. Les Assistants de gérer la plupart des mappages de types de données de. Si vous n’utilisez pas un Assistant, vous pouvez utiliser les informations de mappage pour vous aider à écrire le code d’échange de champs manuellement.  
  
### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>Types de données SQL ANSI mappés aux Types de données C++  
  
|Type de données SQL ANSI|Type de données C++|  
|------------------------|---------------------|  
|**CHAR**|`CString`|  
|**DECIMAL**|`CString` 1|  
|**SMALLINT**|`int`|  
|`REAL`|**float**|  
|**ENTIER**|**long**|  
|**FLOAT**|**double**|  
|**DOUBLE**|**double**|  
|**NUMÉRIQUE**|`CString` 1|  
|**VARCHAR**|`CString`|  
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|  
|**BITS**|**BOOL**|  
|**TINYINT**|**BYTE**|  
|**BIGINT**|`CString` 1|  
|**BINAIRE**|`CByteArray`|  
|**VARBINARY**|`CByteArray`|  
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|  
|**DATE**|`CTime`, `CString`|  
|**HEURE**|**CTime, CString**|  
|**HORODATEUR**|**CTime, CString**|  
  
 1. ANSI **décimal** et **numérique** mapper à `CString` car **SQL_C_CHAR** est le type de transfert ODBC par défaut.  
  
 2. Données de type caractère au-delà de 255 caractères sont tronquées par défaut quand mappé à `CString`. Vous pouvez étendre la longueur de troncation en définissant explicitement le `nMaxLength` argument de `RFX_Text`.  
  
 3. Données binaires au-delà de 255 caractères sont tronquées par défaut lorsque mappé à `CByteArray`. Vous pouvez étendre la longueur de troncation en définissant explicitement le `nMaxLength` argument de `RFX_Binary`.  
  
 Si vous n’utilisez pas la bibliothèque de curseurs ODBC, vous pouvez rencontrer un problème lorsque vous tentez de mettre à jour deux ou plusieurs champs de longueur variable à l’aide du pilote ODBC de Microsoft SQL Server et les classes de base de données ODBC MFC. Les types ODBC **SQL_LONGVARCHAR** et **SQL_LONGVARBINARY**, mappez à texte et image de types SQL Server. A `CDBException` est levée si vous mettez à jour deux ou plusieurs champs de longueur variable sur le même appel à `CRecordset::Update`. Par conséquent, ne mettez pas à jour plusieurs colonnes longues simultanément avec `CRecordset::Update`. Vous pouvez mettre à jour plusieurs colonnes longues simultanément avec l’API ODBC **SQLPutData**. Vous pouvez également utiliser la bibliothèque de curseurs ODBC, mais cela n’est pas recommandé pour les pilotes, comme le pilote SQL Server, qui prennent en charge des curseurs et n’avez pas besoin de la bibliothèque de curseurs.  
  
 Si vous utilisez la bibliothèque de curseurs ODBC avec les classes de base de données ODBC MFC et le pilote ODBC de Microsoft SQL Server, un **ASSERT** peut se produire avec un `CDBException` si un appel à `CRecordset::Update` suit un appel à `CRecordset::Requery`. Au lieu de cela, appelez `CRecordset::Close` et `CRecordset::Open` plutôt que `CRecordset::Requery`. Une autre solution consiste ne pas à utiliser la bibliothèque de curseurs ODBC, car le serveur SQL Server et le pilote ODBC de SQL Server offrent une prise en charge native pour les curseurs en mode natif et de la bibliothèque de curseurs ODBC n’est pas nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL](../../data/odbc/sql.md)   
 [SQL : appels SQL directs (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)