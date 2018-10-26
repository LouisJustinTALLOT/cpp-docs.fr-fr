---
title: Enregistrer des fonctions d’échange de champ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXDB/RFX_Binary
- AFXDB/RFX_Bool
- AFXDB/RFX_Byte
- AFXDB/RFX_Date
- AFXDB/RFX_Double
- AFXDB/RFX_Int
- AFXDB/RFX_Long
- AFXDB/RFX_LongBinary
- AFXDB/RFX_Single
- AFXDB/RFX_Text
- AFXDB/RFX_Binary_Bulk
- AFXDB/RFX_Bool_Bulk
- AFXDB/RFX_Byte_Bulk
- AFXDB/RFX_Date_Bulk
- AFXDB/RFX_Double_Bulk
- AFXDB/RFX_Int_Bulk
- AFXDB/RFX_Long_Bulk
- AFXDB/RFX_Single_Bulk
- AFXDB/RFX_Text_Bulk
- AFXDB/DFX_Binary
- AFXDB/DFX_Bool
- AFXDB/DFX_Byte
- AFXDB/DFX_Currency
- AFXDB/DFX_DateTime
- AFXDB/DFX_Double
- AFXDB/DFX_Long
- AFXDB/DFX_LongBinary
- AFXDB/DFX_Short
- AFXDB/DFX_Single
- AFXDB/DFX_Text
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), record field exchange (DFX)
- ODBC, bulk RFX data exchange functions [MFC]
- RFX (record field exchange), ODBC classes
- DFX (DAO record field exchange), data exchange functions [MFC]
- DFX functions [MFC]
- bulk RFX functions [MFC]
- DFX (DAO record field exchange)
- RFX (record field exchange), DAO classes
- ODBC, RFX
- RFX (record field exchange), data exchange functions [MFC]
- RFX (record field exchange)
ms.assetid: 6e4c5c1c-acb7-4c18-bf51-bf7959a696cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fba2e8d949745f694973f2d7b29c5244ab30db4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50058906"
---
# <a name="record-field-exchange-functions"></a>Fonctions Record Field Exchange (RFX)

Record Field Exchange (RFX en bloc RFX et DFX) cette rubrique répertorie les fonctions utilisées pour automatiser le transfert de données entre un objet recordset et sa source de données et effectuer d’autres opérations sur les données.

Si vous utilisez les classes ODBC et que vous avez implémenté l’extraction de lignes en bloc, vous devez remplacer manuellement la fonction membre `DoBulkFieldExchange` de `CRecordset` en appelant les fonctions RFX en bloc pour chaque membre de données correspondant à une colonne de source de données.

Si vous n’avez pas implémenté l’extraction de lignes en bloc dans les classes ODBC, ou si vous utilisez les classes DAO, ClassWizard remplace la fonction membre `DoFieldExchange` de `CRecordset` ou `CDaoRecordset` en appelant les fonctions RFX (pour les classes ODBC) ou les fonctions DFX (pour les classes DAO) pour chaque membre de données de champ de votre recordset.

Les fonctions d’échange de champs d’enregistrements transfèrent des données chaque fois que l’infrastructure appelle `DoFieldExchange` ou `DoBulkFieldExchange`. Chaque fonction transfère un type de données spécifique.

