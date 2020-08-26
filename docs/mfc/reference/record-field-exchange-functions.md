---
title: Fonctions Record Field Exchange (RFX)
ms.date: 09/17/2019
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
ms.openlocfilehash: 9bb1b7bcbce16bba8029fcfbbeea7552b1d4a0ba
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843597"
---
# <a name="record-field-exchange-functions"></a>Fonctions Record Field Exchange (RFX)

Cette rubrique répertorie les fonctions d’échange de champs d’enregistrements (RFX, RFX en bloc et DFX) permettant d’automatiser le transfert de données entre un objet recordset et sa source de données et d’effectuer d’autres opérations sur les données.

Si vous utilisez les classes ODBC et que vous avez implémenté l’extraction de lignes en bloc, vous devez remplacer manuellement la fonction membre `DoBulkFieldExchange` de `CRecordset` en appelant les fonctions RFX en bloc pour chaque membre de données correspondant à une colonne de source de données.

Si vous n’avez pas implémenté l’extraction de lignes en bloc dans les classes basées sur ODBC, ou si vous utilisez les classes basées sur DAO (obsolètes), ClassWizard remplace la `DoFieldExchange` fonction membre de `CRecordset` ou `CDaoRecordset` en appelant les fonctions RFX (pour les classes ODBC) ou les fonctions DFX (pour les classes DAO) pour chaque membre de données de champ dans votre Recordset.

Les fonctions d’échange de champs d’enregistrements transfèrent des données chaque fois que l’infrastructure appelle `DoFieldExchange` ou `DoBulkFieldExchange`. Chaque fonction transfère un type de données spécifique.

