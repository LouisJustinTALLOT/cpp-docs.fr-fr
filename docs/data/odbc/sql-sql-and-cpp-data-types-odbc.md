---
title: 'SQL : types de données SQL et C++ (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: cffe44b832ac1eb28d368072b8f0e92ea9f57feb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374482"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL : types de données SQL et C++ (ODBC)

> [!NOTE]
> Ces informations s’appliquent aux classes ODBC MFC. Si vous travaillez avec les classes MFC DAO, consultez le thème "Comparaison de Microsoft Jet Database Engine SQL et ANSI SQL" dans DAO Help.

Le tableau suivant cartographie les types de données ANSI SQL aux types de données CMD. Cela augmente les informations linguistiques C données à l’Annexe D de la *référence du programmeur* *SDK de l’ODBC* sur le CD de la Bibliothèque MSDN. Les assistants gèrent la plupart des cartes de type de données pour vous. Si vous n’utilisez pas un assistant, vous pouvez utiliser les informations de cartographie pour vous aider à écrire le code d’échange sur le terrain manuellement.

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>Les types de données ANSI SQL cartographiés aux types de données CMD

|Type de données ANSI SQL|Type de données C++|
|------------------------|---------------------|
|**CHAR**|`CString`|
|**Decimales**|`CString`1|
|**SMALLINT (EN)**|**int**|
|**Réel**|**float**|
|**Entier**|**Long**|
|**Flotteur**|**double**|
|**Double**|**double**|
|**Numérique**|`CString`1|
|**Varchar**|`CString`|
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|
|**Peu**|**Bool**|
|**Tinyint**|**Octet**|
|**Bigint**|`CString`1|
|**Binaire**|`CByteArray`|
|**Varbinary**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|
|**Date**|`CTime`, `CString`|
|**Temps**|`CTime`, `CString`|
|**Timestamp**|`CTime`, `CString`|

1. Carte ANSI **DECIMAL** `CString` et **NUMERIC** à cause **SQL_C_CHAR** est le type de transfert par défaut D’ODBC.

2. Les données de caractère au-delà de 255 `CString`caractères sont tronquées par défaut lorsqu’elles sont cartographiées en . Vous pouvez étendre la longueur de troncation en définissant `RFX_Text`explicitement *l’argument nMaxLength* de .

3. Les données binaires au-delà de 255 `CByteArray`caractères sont tronquées par défaut lorsqu’elles sont cartographiées en . Vous pouvez étendre la longueur de troncation en définissant `RFX_Binary`explicitement *l’argument nMaxLength* de .

Si vous n’utilisez pas la bibliothèque de curseurs ODBC, vous pourriez rencontrer un problème lorsque vous tentez de mettre à jour deux ou plusieurs longs champs à longueur variable à l’aide du pilote Microsoft SQL Server ODBC et des classes de base de données MFC ODBC. Les types ODBC, **SQL_LONGVARCHAR** et **SQL_LONGVARBINARY**, carte de texte et d’image SQL Server types. A `CDBException` est jeté si vous mettez à jour deux ou `CRecordset::Update`plusieurs longs champs de longueur variable sur le même appel à . Par conséquent, ne pas mettre `CRecordset::Update`à jour plusieurs colonnes longues en même temps avec . Vous pouvez mettre à jour plusieurs longues colonnes simultanément avec l’API `SQLPutData`ODBC . Vous pouvez également utiliser la bibliothèque de curseurs ODBC, mais ce n’est pas recommandé pour les conducteurs, comme le conducteur SQL Server, qui prennent en charge les curseurs et n’ont pas besoin de la bibliothèque de curseurs.

Si vous utilisez la bibliothèque de curseurs ODBC avec les classes de base de données MFC ODBC `CDBException` et le `CRecordset::Update` pilote Microsoft `CRecordset::Requery`SQL Server ODBC, un **ASSERT** peut se produire avec un si un appel pour suivre un appel à . Au lieu `CRecordset::Close` `CRecordset::Open` de `CRecordset::Requery`cela, appelez et plutôt que . Une autre solution est de ne pas utiliser la bibliothèque de curseurs ODBC, parce que le serveur SQL et le conducteur SQL Server ODBC fournissent un soutien autochtone pour les curseurs natifs et la bibliothèque de curseurs ODBC n’est pas nécessaire.

## <a name="see-also"></a>Voir aussi

[SQL](../../data/odbc/sql.md)<br/>
[SQL : appels SQL directs (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
