---
title: 'SQL : types de données SQL et C++ (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: 70796db02f8ff3fcfd67694fb596722664e8f904
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404253"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL : types de données SQL et C++ (ODBC)

> [!NOTE]
> Ces informations s’appliquent aux classes ODBC MFC. Si vous utilisez les classes DAO MFC, consultez la rubrique « Comparaison de Microsoft Jet Moteur de base de données SQL et ANSI SQL » dans l’aide de DAO.

Le tableau suivant mappe les types de données ANSI SQL aux types de données C++. Cela augmente les informations de langage C fournies dans l’annexe D de la documentation de [Référence du programmeur ODBC](/sql/odbc/reference/odbc-programmer-s-reference) . Les assistants gèrent la plupart des mappages de types de données. Si vous n’utilisez pas d’Assistant, vous pouvez utiliser les informations de mappage pour vous aider à écrire le code d’échange de champ manuellement.

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>Types de données SQL ANSI mappés aux types de données C++

|Type de données SQL ANSI|Type de données C++|
|------------------------|---------------------|
|**CHAR**|`CString`|
|**SÉPAR**|`CString`1,0|
|**SMALLINT**|**int**|
|**NON**|**float**|
|**ENTIÈRE**|**long**|
|**DISSOCIÉ**|**double**|
|**Cliquer**|**double**|
|**CHIFFRE**|`CString`1,0|
|**VARCHAR**|`CString`|
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|
|**64BITS**|**Boolean**|
|**SA**|**POIDS**|
|**COMPORTANT**|`CString`1,0|
|**BINAIRE2**|`CByteArray`|
|**VARBINARY**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|
|**DATE**|`CTime`, `CString`|
|**SIMULTANÉMENT**|`CTime`, `CString`|
|**CONFIRMÉ**|`CTime`, `CString`|

1. Mappage **décimal** et **numérique** ANSI à `CString` , car **SQL_C_CHAR** est le type de transfert ODBC par défaut.

2. Les données de caractères au-delà de 255 caractères sont tronquées par défaut lorsqu’elles sont mappées à `CString` . Vous pouvez étendre la longueur de troncation en définissant explicitement l’argument *nMaxLength* de `RFX_Text` .

3. Les données binaires au-delà de 255 caractères sont tronquées par défaut lorsqu’elles sont mappées à `CByteArray` . Vous pouvez étendre la longueur de troncation en définissant explicitement l’argument *nMaxLength* de `RFX_Binary` .

Si vous n’utilisez pas la bibliothèque de curseurs ODBC, vous risquez de rencontrer un problème lors de la tentative de mise à jour d’au moins deux champs longs de longueur variable à l’aide de la Microsoft SQL Server pilote ODBC et des classes de base de données ODBC MFC. Les types ODBC, **SQL_LONGVARCHAR** et **SQL_LONGVARBINARY**, sont mappés aux types de SQL Server texte et image. Une `CDBException` exception est levée si vous mettez à jour au moins deux champs de longueur variable longue sur le même appel à `CRecordset::Update` . Par conséquent, ne mettez pas à jour plusieurs colonnes longues simultanément avec `CRecordset::Update` . Vous pouvez mettre à jour plusieurs colonnes longues simultanément avec l’API ODBC `SQLPutData` . Vous pouvez également utiliser la bibliothèque de curseurs ODBC, mais cela n’est pas recommandé pour les pilotes, comme le pilote SQL Server, qui prennent en charge les curseurs et qui n’ont pas besoin de la bibliothèque de curseurs.

Si vous utilisez la bibliothèque de curseurs ODBC avec les classes de base de données ODBC MFC et le pilote ODBC Microsoft SQL Server, une **assertion** peut se produire avec un `CDBException` si un appel à `CRecordset::Update` suit un appel à `CRecordset::Requery` . Au lieu de cela, appelez `CRecordset::Close` et `CRecordset::Open` plutôt que `CRecordset::Requery` . Une autre solution consiste à ne pas utiliser la bibliothèque de curseurs ODBC, car les SQL Server et le pilote ODBC SQL Server fournissent une prise en charge native des curseurs en mode natif et la bibliothèque de curseurs ODBC n’est pas nécessaire.

## <a name="see-also"></a>Voir aussi

[SQL](../../data/odbc/sql.md)<br/>
[SQL : appels SQL directs (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