Pour plus d’informations sur l’utilisation de ces fonctions, consultez les articles [Record Field Exchange : fonctionnement de RFX (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Pour les colonnes de données que vous liez dynamiquement, vous pouvez aussi appeler les fonctions RFX et DFX par vous-même, comme expliqué dans les articles [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). Par ailleurs, vous pouvez écrire vos propres routines RFX ou DFX personnalisées, comme l’explique la Note technique [43](../../mfc/tn043-rfx-routines.md) (pour ODBC) et la Note technique [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (pour DAO).

Pour obtenir un exemple de fonctions RFX et RFX en bloc telles qu’elles apparaissent dans les `DoFieldExchange` `DoBulkFieldExchange` fonctions et, consultez [RFX_Text](#rfx_text) et [RFX_Text_Bulk] #rfx_text_bulk). Les fonctions DFX sont très similaires aux fonctions RFX.

### <a name="rfx-functions-odbc"></a>Fonctions RFX (ODBC)

|Nom|Description|
|-|-|
|[RFX_Binary](#rfx_binary)|Transfère les tableaux d’octets de type [CByteArray](cbytearray-class.md).|
|[RFX_Bool](#rfx_bool)|Transfère les données de type Boolean.|
|[RFX_Byte](#rfx_byte)|Transfère un seul octet de données.|
|[RFX_Date](#rfx_date)|Transfère les données d’heure et de date à l’aide de [ctime](../../atl-mfc-shared/reference/ctime-class.md) ou TIMESTAMP_STRUCT.|
|[RFX_Double](#rfx_double)|Transfère les données de type Float double précision.|
|[RFX_Int](#rfx_int)|Transfère les données de type Integer.|
|[RFX_Long](#rfx_long)|Transfère les données de type Long Integer.|
|[RFX_LongBinary](#rfx_longbinary)|Transfère les données BLOB avec un objet de la classe [CLongBinary](clongbinary-class.md) .|
|[RFX_Single](#rfx_single)|Transfère les données de type Float.|
|[RFX_Text](#rfx_text)|Transfère les données de type String.|

### <a name="bulk-rfx-functions-odbc"></a>Fonctions RFX en bloc (ODBC)

|Nom|Description|
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

|Nom|Description|
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

## <a name="rfx_binary"></a><a name="rfx_binary"></a> RFX_Binary

Transfère les tableaux d’octets entre les données membres de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_BINARY, SQL_VARBINARY ou SQL_LONGVARBINARY.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Binary(
   CFieldExchange* pFX,
   const char* szName,
   CByteArray& value,
   int nMaxLength = 255);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations sur les opérations qu’un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur de type [CByteArray](cbytearray-class.md)est extraite du membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

*nMaxLength*<br/>
Longueur maximale autorisée de la chaîne ou du tableau en cours de transfert. La valeur par défaut de *nMaxLength* est 255. Les valeurs autorisées sont comprises entre 1 et INT_MAX. L’infrastructure alloue cette quantité d’espace pour les données. Pour des performances optimales, transmettez une valeur suffisamment grande pour accueillir le plus grand élément de données que vous attendez.

### <a name="remarks"></a>Notes

Les données de la source de données de ces types sont mappées vers et à partir du type `CByteArray` dans le Recordset.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_bool"></a><a name="rfx_bool"></a> RFX_Bool

Transfère des données booléennes entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_BIT.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations sur les opérations qu’un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type BOOL, provient du membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_byte"></a><a name="rfx_byte"></a> RFX_Byte

Transfère les octets uniques entre les données membres de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_TINYINT.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations sur les opérations qu’un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type BYTE, est extraite du membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_date"></a><a name="rfx_date"></a> RFX_Date

Transfère `CTime` ou TIMESTAMP_STRUCT des données entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_DATE, SQL_TIME ou SQL_TIMESTAMP.

### <a name="syntax"></a>Syntaxe

```cpp
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
Pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations sur les opérations qu’un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans le membre de données indiqué ; valeur à transférer. Les différentes versions de la fonction prennent des types de données différents pour la valeur :

La première version de la fonction prend une référence à un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) . Pour un transfert d’un jeu d’enregistrements à une source de données, cette valeur est extraite du membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

La deuxième version de la fonction prend une référence à une `TIMESTAMP_STRUCT` structure. Vous devez configurer cette structure vous-même avant l’appel. Aucune prise en charge de l’échange de données de boîtes de dialogue (DDX) ni prise en charge de l’Assistant code n’est disponible pour cette version. La troisième version de la fonction fonctionne de la même façon que la première version, sauf qu’elle prend une référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) .

### <a name="remarks"></a>Notes

La `CTime` version de la fonction impose la surcharge liée à un traitement intermédiaire et a une plage relativement limitée. Si vous constatez que l’un de ces facteurs est trop restrictif, utilisez la deuxième version de la fonction. Mais notez l’absence de l’Assistant Code et la prise en charge de DDX et la nécessité de configurer vous-même la structure.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_double"></a><a name="rfx_double"></a> RFX_Double

Transfère les données à **double flotte** entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_DOUBLE.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations sur les opérations qu’un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type, provient du **`double`** membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_int"></a><a name="rfx_int"></a> RFX_Int

Transfère les données de type entier entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_SMALLINT.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations sur les opérations qu’un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type, provient du **`int`** membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_long"></a><a name="rfx_long"></a> RFX_Long

Transfère les données d’entier long entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_INTEGER.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Long(
   CFieldExchange* pFX,
   const char* szName,
   LONG&
value );
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations sur les opérations qu’un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type, provient du **`long`** membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_longbinary"></a><a name="rfx_longbinary"></a> RFX_LongBinary

Transfère les données BLOB (Binary Large Object) à l’aide de la classe [CLongBinary](clongbinary-class.md) entre les données membres de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_LONGVARBINARY ou SQL_LONGVARCHAR.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations sur les opérations qu’un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type, provient du `CLongBinary` membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_single"></a><a name="rfx_single"></a> RFX_Single

Transfère les données à virgule flottante entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_REAL.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations sur les opérations qu’un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type, provient du **`float`** membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_text"></a><a name="rfx_text"></a> RFX_Text

Transfère des `CString` données entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL ou Sql_Numeric.

### <a name="syntax"></a>Syntaxe

```cpp
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
Pointeur vers un objet de classe `CFieldExchange` . Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations sur les opérations qu’un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type, provient du `CString` membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

*nMaxLength*<br/>
Longueur maximale autorisée de la chaîne ou du tableau en cours de transfert. La valeur par défaut de *nMaxLength* est 255. Les valeurs autorisées sont comprises entre 1 et INT_MAX). L’infrastructure alloue cette quantité d’espace pour les données. Pour des performances optimales, transmettez une valeur suffisamment grande pour accueillir le plus grand élément de données que vous attendez.

*nColumnType*<br/>
Utilisé principalement pour les paramètres. Entier qui indique le type de données du paramètre. Le type est un type de données ODBC de la forme **SQL_XXX**.

*nScale*<br/>
Spécifie l’échelle pour les valeurs de type ODBC SQL_DECIMAL ou SQL_NUMERIC. *nScale* est utile uniquement lors de la définition de valeurs de paramètre. Pour plus d’informations, consultez la rubrique sur la précision, l’échelle, la longueur et la taille d’affichage dans l’annexe D du *Guide de référence du programmeur du kit de développement logiciel (SDK) ODBC*.

### <a name="remarks"></a>Notes

Les données de la source de données de tous ces types sont mappées vers et à partir de `CString` dans le Recordset.

### <a name="example"></a>Exemple

Cet exemple illustre plusieurs appels à `RFX_Text` . Notez également les deux appels à `CFieldExchange::SetFieldType` . Pour les paramètres, vous devez écrire l’appel à `SetFieldType` et son appel RFX. L’appel de colonne de sortie et ses appels RFX associés sont généralement écrits par un assistant de code.

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

**En-tête :** AFXDB. h

## <a name="rfx_binary_bulk"></a><a name="rfx_binary_bulk"></a> RFX_Binary_Bulk

Transfère plusieurs lignes de données d’octets d’une colonne d’une source de données ODBC vers un tableau correspondant dans un `CRecordset` objet dérivé de.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Binary_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet [CFieldExchange](cfieldexchange-class.md) . Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*prgByteVals*<br/>
Pointeur vers un tableau de valeurs d’octets. Ce tableau stocke les données à transférer de la source de données vers le Recordset.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stocke la longueur en octets de chaque valeur du tableau pointé par *prgByteVals*. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *Guide de référence du programmeur ODBC SDK*.

*nMaxLength*<br/>
Longueur maximale autorisée des valeurs stockées dans le tableau pointé par *prgByteVals*. Pour vous assurer que les données ne seront pas tronquées, transmettez une valeur suffisamment grande pour accueillir le plus grand élément de données attendu.

### <a name="remarks"></a>Notes

La colonne de source de données peut avoir un type ODBC de SQL_BINARY, SQL_VARBINARY ou SQL_LONGVARBINARY. Le jeu d’enregistrements doit définir un membre de données de champ de type pointeur vers octet.

Si vous initialisez *prgByteVals* et *prgLengths* sur null, les tableaux vers lesquels ils pointent sont alloués automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
> L’échange de champs d’enregistrements en bloc transfère uniquement les données de la source de données vers l’objet Recordset. Pour que votre jeu d’enregistrements puisse être mis à jour, vous devez utiliser la fonction API ODBC `SQLSetPos` .

Pour plus d’informations, consultez l’article [Recordset : extraction d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [RFX (Record Field Exchange](../../data/odbc/record-field-exchange-rfx.md)).

### <a name="example"></a>Exemple

Consultez [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_bool_bulk"></a><a name="rfx_bool_bulk"></a> RFX_Bool_Bulk

Transfère plusieurs lignes de données booléennes d’une colonne d’une source de données ODBC vers un tableau correspondant dans un `CRecordset` objet dérivé de.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Bool_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BOOL** prgBoolVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet [CFieldExchange](cfieldexchange-class.md) . Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*prgBoolVals*<br/>
Pointeur vers un tableau de valeurs BOOL. Ce tableau stocke les données à transférer de la source de données vers le Recordset.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stocke la longueur en octets de chaque valeur du tableau pointé par *prgBoolVals*. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *Guide de référence du programmeur ODBC SDK*.

### <a name="remarks"></a>Notes

La colonne de source de données doit avoir un type ODBC de SQL_BIT. Le Recordset doit définir un membre de données de champ de type pointeur sur BOOL.

Si vous initialisez *prgBoolVals* et *prgLengths* sur null, les tableaux vers lesquels ils pointent sont alloués automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
> L’échange de champs d’enregistrements en bloc transfère uniquement les données de la source de données vers l’objet Recordset. Pour mettre à jour votre jeu d’enregistrements, vous devez utiliser la fonction API ODBC `SQLSetPos` .

Pour plus d’informations, consultez l’article [Recordset : extraction d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [RFX (Record Field Exchange](../../data/odbc/record-field-exchange-rfx.md)).

### <a name="example"></a>Exemple

Consultez [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_byte_bulk"></a><a name="rfx_byte_bulk"></a> RFX_Byte_Bulk

Transfère plusieurs lignes d’un seul octet d’une colonne d’une source de données ODBC vers un tableau correspondant dans un `CRecordset` objet dérivé de.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Byte_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet [CFieldExchange](cfieldexchange-class.md) . Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*prgByteVals*<br/>
Pointeur vers un tableau de valeurs d’octets. Ce tableau stocke les données à transférer de la source de données vers le Recordset.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stocke la longueur en octets de chaque valeur du tableau pointé par *prgByteVals*. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *Guide de référence du programmeur ODBC SDK*.

### <a name="remarks"></a>Notes

La colonne de source de données doit avoir un type ODBC de SQL_TINYINT. Le jeu d’enregistrements doit définir un membre de données de champ de type pointeur vers octet.

Si vous initialisez *prgByteVals* et *prgLengths* sur null, les tableaux vers lesquels ils pointent sont alloués automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
> L’échange de champs d’enregistrements en bloc transfère uniquement les données de la source de données vers l’objet Recordset. Pour mettre à jour votre jeu d’enregistrements, vous devez utiliser la fonction API ODBC `SQLSetPos` .

Pour plus d’informations, consultez l’article [Recordset : extraction d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [RFX (Record Field Exchange](../../data/odbc/record-field-exchange-rfx.md)).

### <a name="example"></a>Exemple

Consultez [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_date_bulk"></a><a name="rfx_date_bulk"></a> RFX_Date_Bulk

Transfère plusieurs lignes de TIMESTAMP_STRUCT données d’une colonne d’une source de données ODBC vers un tableau correspondant dans un `CRecordset` objet dérivé de.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Date_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   TIMESTAMP_STRUCT** prgTSVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet [CFieldExchange](cfieldexchange-class.md) . Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*prgTSVals*<br/>
Pointeur vers un tableau de valeurs TIMESTAMP_STRUCT. Ce tableau stocke les données à transférer de la source de données vers le Recordset. Pour plus d’informations sur le type de données TIMESTAMP_STRUCT, consultez la rubrique « types de données C » dans l’annexe D du *Guide de référence du programmeur du kit de développement logiciel (SDK) ODBC*.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stocke la longueur en octets de chaque valeur du tableau pointé par *prgTSVals*. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *Guide de référence du programmeur ODBC SDK*.

### <a name="remarks"></a>Notes

La colonne de source de données peut avoir un type ODBC de SQL_DATE, SQL_TIME ou SQL_TIMESTAMP. Le Recordset doit définir un membre de données de champ de type pointeur sur TIMESTAMP_STRUCT.

Si vous initialisez *prgTSVals* et *prgLengths* sur null, les tableaux vers lesquels ils pointent sont alloués automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
> L’échange de champs d’enregistrements en bloc transfère uniquement les données de la source de données vers l’objet Recordset. Pour mettre à jour votre jeu d’enregistrements, vous devez utiliser la fonction API ODBC `SQLSetPos` .

Pour plus d’informations, consultez l’article [Recordset : extraction d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [RFX (Record Field Exchange](../../data/odbc/record-field-exchange-rfx.md)).

### <a name="example"></a>Exemple

Consultez [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_double_bulk"></a><a name="rfx_double_bulk"></a> RFX_Double_Bulk

Transfère plusieurs lignes de données à virgule flottante double précision d’une colonne d’une source de données ODBC vers un tableau correspondant dans un `CRecordset` objet dérivé de.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Double_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   double** prgDblVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet [CFieldExchange](cfieldexchange-class.md) . Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*prgDblVals*<br/>
Pointeur vers un tableau de **`double`** valeurs. Ce tableau stocke les données à transférer de la source de données vers le Recordset.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stocke la longueur en octets de chaque valeur du tableau pointé par *prgDblVals*. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *Guide de référence du programmeur ODBC SDK*.

### <a name="remarks"></a>Notes

La colonne de source de données doit avoir un type ODBC de SQL_DOUBLE. Le jeu d’enregistrements doit définir un membre de données de champ de type pointeur vers **`double`** .

Si vous initialisez *prgDblVals* et *prgLengths* sur null, les tableaux vers lesquels ils pointent sont alloués automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
> L’échange de champs d’enregistrements en bloc transfère uniquement les données de la source de données vers l’objet Recordset. Pour mettre à jour votre jeu d’enregistrements, vous devez utiliser la fonction API ODBC `SQLSetPos` .

Pour plus d’informations, consultez l’article [Recordset : extraction d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [RFX (Record Field Exchange](../../data/odbc/record-field-exchange-rfx.md)).

### <a name="example"></a>Exemple

Consultez [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_int_bulk"></a><a name="rfx_int_bulk"></a> RFX_Int_Bulk

Transfère les données de type entier entre les membres de données de champ d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_SMALLINT.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations sur les opérations qu’un `CFieldExchange` objet peut spécifier, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type, provient du **`int`** membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

### <a name="example"></a>Exemple

Consultez [RFX_Text](#rfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_long_bulk"></a><a name="rfx_long_bulk"></a> RFX_Long_Bulk

Transfère plusieurs lignes de données de type entier long d’une colonne d’une source de données ODBC vers un tableau correspondant dans un `CRecordset` objet dérivé de.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Long_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   long** prgLongVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet [CFieldExchange](cfieldexchange-class.md) . Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*prgLongVals*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stocke les données à transférer de la source de données vers le Recordset.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stocke la longueur en octets de chaque valeur du tableau pointé par *prgLongVals*. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *Guide de référence du programmeur ODBC SDK*.

### <a name="remarks"></a>Notes

La colonne de source de données doit avoir un type ODBC de SQL_INTEGER. Le jeu d’enregistrements doit définir un membre de données de champ de type pointeur vers **`long`** .

Si vous initialisez *prgLongVals* et *prgLengths* sur null, les tableaux vers lesquels ils pointent sont alloués automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
> L’échange de champs d’enregistrements en bloc transfère uniquement les données de la source de données vers l’objet Recordset. Pour mettre à jour votre jeu d’enregistrements, vous devez utiliser la fonction API ODBC `SQLSetPos` .

Pour plus d’informations, consultez l’article [Recordset : extraction d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [RFX (Record Field Exchange](../../data/odbc/record-field-exchange-rfx.md)).

### <a name="example"></a>Exemple

Consultez [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_single_bulk"></a><a name="rfx_single_bulk"></a> RFX_Single_Bulk

Transfère plusieurs lignes de données à virgule flottante à partir d’une colonne d’une source de données ODBC vers un tableau correspondant dans un `CRecordset` objet dérivé de.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Single_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   float** prgFltVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet [CFieldExchange](cfieldexchange-class.md) . Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*prgFltVals*<br/>
Pointeur vers un tableau de **`float`** valeurs. Ce tableau stocke les données à transférer de la source de données vers le Recordset.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stocke la longueur en octets de chaque valeur du tableau pointé par *prgFltVals*. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *Guide de référence du programmeur ODBC SDK*.

### <a name="remarks"></a>Notes

La colonne de source de données doit avoir un type ODBC de SQL_REAL. Le jeu d’enregistrements doit définir un membre de données de champ de type pointeur vers **`float`** .

Si vous initialisez *prgFltVals* et *prgLengths* sur null, les tableaux vers lesquels ils pointent sont alloués automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
> L’échange de champs d’enregistrements en bloc transfère uniquement les données de la source de données vers l’objet Recordset. Pour mettre à jour votre jeu d’enregistrements, vous devez utiliser la fonction API ODBC `SQLSetPos` .

Pour plus d’informations, consultez l’article [Recordset : extraction d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [RFX (Record Field Exchange](../../data/odbc/record-field-exchange-rfx.md)).

### <a name="example"></a>Exemple

Consultez [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Configuration requise

**En-tête :** AFXDB. h

## <a name="rfx_text_bulk"></a><a name="rfx_text_bulk"></a> RFX_Text_Bulk

Transfère plusieurs lignes de données de caractères à partir d’une colonne d’une source de données ODBC vers un tableau correspondant dans un `CRecordset` objet dérivé de.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Text_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   LPSTR* prgStrVals,
   long** prgLengths,
   int nMaxLength);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet [CFieldExchange](cfieldexchange-class.md) . Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, consultez l’article [Record Field Exchange : fonctionnement de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName*<br/>
Nom d’une colonne de données.

*prgStrVals*<br/>
Pointeur vers un tableau de valeurs LPSTR. Ce tableau stocke les données à transférer de la source de données vers le Recordset. Notez qu’avec la version actuelle d’ODBC, ces valeurs ne peuvent pas être au format Unicode.

*prgLengths*<br/>
Pointeur vers un tableau d’entiers longs. Ce tableau stocke la longueur en octets de chaque valeur du tableau pointé par *prgStrVals*. Cette longueur exclut le caractère de fin null. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur null. Pour plus d’informations, consultez la fonction API ODBC `SQLBindCol` dans le *Guide de référence du programmeur ODBC SDK*.

*nMaxLength*<br/>
Longueur maximale autorisée des valeurs stockées dans le tableau pointé par *prgStrVals*, y compris le caractère de fin null. Pour vous assurer que les données ne seront pas tronquées, transmettez une valeur suffisamment grande pour accueillir le plus grand élément de données attendu.

### <a name="remarks"></a>Notes

La colonne de source de données peut avoir un type ODBC de SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL ou SQL_NUMERIC. Le jeu d’enregistrements doit définir un membre de données de champ de type LPSTR.

Si vous initialisez *prgStrVals* et *prgLengths* sur null, les tableaux vers lesquels ils pointent sont alloués automatiquement, avec des tailles égales à la taille de l’ensemble de lignes.

> [!NOTE]
> L’échange de champs d’enregistrements en bloc transfère uniquement les données de la source de données vers l’objet Recordset. Pour mettre à jour votre jeu d’enregistrements, vous devez utiliser la fonction API ODBC `SQLSetPos` .

Pour plus d’informations, consultez l’article [Recordset : extraction d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [RFX (Record Field Exchange](../../data/odbc/record-field-exchange-rfx.md)).

### <a name="example"></a>Exemple

Vous devez écrire manuellement les appels dans votre `DoBulkFieldExchange` remplacement. Cet exemple montre un appel à `RFX_Text_Bulk` , ainsi qu’un appel à `RFX_Long_Bulk` , pour le transfert de données. Ces appels sont précédés d’un appel à [CFieldExchange :: SetFieldType](cfieldexchange-class.md#setfieldtype). Notez que pour les paramètres, vous devez appeler les fonctions RFX à la place des fonctions RFX en bloc.

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

**En-tête :** AFXDB. h

## <a name="dfx_binary"></a><a name="dfx_binary"></a> DFX_Binary

Transfère les tableaux d’octets entre les membres de données de champ d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Binary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CByteArray& value,
   int nPreAllocSize = AFX_DAO_BINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de la classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur de type [CByteArray](cbytearray-class.md)est extraite du membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

*nPreAllocSize*<br/>
L’infrastructure Préalloue cette quantité de mémoire. Si vos données sont plus volumineuses, l’infrastructure allouera plus d’espace en fonction des besoins. Pour de meilleures performances, définissez cette taille sur une valeur suffisamment grande pour empêcher les réallocations. La taille par défaut est définie dans AFXDAO. Fichier H en tant que AFX_DAO_BINARY_DEFAULT_SIZE.

*dwBindOptions*<br/>
Option qui vous permet de tirer parti du mécanisme de double mise en mémoire tampon de MFC pour la détection des champs du Recordset qui ont changé. La valeur par défaut, AFX_DAO_DISABLE_FIELD_CACHE, n’utilise pas la double mise en mémoire tampon et vous devez appeler [SetFieldDirty](cdaorecordset-class.md#setfielddirty) et [SetFieldNull](cdaorecordset-class.md#setfieldnull) vous-même. L’autre valeur possible, AFX_DAO_ENABLE_FIELD_CACHE, utilise la double mise en mémoire tampon et vous n’avez pas à effectuer de travail supplémentaire pour marquer les champs comme modifiés ou null. Pour des raisons de performances et de mémoire, évitez cette valeur, sauf si vos données binaires sont relativement petites.

> [!NOTE]
> Vous pouvez contrôler si les données sont double mise en mémoire tampon pour tous les champs par défaut en définissant [CDaoRecordset :: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont mappées entre le type DAO_BYTES dans DAO et le type [CByteArray](cbytearray-class.md) dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao. h

## <a name="dfx_bool"></a><a name="dfx_bool"></a> DFX_Bool

Transfère des données booléennes entre les membres de données de champ d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Bool(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BOOL& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de la classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type BOOL, provient du membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Option qui vous permet de tirer parti du mécanisme de double mise en mémoire tampon de MFC pour la détection des champs du Recordset qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise la double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas ce champ. Vous devez appeler `SetFieldDirty` et vous `SetFieldNull` -même.

> [!NOTE]
> Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset :: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont mappées entre le type DAO_BOOL dans DAO et le type BOOL dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao. h

## <a name="dfx_byte"></a><a name="dfx_byte"></a> DFX_Byte

Transfère un seul octet entre les données membres de champ d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Byte(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BYTE& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de la classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type BYTE, est extraite du membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Option qui vous permet de tirer parti du mécanisme de double mise en mémoire tampon de MFC pour la détection des champs du Recordset qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise la double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas ce champ. Vous devez appeler `SetFieldDirty` et vous `SetFieldNull` -même.

> [!NOTE]
> Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset :: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont mappées entre le type DAO_BYTES dans DAO et le type BYTE dans le Recordset.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao. h

## <a name="dfx_currency"></a><a name="dfx_currency"></a> DFX_Currency

Transfère les données monétaires entre les membres de données de champ d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Currency(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleCurrency& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de la classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, cette valeur est extraite du membre de données spécifié, de type [COleCurrency](colecurrency-class.md). Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Option qui vous permet de tirer parti du mécanisme de double mise en mémoire tampon de MFC pour la détection des champs du Recordset qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise la double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas ce champ. Vous devez appeler `SetFieldDirty` et vous `SetFieldNull` -même.

> [!NOTE]
> Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset :: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont mappées entre le type DAO_CURRENCY dans DAO et le type [COleCurrency](colecurrency-class.md) dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao. h

## <a name="dfx_datetime"></a><a name="dfx_datetime"></a> DFX_DateTime

Transfère les données de date et d’heure entre les membres de données de champ d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_DateTime(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleDateTime& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de la classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. La fonction prend une référence à un objet [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) . Pour un transfert d’un jeu d’enregistrements à une source de données, cette valeur est extraite du membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Option qui vous permet de tirer parti du mécanisme de double mise en mémoire tampon de MFC pour la détection des champs du Recordset qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise la double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas ce champ. Vous devez appeler `SetFieldDirty` et vous `SetFieldNull` -même.

> [!NOTE]
> Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset :: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont mappées entre le type DAO_DATE dans DAO et le type [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) dans le jeu d’enregistrements.

> [!NOTE]
> `COleDateTime` remplace [ctime](../../atl-mfc-shared/reference/ctime-class.md) et TIMESTAMP_STRUCT à cet effet dans les classes DAO. `CTime` et TIMESTAMP_STRUCT sont toujours utilisés pour les classes d’accès aux données basées sur ODBC.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao. h

## <a name="dfx_double"></a><a name="dfx_double"></a> DFX_Double

Transfère les données de **type float double** entre les membres de données de champ d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Double(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   double& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de la classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type, provient du **`double`** membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Option qui vous permet de tirer parti du mécanisme de double mise en mémoire tampon de MFC pour la détection des champs du Recordset qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise la double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas ce champ. Vous devez appeler `SetFieldDirty` et vous `SetFieldNull` -même.

> [!NOTE]
> Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset :: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont mappées entre le type DAO_R8 dans DAO et le type **double float** dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao. h

## <a name="dfx_long"></a><a name="dfx_long"></a> DFX_Long

Transfère les données de type entier long entre les membres de données de champ d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Long(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   long& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de la classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type, provient du **`long`** membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Option qui vous permet de tirer parti du mécanisme de double mise en mémoire tampon de MFC pour la détection des champs du Recordset qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise la double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas ce champ. Vous devez appeler `SetFieldDirty` et vous `SetFieldNull` -même.

> [!NOTE]
> Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset :: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont mappées entre le type DAO_I4 dans DAO et **`long`** le type dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao. h

## <a name="dfx_longbinary"></a><a name="dfx_longbinary"></a> DFX_LongBinary

**Important** Nous vous recommandons d’utiliser [DFX_Binary](#dfx_binary) au lieu de cette fonction.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_LongBinary(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CLongBinary& value,
   DWORD dwPreAllocSize = AFX_DAO_LONGBINARY_DEFAULT_SIZE,
   DWORD dwBindOptions = 0);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de la classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type [CLongBinary](clongbinary-class.md), est extraite du membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

*dwPreAllocSize*<br/>
L’infrastructure Préalloue cette quantité de mémoire. Si vos données sont plus volumineuses, l’infrastructure allouera plus d’espace en fonction des besoins. Pour de meilleures performances, définissez cette taille sur une valeur suffisamment grande pour empêcher les réallocations.

*dwBindOptions*<br/>
Option qui vous permet de tirer parti du mécanisme de double mise en mémoire tampon de MFC pour la détection des champs du Recordset qui ont changé. La valeur par défaut, AFX_DISABLE_FIELD_CACHE, n’utilise pas la double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_ENABLE_FIELD_CACHE. Utilise la double mise en mémoire tampon, et il n’est pas nécessaire d’effectuer un travail supplémentaire pour marquer les champs comme modifiés ou null. Pour des raisons de performances et de mémoire, évitez cette valeur, sauf si vos données binaires sont relativement petites.

> [!NOTE]
> Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset :: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

`DFX_LongBinary` est fourni pour la compatibilité avec les classes ODBC MFC. La `DFX_LongBinary` fonction transfère les données BLOB (Binary Large Object) à l’aide de la classe `CLongBinary` entre les membres de données de champ d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données. Les données sont mappées entre le type DAO_BYTES dans DAO et le type [CLongBinary](clongbinary-class.md) dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao. h

## <a name="dfx_short"></a><a name="dfx_short"></a> DFX_Short

Transfère des données de type entier Short entre les membres de données de champ d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Short(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   short& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de la classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type, provient du **`short`** membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Option qui vous permet de tirer parti du mécanisme de double mise en mémoire tampon de MFC pour la détection des champs du Recordset qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise la double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas ce champ. Vous devez appeler `SetFieldDirty` et vous `SetFieldNull` -même.

> [!NOTE]
> Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset :: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont mappées entre le type DAO_I2 dans DAO et **`short`** le type dans le jeu d’enregistrements.

> [!NOTE]
> `DFX_Short` équivaut à [RFX_Int](#rfx_int) pour les classes basées sur ODBC.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao. h

## <a name="dfx_single"></a><a name="dfx_single"></a> DFX_Single

Transfère les données à virgule flottante entre les membres de données de champ d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Single(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   float& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de la classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur, de type, provient du **`float`** membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

*dwBindOptions*<br/>
Option qui vous permet de tirer parti du mécanisme de double mise en mémoire tampon de MFC pour la détection des champs du Recordset qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise la double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas ce champ. Vous devez appeler `SetFieldDirty` et vous `SetFieldNull` -même.

> [!NOTE]
> Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset :: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont mappées entre le type DAO_R4 dans DAO et **`float`** le type dans le jeu d’enregistrements.

### <a name="example"></a>Exemple

Consultez [DFX_Text](#dfx_text).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao. h

## <a name="dfx_text"></a><a name="dfx_text"></a> DFX_Text

Transfère des `CString` données entre les membres de données de champ d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Text(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   CString& value,
   int nPreAllocSize = AFX_DAO_TEXT_DEFAULT_SIZE,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*pFX*<br/>
Pointeur vers un objet de la classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName*<br/>
Nom d’une colonne de données.

*value*<br/>
Valeur stockée dans la donnée membre indiquée : valeur à transférer. Pour un transfert d’un jeu d’enregistrements à une source de données, la valeur de type [CString](../../atl-mfc-shared/reference/cstringt-class.md)est extraite du membre de données spécifié. Pour un transfert à partir de la source de données vers le Recordset, la valeur est stockée dans le membre de données spécifié.

*nPreAllocSize*<br/>
L’infrastructure Préalloue cette quantité de mémoire. Si vos données sont plus volumineuses, l’infrastructure allouera plus d’espace en fonction des besoins. Pour de meilleures performances, définissez cette taille sur une valeur suffisamment grande pour empêcher les réallocations.

*dwBindOptions*<br/>
Option qui vous permet de tirer parti du mécanisme de double mise en mémoire tampon de MFC pour la détection des champs du Recordset qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise la double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas ce champ. Vous devez appeler [SetFieldDirty](cdaorecordset-class.md#setfielddirty) et [SetFieldNull](cdaorecordset-class.md#setfieldnull) vous-même.

> [!NOTE]
> Vous pouvez contrôler si les données sont double mise en mémoire tampon par défaut en définissant [CDaoRecordset :: m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont mappées entre les DAO_CHAR de type dans DAO (ou, si le _UNICODE de symbole est défini, DAO_WCHAR) et le type [CString](../../atl-mfc-shared/reference/cstringt-class.md) dans le jeu d’enregistrements.  n

### <a name="example"></a>Exemple

Cet exemple illustre plusieurs appels à `DFX_Text` . Notez également les deux appels à [CDaoFieldExchange :: SetFieldType](cdaofieldexchange-class.md#setfieldtype). Vous devez écrire le premier appel à `SetFieldType` et son appel **DFX** . Le deuxième appel et ses appels **DFX** associés sont généralement écrits par l’Assistant code qui a généré la classe.

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

**En-tête :** afxdao. h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[CRecordset ::D oFieldExchange](crecordset-class.md#dofieldexchange)<br/>
[CRecordset ::D oBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)<br/>
[CDaoRecordset ::D oFieldExchange](cdaorecordset-class.md#dofieldexchange)