Pour plus d’informations sur l’utilisation de ces fonctions, consultez les articles [Record Field Exchange : fonctionnement de RFX (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Pour les colonnes de données que vous liez dynamiquement, vous pouvez aussi appeler les fonctions RFX et DFX par vous-même, comme expliqué dans les articles [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). Par ailleurs, vous pouvez écrire vos propres routines RFX ou DFX personnalisées, comme l’explique la Note technique [43](../../mfc/tn043-rfx-routines.md) (pour ODBC) et la Note technique [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (pour DAO).

Pour un exemple de RFX et RFX en bloc des fonctions telles qu’elles apparaissent dans le `DoFieldExchange` et `DoBulkFieldExchange` fonctions, consultez [RFX_Text](#rfx_text) et [RFX_Text_Bulk] #rfx_text_bulk). Les fonctions DFX sont très similaires aux fonctions RFX.

### <a name="rfx-functions-odbc"></a>Fonctions RFX (ODBC)

|||
|-|-|
|[RFX_Binary](#rfx_binary)|Transfère les tableaux d’octets de type [CByteArray](cbytearray-class.md).|
|[RFX_Bool](#rfx_bool)|Transfère les données de type Boolean.|
|[RFX_Byte](#rfx_byte)|Transfère un seul octet de données.|
|[RFX_Date](#rfx_date)|Transfère les heure et date à l’aide de données [CTime](../../atl-mfc-shared/reference/ctime-class.md) ou TIMESTAMP_STRUCT.|
|[RFX_Double](#rfx_double)|Transfère les données de type Float double précision.|
|[RFX_Int](#rfx_int)|Transfère les données de type Integer.|
|[RFX_Long](#rfx_long)|Transfère les données de type Long Integer.|
|[RFX_LongBinary](#rfx_longbinary)|Transfère les données BLOB avec un objet de la classe [CLongBinary](clongbinary-class.md) .|
|[RFX_Single](#rfx_single)|Transfère les données de type Float.|
|[RFX_Text](#rfx_text)|Transfère les données de type String.|

### <a name="bulk-rfx-functions-odbc"></a>Fonctions RFX en bloc (ODBC)

|||
|-|-|
|[RFX_Binary_Bulk](#rfx_binary_bulk)|Transfère les tableaux de données de type Byte.|
|[RFX_Bool_Bulk](#rfx_bool_bulk)|Transfère les tableaux de données de type Boolean.|
|[RFX_Byte_Bulk](#rfx_byte_bulk)|Transfère les tableaux d’octets uniques.|
|[RFX_Date_Bulk](#rfx_date_bulk)|Transfère les tableaux de données de type TIMESTAMP_STRUCT.|
|[RFX_Double_Bulk](#rfx_double_bulk)|Transfère les tableaux de données à virgule flottante double précision.|
|[RFX_Int_Bulk](#rfx_int_bulk)|Transfère les tableaux de données de type Integer.|
|[RFX_Long_Bulk](#rfx_long_bulk)|Transfère les tableaux de données de type Long Integer.|
|[RFX_Single_Bulk](#rfx_single_bulk)|Transfère les tableaux de données à virgule flottante.|
|[RFX_Text_Bulk](#rfx_text_bulk)|Transfère les tableaux de données de type LPSTR.|

### <a name="dfx-functions-dao"></a>Fonctions DFX (DAO)

|||
|-|-|
|[DFX_Binary](#dfx_binary)|Transfère les tableaux d’octets de type [CByteArray](cbytearray-class.md).|
|[DFX_Bool](#dfx_bool)|Transfère les données de type Boolean.|
|[DFX_Byte](#dfx_byte)|Transfère un seul octet de données.|
|[DFX_Currency](#dfx_currency)|Transfère les données de devise de type [COleCurrency](colecurrency-class.md).|
|[DFX_DateTime](#dfx_datetime)|Transfère les données de date et d’heure de type [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md).|
|[DFX_Double](#dfx_double)|Transfère les données de type Float double précision.|
|[DFX_Long](#dfx_long)|Transfère les données de type Long Integer.|
|[DFX_LongBinary](#dfx_longbinary)|Transfère les données BLOB avec un objet de la classe `CLongBinary` . Pour DAO, il est recommandé d’utiliser plutôt [DFX_Binary](#dfx_binary) .|
|[DFX_Short](#dfx_short)|Transfère les données de type Short Integer.|
|[DFX_Single](#dfx_single)|Transfère les données de type Float.|
|[DFX_Text](#dfx_text)|Transfère les données de type String.|

=============================================

## <a name="rfx_binary"></a>  RFX_Binary

Transfère les tableaux d’octets entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données d’ODBC SQL_BINARY ou type SQL_VARBINARY SQL_LONGVARBINARY.

### <a name="syntax"></a>Syntaxe

```
void RFX_Binary(
   CFieldExchange* pFX,
   const char* szName,
   CByteArray& value,
   int nMaxLength = 255);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations sur les opérations un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert de jeu d’enregistrements à la source de données, la valeur de type [CByteArray](cbytearray-class.md), provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

*nMaxLength*<br/>
La longueur maximale autorisée de la chaîne ou un tableau en cours de transfert. La valeur par défaut *nMaxLength* est 255. Valeurs autorisées vont de 1 à INT_MAX. Le framework alloue cette quantité d’espace pour les données. Pour de meilleures performances, passez une valeur suffisamment grande pour contenir l’élément de données plus grand que prévu.

### <a name="remarks"></a>Notes

Les données dans la source de données de ces types sont mappées vers et à partir du type `CByteArray` dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_bool"></a>  RFX_Bool

Transfère les données booléennes entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données d’ODBC tapez SQL_BIT.

### <a name="syntax"></a>Syntaxe

```
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations sur les opérations un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert à partir du jeu d’enregistrements à la source de données, la valeur de type BOOL, provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_byte"></a>  RFX_Byte

Transferts unique octets entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données d’ODBC tapez SQL_TINYINT.

### <a name="syntax"></a>Syntaxe

```
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations sur les opérations un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert à partir du jeu d’enregistrements à la source de données, la valeur de type BYTE, provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_date"></a>  RFX_Date

Transferts `CTime` TIMESTAMP_STRUCT des données entre les membres de données de champ ou une `CRecordset` objet et les colonnes d’un enregistrement sur la source de données d’ODBC tapez SQL_DATE, SQL_TIME ou SQL_TIMESTAMP.

### <a name="syntax"></a>Syntaxe

```
void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   CTime& value);

void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   TIMESTAMP_STRUCT& value);

void RFX_Date(
   CFieldExchange* pFX,
   const char* szName,
   COleDateTime& value);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations sur les opérations un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué ; la valeur doit être transféré. Les différentes versions de la fonction prennent différents types de données pour la valeur :

La première version de la fonction accepte une référence à un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objet. Pour un transfert à partir du jeu d’enregistrements à la source de données, cette valeur provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

La deuxième version de la fonction accepte une référence à un `TIMESTAMP_STRUCT` structure. Vous devez définir cette structure vous-même avant l’appel. Aucun échange de données de boîtes de dialogue (DDX) prennent en charge ni prise en charge de code Assistant est disponible pour cette version. La troisième version de la fonction fonctionne de manière similaire à la première version, à ceci près qu’elle prend une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objet.

### <a name="remarks"></a>Notes

Le `CTime` version de la fonction impose la surcharge liée à un traitement intermédiaire et a une plage quelque peu limitée. Si vous trouvez un de ces facteurs trop limitée, utilisez la deuxième version de la fonction. Mais notez l’absence de l’Assistant de code et de prise en charge DDX et de l’exigence que vous avez configuré la structure vous-même.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_double"></a>  RFX_Double

Transferts **float double** des données entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données d’ODBC SQL_DOUBLE de type.

### <a name="syntax"></a>Syntaxe

```
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations sur les opérations un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert de jeu d’enregistrements à la source de données, la valeur de type **double**, provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_int"></a>  RFX_Int

Transfère les données d’entier entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données d’ODBC tapez SQL_SMALLINT.

### <a name="syntax"></a>Syntaxe

```
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations sur les opérations un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert de jeu d’enregistrements à la source de données, la valeur de type **int**, provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_long"></a>  RFX_Long

Transfère les données de type entier long entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données d’ODBC tapez SQL_INTEGER.

### <a name="syntax"></a>Syntaxe

```
void RFX_Long(
   CFieldExchange* pFX,
   const char* szName,
   LONG&
value );
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations sur les opérations un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert de jeu d’enregistrements à la source de données, la valeur de type **long**, provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_longbinary"></a>  RFX_LongBinary

Transfère les données d’objet binaire volumineux (BLOB) à l’aide de la classe [CLongBinary](clongbinary-class.md) entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données d’ODBC tapez SQL_LONGVARBINARY ou SQL_LONGVARCHAR.

### <a name="syntax"></a>Syntaxe

```
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations sur les opérations un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert de jeu d’enregistrements à la source de données, la valeur de type `CLongBinary`, provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_single"></a>  RFX_Single

Transfère les données à virgule flottante entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données d’ODBC tapez SQL_REAL.

### <a name="syntax"></a>Syntaxe

```
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations sur les opérations un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert de jeu d’enregistrements à la source de données, la valeur de type **float**, provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_text"></a>  RFX_Text

Transferts `CString` des données entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données d’ODBC type SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL ou SQL_NUMERIC.

### <a name="syntax"></a>Syntaxe

```
void RFX_Text(
   CFieldExchange* pFX,
   const char* szName,
   CString& value,
   int nMaxLength = 255,
   int nColumnType = SQL_VARCHAR,
   short nScale = 0);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe `CFieldExchange`. Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations sur les opérations un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert de jeu d’enregistrements à la source de données, la valeur de type `CString`, provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

*nMaxLength*<br/>
La longueur maximale autorisée de la chaîne ou un tableau en cours de transfert. La valeur par défaut *nMaxLength* est 255. Valeurs autorisées sont 1 à INT_MAX). Le framework alloue cette quantité d’espace pour les données. Pour de meilleures performances, passez une valeur suffisamment grande pour contenir l’élément de données plus grand que prévu.

*nColumnType*<br/>
Utilisé principalement pour les paramètres. Entier indiquant le type de données du paramètre. Le type est un type de données ODBC sous la forme **SQL_XXX**.

*nScale*<br/>
Spécifie l’échelle des valeurs de type ODBC SQL_DECIMAL ou SQL_NUMERIC. *nScale* est utile uniquement lors de la définition des valeurs de paramètre. Pour plus d’informations, consultez la rubrique « Précision, échelle, longueur et taille d’affichage » dans l’annexe D de la *de référence du programmeur ODBC SDK*.

### <a name="remarks"></a>Notes

Les données dans la source de données de tous ces types sont mappées vers et depuis `CString` dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Cet exemple illustre plusieurs appels à `RFX_Text`. Notez également les deux appels à `CFieldExchange::SetFieldType`. Pour les paramètres, vous devez écrire l’appel à `SetFieldType` et son appel RFX. L’appel de colonne de sortie et de ses appels RFX associés sont normalement écrits par un Assistant code.

```cpp
void CCustomer::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   // Macros such as RFX_Text() and RFX_Int() are dependent on the
   // type of the member variable, not the type of the field in the database.
   // ODBC will try to automatically convert the column value to the requested type
   RFX_Long(pFX, _T("[CustomerID]"), m_CustomerID);
   RFX_Text(pFX, _T("[ContactFirstName]"), m_ContactFirstName);
   RFX_Text(pFX, _T("[PostalCode]"), m_PostalCode);
   RFX_Text(pFX, _T("[L_Name]"), m_L_Name);
   RFX_Long(pFX, _T("[BillingID]"), m_BillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_binary_bulk"></a>  RFX_Binary_Bulk

Transferts de plusieurs lignes de données de type octet à partir d’une colonne d’une source de données ODBC dans un tableau correspondant dans un `CRecordset`-objet dérivé.

### <a name="syntax"></a>Syntaxe

```
void RFX_Binary_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un [CFieldExchange](cfieldexchange-class.md) objet. Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*prgByteVals*<br/>
Pointeur vers un tableau de valeurs d’octets. Ce tableau stocke les données seront transférés à partir de la source de données vers le jeu d’enregistrements.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stockera la longueur en octets de chaque valeur dans le tableau vers lequel pointé *prgByteVals*. Notez que la valeur de SQL_NULL_DATA sera stockée si l’élément de données correspondante contienne une valeur Null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *de référence du programmeur ODBC SDK*.

*nMaxLength*<br/>
La longueur des valeurs stockées dans le tableau vers lequel pointé maximale autorisée *prgByteVals*. Pour vous assurer que les données ne seront pas tronquées, passez une valeur suffisamment grande pour contenir l’élément de données plus grand que prévu.

### <a name="remarks"></a>Notes

La colonne de source de données peut avoir un type ODBC de SQL_BINARY ou SQL_VARBINARY SQL_LONGVARBINARY. Le jeu d’enregistrements doit définir un membre de données de champ de type pointeur en octet.

Si vous initialisez *prgByteVals* et *prgLengths* avec la valeur NULL, puis les tableaux ils pointent vers seront allouées automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
>  RFX en bloc transfère uniquement les données à partir de la source de données à l’objet recordset. Pour rendre votre jeu d’enregistrements modifiables, vous devez utiliser la fonction API ODBC `SQLSetPos`.

Pour plus d’informations, consultez les articles [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Consultez [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_bool_bulk"></a>  RFX_Bool_Bulk

Transferts de plusieurs lignes de données booléen à partir d’une colonne d’une source de données ODBC dans un tableau correspondant dans un `CRecordset`-objet dérivé.

### <a name="syntax"></a>Syntaxe

```
void RFX_Bool_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BOOL** prgBoolVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un [CFieldExchange](cfieldexchange-class.md) objet. Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*prgBoolVals*<br/>
Un pointeur vers un tableau de valeurs de type BOOL. Ce tableau stocke les données seront transférés à partir de la source de données vers le jeu d’enregistrements.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stockera la longueur en octets de chaque valeur dans le tableau vers lequel pointé *prgBoolVals*. Notez que la valeur de SQL_NULL_DATA sera stockée si l’élément de données correspondante contienne une valeur Null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *de référence du programmeur ODBC SDK*.

### <a name="remarks"></a>Notes

La colonne de source de données doit avoir un type ODBC de SQL_BIT. Le jeu d’enregistrements doit définir un membre de données de champ de type pointeur en BOOL.

Si vous initialisez *prgBoolVals* et *prgLengths* avec la valeur NULL, puis les tableaux ils pointent vers seront allouées automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
>  RFX en bloc transfère uniquement les données à partir de la source de données à l’objet recordset. Pour rendre votre jeu d’enregistrements modifiables, vous devez utiliser la fonction API ODBC `SQLSetPos`.

Pour plus d’informations, consultez les articles [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Consultez [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_byte_bulk"></a>  RFX_Byte_Bulk

Transferts de plusieurs lignes d’octets uniques à partir d’une colonne d’une source de données ODBC dans un tableau correspondant dans un `CRecordset`-objet dérivé.

### <a name="syntax"></a>Syntaxe

```
void RFX_Byte_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un [CFieldExchange](cfieldexchange-class.md) objet. Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*prgByteVals*<br/>
Pointeur vers un tableau de valeurs d’octets. Ce tableau stocke les données seront transférés à partir de la source de données vers le jeu d’enregistrements.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stockera la longueur en octets de chaque valeur dans le tableau vers lequel pointé *prgByteVals*. Notez que la valeur de SQL_NULL_DATA sera stockée si l’élément de données correspondante contienne une valeur Null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *de référence du programmeur ODBC SDK*.

### <a name="remarks"></a>Notes

La colonne de source de données doit avoir un type ODBC de SQL_TINYINT. Le jeu d’enregistrements doit définir un membre de données de champ de type pointeur en octet.

Si vous initialisez *prgByteVals* et *prgLengths* avec la valeur NULL, puis les tableaux ils pointent vers seront allouées automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
>  RFX en bloc transfère uniquement les données à partir de la source de données à l’objet recordset. Pour rendre votre jeu d’enregistrements modifiables, vous devez utiliser la fonction API ODBC `SQLSetPos`.

Pour plus d’informations, consultez les articles [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Consultez [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_date_bulk"></a>  RFX_Date_Bulk

Transferts de plusieurs lignes de données TIMESTAMP_STRUCT à partir d’une colonne d’une source de données ODBC dans un tableau correspondant dans un `CRecordset`-objet dérivé.

### <a name="syntax"></a>Syntaxe

```
void RFX_Date_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   TIMESTAMP_STRUCT** prgTSVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un [CFieldExchange](cfieldexchange-class.md) objet. Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*prgTSVals*<br/>
Pointeur vers un tableau de valeurs TIMESTAMP_STRUCT. Ce tableau stocke les données seront transférés à partir de la source de données vers le jeu d’enregistrements. Pour plus d’informations sur le type de données TIMESTAMP_STRUCT, consultez la rubrique « Types de données C » dans l’annexe D de la *de référence du programmeur ODBC SDK*.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stockera la longueur en octets de chaque valeur dans le tableau vers lequel pointé *prgTSVals*. Notez que la valeur de SQL_NULL_DATA sera stockée si l’élément de données correspondante contienne une valeur Null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *de référence du programmeur ODBC SDK*.

### <a name="remarks"></a>Notes

La colonne de source de données peut avoir un type ODBC de SQL_DATE, SQL_TIME ou SQL_TIMESTAMP. Le jeu d’enregistrements doit définir un membre de données de champ de type pointeur à TIMESTAMP_STRUCT.

Si vous initialisez *prgTSVals* et *prgLengths* avec la valeur NULL, puis les tableaux ils pointent vers seront allouées automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
>  RFX en bloc transfère uniquement les données à partir de la source de données à l’objet recordset. Pour rendre votre jeu d’enregistrements modifiables, vous devez utiliser la fonction API ODBC `SQLSetPos`.

Pour plus d’informations, consultez les articles [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Consultez [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_double_bulk"></a>  RFX_Double_Bulk

Transferts de plusieurs lignes de données à virgule flottante double précision à partir d’une colonne d’une source de données ODBC dans un tableau correspondant dans un `CRecordset`-objet dérivé.

### <a name="syntax"></a>Syntaxe

```
void RFX_Double_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   double** prgDblVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un [CFieldExchange](cfieldexchange-class.md) objet. Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*prgDblVals*<br/>
Un pointeur vers un tableau de **double** valeurs. Ce tableau stocke les données seront transférés à partir de la source de données vers le jeu d’enregistrements.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stockera la longueur en octets de chaque valeur dans le tableau vers lequel pointé *prgDblVals*. Notez que la valeur de SQL_NULL_DATA sera stockée si l’élément de données correspondante contienne une valeur Null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *de référence du programmeur ODBC SDK*.

### <a name="remarks"></a>Notes

La colonne de source de données doit avoir un type ODBC de SQL_DOUBLE. Le jeu d’enregistrements doit définir un membre de données de champ de type pointeur vers **double**.

Si vous initialisez *prgDblVals* et *prgLengths* avec la valeur NULL, puis les tableaux ils pointent vers seront allouées automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
>  RFX en bloc transfère uniquement les données à partir de la source de données à l’objet recordset. Pour rendre votre jeu d’enregistrements modifiables, vous devez utiliser la fonction API ODBC `SQLSetPos`.

Pour plus d’informations, consultez les articles [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Consultez [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_int_bulk"></a>  RFX_Int_Bulk

Transfère les données d’entier entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données d’ODBC tapez SQL_SMALLINT.

### <a name="syntax"></a>Syntaxe

```
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations sur les opérations un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert de jeu d’enregistrements à la source de données, la valeur de type **int**, provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_long_bulk"></a>  RFX_Long_Bulk

Transferts de plusieurs lignes de données de type entier long d’une colonne d’une source de données ODBC dans un tableau correspondant dans un `CRecordset`-objet dérivé.

### <a name="syntax"></a>Syntaxe

```
void RFX_Long_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   long** prgLongVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un [CFieldExchange](cfieldexchange-class.md) objet. Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*prgLongVals*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stocke les données seront transférés à partir de la source de données vers le jeu d’enregistrements.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stockera la longueur en octets de chaque valeur dans le tableau vers lequel pointé *prgLongVals*. Notez que la valeur de SQL_NULL_DATA sera stockée si l’élément de données correspondante contienne une valeur Null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *de référence du programmeur ODBC SDK*.

### <a name="remarks"></a>Notes

La colonne de source de données doit avoir un type ODBC de SQL_INTEGER. Le jeu d’enregistrements doit définir un membre de données de champ de type pointeur vers **long**.

Si vous initialisez *prgLongVals* et *prgLengths* avec la valeur NULL, puis les tableaux ils pointent vers seront allouées automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
>  RFX en bloc transfère uniquement les données à partir de la source de données à l’objet recordset. Pour rendre votre jeu d’enregistrements modifiables, vous devez utiliser la fonction API ODBC `SQLSetPos`.

Pour plus d’informations, consultez les articles [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Consultez [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_single_bulk"></a>  RFX_Single_Bulk

Transferts de plusieurs lignes de données à virgule flottante à partir d’une colonne d’une source de données ODBC dans un tableau correspondant dans un `CRecordset`-objet dérivé.

### <a name="syntax"></a>Syntaxe

```
void RFX_Single_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   float** prgFltVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un [CFieldExchange](cfieldexchange-class.md) objet. Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*prgFltVals*<br/>
Un pointeur vers un tableau de **float** valeurs. Ce tableau stocke les données seront transférés à partir de la source de données vers le jeu d’enregistrements.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stockera la longueur en octets de chaque valeur dans le tableau vers lequel pointé *prgFltVals*. Notez que la valeur de SQL_NULL_DATA sera stockée si l’élément de données correspondante contienne une valeur Null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *de référence du programmeur ODBC SDK*.

### <a name="remarks"></a>Notes

La colonne de source de données doit avoir un type ODBC de SQL_REAL. Le jeu d’enregistrements doit définir un membre de données de champ de type pointeur vers **float**.

Si vous initialisez *prgFltVals* et *prgLengths* avec la valeur NULL, puis les tableaux ils pointent vers seront allouées automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
>  RFX en bloc transfère uniquement les données à partir de la source de données à l’objet recordset. Pour rendre votre jeu d’enregistrements modifiables, vous devez utiliser la fonction API ODBC `SQLSetPos`.

Pour plus d’informations, consultez les articles [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Consultez [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="rfx_text_bulk"></a>  RFX_Text_Bulk

Transferts de plusieurs lignes de données de type caractère à partir d’une colonne d’une source de données ODBC dans un tableau correspondant dans un `CRecordset`-objet dérivé.

### <a name="syntax"></a>Syntaxe

```
void RFX_Text_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   LPSTR* prgStrVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un [CFieldExchange](cfieldexchange-class.md) objet. Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Le nom d’une colonne de données.

*prgStrVals*<br/>
Pointeur vers un tableau de valeurs LPSTR. Ce tableau stocke les données seront transférés à partir de la source de données vers le jeu d’enregistrements. Notez qu’avec la version actuelle d’ODBC, ces valeurs ne peut pas être Unicode.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stockera la longueur en octets de chaque valeur dans le tableau vers lequel pointé *prgStrVals*. Cette durée exclut le caractère de fin null. Notez que la valeur de SQL_NULL_DATA sera stockée si l’élément de données correspondante contienne une valeur Null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *de référence du programmeur ODBC SDK*.

*nMaxLength*<br/>
La longueur des valeurs stockées dans le tableau vers lequel pointé maximale autorisée *prgStrVals*, y compris le caractère de fin null. Pour vous assurer que les données ne seront pas tronquées, passez une valeur suffisamment grande pour contenir l’élément de données plus grand que prévu.

### <a name="remarks"></a>Notes

La colonne de source de données peut avoir un type ODBC de SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL ou SQL_NUMERIC. Le jeu d’enregistrements doit définir un membre de données de champ de type LPSTR.

Si vous initialisez *prgStrVals* et *prgLengths* avec la valeur NULL, puis les tableaux ils pointent vers seront allouées automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
>  RFX en bloc transfère uniquement les données à partir de la source de données à l’objet recordset. Pour rendre votre jeu d’enregistrements modifiables, vous devez utiliser la fonction API ODBC `SQLSetPos`.

Pour plus d’informations, consultez les articles [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Vous devez écrire manuellement les appels votre `DoBulkFieldExchange` remplacer. Cet exemple montre un appel à `RFX_Text_Bulk`, ainsi qu’un appel à `RFX_Long_Bulk`, pour le transfert de données. Ces appels sont précédées par un appel à [CFieldExchange::SetFieldType](CFieldExchange::SetFieldType.md). Notez que pour les paramètres, vous devez appeler les fonctions RFX au lieu des fonctions RFX en bloc.

```cpp
void CMultiCustomer::DoBulkFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Long_Bulk(pFX, _T("[CustomerID]"), &m_pCustomerID, &m_pcCustomerID);
   RFX_Text_Bulk(pFX, _T("[ContactFirstName]"), &m_pContactFirstName, &m_pcContactFirstName, 50);
   RFX_Text_Bulk(pFX, _T("[PostalCode]"), &m_pPostalCode, &m_pcPostalCode, 50);
   RFX_Text_Bulk(pFX, _T("[L_Name]"), &m_pL_Name, &m_pcL_Name, 50);
   RFX_Long_Bulk(pFX, _T("[BillingID]"), &m_pBillingID, &m_pcBillingID);

   pFX->SetFieldType(CFieldExchange::inputParam);
   RFX_Text(pFX, _T("Param"), m_strParam);
}
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

## <a name="dfx_binary"></a>  DFX_Binary

Transfère les tableaux d’octets entre les membres de données de champ d’un [CDaoRecordset](cdaorecordset-class.md) objet et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Binary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CByteArray& value,
   int nPreAllocSize = AFX_DAO_BINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction.

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert de jeu d’enregistrements à la source de données, la valeur de type [CByteArray](cbytearray-class.md), provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

*nPreAllocSize*<br/>
Le framework Préalloue cette quantité de mémoire. Si vos données sont supérieure, le framework sera allouée davantage d’espace en fonction des besoins. Pour de meilleures performances, définissez cette taille à une valeur suffisamment élevée pour empêcher les réallocations. La taille par défaut est définie dans le AFXDAO. Fichier H comme AFX_DAO_BINARY_DEFAULT_SIZE.

*dwBindOptions*<br/>
Une option qui vous permet de tirer parti des mécanisme de double tampon du MFC pour la détection des champs de jeu d’enregistrements qui ont été modifiés. La valeur par défaut, AFX_DAO_DISABLE_FIELD_CACHE le mécanisme, n’utilise pas de mécanisme de double tampon, et vous devez appeler [SetFieldDirty](cdaorecordset-class.md#setfielddirty) et [SetFieldNull](cdaorecordset-class.md#setfieldnull) vous-même. L’autre valeur possible, AFX_DAO_ENABLE_FIELD_CACHE, utilise la double mise en tampon, et vous n’avez pas à effectuer un travail supplémentaire pour marquer des champs modifiés ou Null. Pour des raisons de la mémoire et des performances, évitez cette valeur sauf si vos données binaire sont relativement faible.

> [!NOTE]
>  Vous pouvez contrôler si les données sont double tampon pour tous les champs par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Données sont mappées entre le type DAO_BYTES dans DAO et [CByteArray](cbytearray-class.md) dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

## <a name="dfx_bool"></a>  DFX_Bool

Transfère les données booléennes entre les membres de données de champ d’un [CDaoRecordset](cdaorecordset-class.md) objet et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Bool(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BOOL& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction.

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert à partir du jeu d’enregistrements à la source de données, la valeur de type BOOL, provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Une option qui vous permet de tirer parti des mécanisme de double tampon du MFC pour la détection des champs de jeu d’enregistrements qui ont été modifiés. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise le mécanisme de double tampon. La valeur est également possible AFX_DAO_DISABLE_FIELD_CACHE le mécanisme. Si vous spécifiez cette valeur, MFC n’effectue aucun contrôle sur ce champ. Vous devez appeler `SetFieldDirty` et `SetFieldNull` vous-même.

> [!NOTE]
>  Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Données sont mappées entre DAO_BOOL dans DAO de type et le type BOOL dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

## <a name="dfx_byte"></a>  DFX_Byte

Transferts unique octets entre les membres de données de champ d’un [CDaoRecordset](cdaorecordset-class.md) objet et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Byte(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BYTE& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction.

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert à partir du jeu d’enregistrements à la source de données, la valeur de type BYTE, provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Une option qui vous permet de tirer parti des mécanisme de double tampon du MFC pour la détection des champs de jeu d’enregistrements qui ont été modifiés. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise le mécanisme de double tampon. La valeur est également possible AFX_DAO_DISABLE_FIELD_CACHE le mécanisme. Si vous spécifiez cette valeur, MFC n’effectue aucun contrôle sur ce champ. Vous devez appeler `SetFieldDirty` et `SetFieldNull` vous-même.

> [!NOTE]
>  Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Données sont mappées entre DAO_BYTES dans DAO de type et de type BYTE dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

## <a name="dfx_currency"></a>  DFX_Currency

Transfère les données de devise entre les membres de données de champ d’un [CDaoRecordset](cdaorecordset-class.md) objet et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Currency(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleCurrency& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction.

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert à partir du jeu d’enregistrements à la source de données, cette valeur est prise à partir du membre de données spécifié, de type [COleCurrency](colecurrency-class.md). Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Une option qui vous permet de tirer parti des mécanisme de double tampon du MFC pour la détection des champs de jeu d’enregistrements qui ont été modifiés. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise le mécanisme de double tampon. La valeur est également possible AFX_DAO_DISABLE_FIELD_CACHE le mécanisme. Si vous spécifiez cette valeur, MFC n’effectue aucun contrôle sur ce champ. Vous devez appeler `SetFieldDirty` et `SetFieldNull` vous-même.

> [!NOTE]
>  Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Données sont mappées entre le type DAO_CURRENCY dans DAO et [COleCurrency](colecurrency-class.md) dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

## <a name="dfx_datetime"></a>  DFX_DateTime

Transfère les données de date et l’heure entre les membres de données de champ d’un [CDaoRecordset](cdaorecordset-class.md) objet et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_DateTime(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleDateTime& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction.

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. La fonction accepte une référence à un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objet. Pour un transfert à partir du jeu d’enregistrements à la source de données, cette valeur provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Une option qui vous permet de tirer parti des mécanisme de double tampon du MFC pour la détection des champs de jeu d’enregistrements qui ont été modifiés. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise le mécanisme de double tampon. La valeur est également possible AFX_DAO_DISABLE_FIELD_CACHE le mécanisme. Si vous spécifiez cette valeur, MFC n’effectue aucun contrôle sur ce champ. Vous devez appeler `SetFieldDirty` et `SetFieldNull` vous-même.

> [!NOTE]
>  Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Données sont mappées entre le type DAO_DATE dans DAO et [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) dans le jeu d’enregistrements.

> [!NOTE]
>  `COleDateTime` remplace [CTime](../../atl-mfc-shared/reference/ctime-class.md) et TIMESTAMP_STRUCT à cet effet dans les classes DAO. `CTime` et TIMESTAMP_STRUCT sont toujours utilisés pour les classes d’accès aux données basées sur ODBC.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

## <a name="dfx_double"></a>  DFX_Double

Transferts **float double** des données entre les membres de données de champ d’un [CDaoRecordset](cdaorecordset-class.md) objet et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Double(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   double& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction.

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert de jeu d’enregistrements à la source de données, la valeur de type **double**, provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Une option qui vous permet de tirer parti des mécanisme de double tampon du MFC pour la détection des champs de jeu d’enregistrements qui ont été modifiés. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise le mécanisme de double tampon. La valeur est également possible AFX_DAO_DISABLE_FIELD_CACHE le mécanisme. Si vous spécifiez cette valeur, MFC n’effectue aucun contrôle sur ce champ. Vous devez appeler `SetFieldDirty` et `SetFieldNull` vous-même.

> [!NOTE]
>  Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Données sont mappées entre le type DAO_R8 dans DAO et type **float double** dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

## <a name="dfx_long"></a>  DFX_Long

Transfère les données de type entier long entre les membres de données de champ d’un [CDaoRecordset](cdaorecordset-class.md) objet et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Long(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   long& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction.

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert de jeu d’enregistrements à la source de données, la valeur de type **long**, provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Une option qui vous permet de tirer parti des mécanisme de double tampon du MFC pour la détection des champs de jeu d’enregistrements qui ont été modifiés. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise le mécanisme de double tampon. La valeur est également possible AFX_DAO_DISABLE_FIELD_CACHE le mécanisme. Si vous spécifiez cette valeur, MFC n’effectue aucun contrôle sur ce champ. Vous devez appeler `SetFieldDirty` et `SetFieldNull` vous-même.

> [!NOTE]
>  Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Données sont mappées entre le type DAO_I4 dans DAO et type **long** dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

## <a name="dfx_longbinary"></a>  DFX_LongBinary

**Important** il est recommandé d’utiliser [DFX_Binary](#dfx_binary) au lieu de cette fonction.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_LongBinary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CLongBinary& value,
   DWORD dwPreAllocSize = AFX_DAO_LONGBINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction.

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert de jeu d’enregistrements à la source de données, la valeur de type [CLongBinary](clongbinary-class.md), provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

*dwPreAllocSize*<br/>
Le framework Préalloue cette quantité de mémoire. Si vos données sont supérieure, le framework sera allouée davantage d’espace en fonction des besoins. Pour de meilleures performances, définissez cette taille à une valeur suffisamment élevée pour empêcher les réallocations.

*dwBindOptions*<br/>
Une option qui vous permet de tirer parti des mécanisme de double tampon du MFC pour la détection des champs de jeu d’enregistrements qui ont été modifiés. La valeur par défaut, AFX_DISABLE_FIELD_CACHE, n’utilise pas de mécanisme de double tampon. La valeur est également possible AFX_DAO_ENABLE_FIELD_CACHE. Le mécanisme de double tampon utilise et vous n’avez pas à effectuer un travail supplémentaire pour marquer des champs modifiés ou Null. Pour des raisons de la mémoire et des performances, évitez cette valeur sauf si vos données binaire sont relativement faible.

> [!NOTE]
>  Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

`DFX_LongBinary` est fourni pour la compatibilité avec les classes ODBC MFC. Le `DFX_LongBinary` fonction transfère les données binaires-objets volumineux (BLOB) à l’aide de la classe `CLongBinary` entre les membres de données de champ d’un [CDaoRecordset](cdaorecordset-class.md) objet et les colonnes d’un enregistrement sur la source de données. Données sont mappées entre le type DAO_BYTES dans DAO et [CLongBinary](clongbinary-class.md) dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

## <a name="dfx_short"></a>  DFX_Short

Transferts abrégée des données de type entier entre les membres de données de champ d’un [CDaoRecordset](cdaorecordset-class.md) objet et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Short(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   short& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction.

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert de jeu d’enregistrements à la source de données, la valeur de type **court**, provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Une option qui vous permet de tirer parti des mécanisme de double tampon du MFC pour la détection des champs de jeu d’enregistrements qui ont été modifiés. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise le mécanisme de double tampon. La valeur est également possible AFX_DAO_DISABLE_FIELD_CACHE le mécanisme. Si vous spécifiez cette valeur, MFC n’effectue aucun contrôle sur ce champ. Vous devez appeler `SetFieldDirty` et `SetFieldNull` vous-même.

> [!NOTE]
>  Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Données sont mappées entre le type DAO_I2 dans DAO et type **court** dans le jeu d’enregistrements.

> [!NOTE]
>  `DFX_Short` équivaut à [RFX_Int](#rfx_int) pour les classes basées sur ODBC.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

## <a name="dfx_single"></a>  DFX_Single

Transfère les données à virgule flottante entre les membres de données de champ d’un [CDaoRecordset](cdaorecordset-class.md) objet et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Single(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   float& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction.

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert de jeu d’enregistrements à la source de données, la valeur de type **float**, provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Une option qui vous permet de tirer parti des mécanisme de double tampon du MFC pour la détection des champs de jeu d’enregistrements qui ont été modifiés. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise le mécanisme de double tampon. La valeur est également possible AFX_DAO_DISABLE_FIELD_CACHE le mécanisme. Si vous spécifiez cette valeur, MFC n’effectue aucun contrôle sur ce champ. Vous devez appeler `SetFieldDirty` et `SetFieldNull` vous-même.

> [!NOTE]
>  Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Données sont mappées entre le type DAO_R4 dans DAO et type **float** dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

## <a name="dfx_text"></a>  DFX_Text

Transferts `CString` des données entre les membres de données de champ d’un [CDaoRecordset](cdaorecordset-class.md) objet et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI DFX_Text(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CString& value,
   int nPreAllocSize = AFX_DAO_TEXT_DEFAULT_SIZE,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Un pointeur vers un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte pour chaque appel de la fonction.

*szName*<br/>
Le nom d’une colonne de données.

*valeur*<br/>
La valeur stockée dans le membre de données indiqué, la valeur doit être transféré. Pour un transfert de jeu d’enregistrements à la source de données, la valeur de type [CString](../../atl-mfc-shared/reference/cstringt-class.md), provient de la donnée membre spécifiée. Pour un transfert à partir de la source de données vers le recordset, la valeur est stockée dans le membre de données spécifié.

*nPreAllocSize*<br/>
Le framework Préalloue cette quantité de mémoire. Si vos données sont supérieure, le framework sera allouée davantage d’espace en fonction des besoins. Pour de meilleures performances, définissez cette taille à une valeur suffisamment élevée pour empêcher les réallocations.

*dwBindOptions*<br/>
Une option qui vous permet de tirer parti des mécanisme de double tampon du MFC pour la détection des champs de jeu d’enregistrements qui ont été modifiés. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise le mécanisme de double tampon. La valeur est également possible AFX_DAO_DISABLE_FIELD_CACHE le mécanisme. Si vous spécifiez cette valeur, MFC n’effectue aucun contrôle sur ce champ. Vous devez appeler [SetFieldDirty](cdaorecordset-class.md#setfielddirty) et [SetFieldNull](cdaorecordset-class.md#setfieldnull) vous-même.

> [!NOTE]
>  Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont mappées entre type DAO_CHAR dans DAO (ou, si le symbole _UNICODE est défini, DAO_WCHAR) et le type [CString](../../atl-mfc-shared/reference/cstringt-class.md) dans le jeu d’enregistrements.  n

### <a name="example"></a>Exemple

Cet exemple illustre plusieurs appels à `DFX_Text`. Notez également les deux appels à [CDaoFieldExchange::SetFieldType](cdaofieldexchange-class.md#setfieldtype). Vous devez écrire le premier appel à `SetFieldType` et son **DFX** appeler. Le deuxième appel et elle est associée **DFX** appels sont normalement écrits par l’Assistant de code qui a généré la classe.

```cpp
void CCustSet::DoFieldExchange(CDaoFieldExchange* pFX)
{
   pFX->SetFieldType(CDaoFieldExchange::param);
   DFX_Text(pFX, _T("Param"), m_strParam);
   pFX->SetFieldType(CDaoFieldExchange::outputColumn);
   DFX_Short(pFX, _T("EmployeeID"), m_EmployeeID);
   DFX_Text(pFX, _T("LastName"), m_LastName);
   DFX_Short(pFX, _T("Age"), m_Age);
   DFX_DateTime(pFX, _T("hire_date"), m_hire_date);
   DFX_DateTime(pFX, _T("termination_date"), m_termination_date);

   CDaoRecordset::DoFieldExchange(pFX);
}
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[CRecordset::DoFieldExchange](crecordset-class.md#dofieldexchange)<br/>
[CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)<br/>
[CDaoRecordset::DoFieldExchange](cdaorecordset-class.md#dofieldexchange)

