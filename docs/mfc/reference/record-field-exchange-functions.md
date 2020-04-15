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
ms.openlocfilehash: bfd3ba64a33547b8a27e0f3bc896f39c94486464
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372979"
---
# <a name="record-field-exchange-functions"></a>Fonctions Record Field Exchange (RFX)

Cette rubrique répertorie les fonctions d’échange de champs d’enregistrements (RFX, RFX en bloc et DFX) permettant d’automatiser le transfert de données entre un objet recordset et sa source de données et d’effectuer d’autres opérations sur les données.

Si vous utilisez les classes ODBC et que vous avez implémenté l’extraction de lignes en bloc, vous devez remplacer manuellement la fonction membre `DoBulkFieldExchange` de `CRecordset` en appelant les fonctions RFX en bloc pour chaque membre de données correspondant à une colonne de source de données.

Si vous n’avez pas mis en œuvre la course en vrac dans les classes basées sur l’ODBC, ou si vous utilisez les classes basées sur DAO (obsolètes), alors ClassWizard remplacera la `DoFieldExchange` fonction membre de `CRecordset` ou `CDaoRecordset` en appelant les fonctions RFX (pour les classes ODBC) ou les fonctions DFX (pour les classes DAO) pour chaque membre des données sur le terrain dans votre dossier.

Les fonctions d’échange de champs d’enregistrements transfèrent des données chaque fois que l’infrastructure appelle `DoFieldExchange` ou `DoBulkFieldExchange`. Chaque fonction transfère un type de données spécifique.

Pour plus d’informations sur l’utilisation de ces fonctions, consultez les articles [Record Field Exchange : fonctionnement de RFX (ODBC)](../../data/odbc/record-field-exchange-how-rfx-works.md). Pour plus d’informations sur l’extraction de lignes en bloc, consultez l’article [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Pour les colonnes de données que vous liez dynamiquement, vous pouvez aussi appeler les fonctions RFX et DFX par vous-même, comme expliqué dans les articles [Recordset : liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). Par ailleurs, vous pouvez écrire vos propres routines RFX ou DFX personnalisées, comme l’explique la Note technique [43](../../mfc/tn043-rfx-routines.md) (pour ODBC) et la Note technique [53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) (pour DAO).

Par exemple, RFX et Bulk RFX fonctionnent `DoFieldExchange` au `DoBulkFieldExchange` fur et à mesure qu’ils apparaissent dans les fonctions et les fonctions, voir [RFX_Text](#rfx_text) et [RFX_Text_Bulk]#rfx_text_bulk). Les fonctions DFX sont très similaires aux fonctions RFX.

### <a name="rfx-functions-odbc"></a>Fonctions RFX (ODBC)

|||
|-|-|
|[RFX_Binary](#rfx_binary)|Transfère les tableaux d’octets de type [CByteArray](cbytearray-class.md).|
|[RFX_Bool](#rfx_bool)|Transfère les données de type Boolean.|
|[RFX_Byte](#rfx_byte)|Transfère un seul octet de données.|
|[RFX_Date](#rfx_date)|Transfère les données d’heure et de date à l’aide [de CTime](../../atl-mfc-shared/reference/ctime-class.md) ou de TIMESTAMP_STRUCT.|
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

## <a name="rfx_binary"></a><a name="rfx_binary"></a>RFX_Binary

Transfère des gammes d’octets `CRecordset` entre les membres des données sur le terrain d’un objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_BINARY, SQL_VARBINARY ou SQL_LONGVARBINARY.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Binary(
   CFieldExchange* pFX,
   const char* szName,
   CByteArray& value,
   int nMaxLength = 255);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations `CFieldExchange` sur les opérations, un objet peut spécifier, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, du type [CByteArray](cbytearray-class.md), est tirée du membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

*nMaxLength (en)*<br/>
La longueur maximale autorisée de la chaîne ou du tableau étant transférée. La valeur par défaut de *nMaxLength* est de 255. Les valeurs juridiques sont de 1 à INT_MAX. Le cadre alloue cette quantité d’espace pour les données. Pour obtenir de meilleures performances, passez une valeur suffisamment grande pour accueillir le plus grand élément de données que vous attendez.

### <a name="remarks"></a>Notes

Les données de la source de données de `CByteArray` ces types sont cartographiées à et à partir du type dans l’ensemble d’enregistrements.

### <a name="example"></a>Exemple

Voir [RFX_Text](#rfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_bool"></a><a name="rfx_bool"></a>RFX_Bool

Transfère les données Boolean `CRecordset` entre les membres des données sur le terrain d’un objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_BIT.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Bool(
   CFieldExchange* pFX,
   const char* szName,
   BOOL& value);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations `CFieldExchange` sur les opérations, un objet peut spécifier, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, de type BOOL, est prélevée sur le membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

### <a name="example"></a>Exemple

Voir [RFX_Text](#rfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_byte"></a><a name="rfx_byte"></a>RFX_Byte

Transfère des octets uniques `CRecordset` entre les membres des données de terrain d’un objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_TINYINT.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Byte(
   CFieldExchange* pFX,
   const char* szName,
   BYTE& value);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations `CFieldExchange` sur les opérations, un objet peut spécifier, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, de type BYTE, est prélevée sur le membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

### <a name="example"></a>Exemple

Voir [RFX_Text](#rfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_date"></a><a name="rfx_date"></a>RFX_Date

Transferts `CTime` ou TIMESTAMP_STRUCT données entre les membres `CRecordset` des données sur le terrain d’un objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_DATE, SQL_TIME ou SQL_TIMESTAMP.

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

*Pfx*<br/>
Un pointeur à un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations `CFieldExchange` sur les opérations, un objet peut spécifier, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée; la valeur à transférer. Les différentes versions de la fonction prennent différents types de données pour la valeur:

La première version de la fonction fait référence à un objet [CTime.](../../atl-mfc-shared/reference/ctime-class.md) Pour un transfert de l’ensemble de données à la source de données, cette valeur provient du membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

La deuxième version de la fonction `TIMESTAMP_STRUCT` fait référence à une structure. Vous devez mettre en place cette structure vous-même avant l’appel. Ni le support d’échange de données de dialogue (DDX) ni le support d’assistant de code n’est disponible pour cette version. La troisième version de la fonction fonctionne de la même manière que la première version, sauf qu’elle fait référence à un objet [COleDateTime.](../../atl-mfc-shared/reference/coledatetime-class.md)

### <a name="remarks"></a>Notes

La `CTime` version de la fonction impose les frais généraux d’un traitement intermédiaire et a une portée quelque peu limitée. Si vous trouvez l’un de ces facteurs trop limitant, utilisez la deuxième version de la fonction. Mais notez son manque de code assistant et de soutien DDX et l’exigence que vous configurez la structure vous-même.

### <a name="example"></a>Exemple

Voir [RFX_Text](#rfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_double"></a><a name="rfx_double"></a>RFX_Double

Transfère les données de double `CRecordset` **flotteur** entre les membres des données de terrain d’un objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_DOUBLE.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Double(
   CFieldExchange* pFX,
   const char* szName,
   double& value);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations `CFieldExchange` sur les opérations, un objet peut spécifier, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, du **type double,** est tirée du membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

### <a name="example"></a>Exemple

Voir [RFX_Text](#rfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_int"></a><a name="rfx_int"></a>RFX_Int

Transfère les données d’intégration entre les membres des données sur le terrain d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_SMALLINT.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations `CFieldExchange` sur les opérations, un objet peut spécifier, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, de type **int**, est prise à partir du membre de données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

### <a name="example"></a>Exemple

Voir [RFX_Text](#rfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_long"></a><a name="rfx_long"></a>RFX_Long

Transfère les données d’intégrer `CRecordset` entre les membres des données sur le terrain d’un objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_INTEGER.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Long(
   CFieldExchange* pFX,
   const char* szName,
   LONG&
value );
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations `CFieldExchange` sur les opérations, un objet peut spécifier, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, de type **long,** est prise à partir du membre de données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

### <a name="example"></a>Exemple

Voir [RFX_Text](#rfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_longbinary"></a><a name="rfx_longbinary"></a>RFX_LongBinary

Transfère les données binaires de gros objets (BLOB) `CRecordset` à l’aide de la classe [CLongBinary](clongbinary-class.md) entre les membres des données de terrain d’un objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_LONGVARBINARY ou SQL_LONGVARCHAR.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_LongBinary(
   CFieldExchange* pFX,
   const char* szName,
   CLongBinary& value);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations `CFieldExchange` sur les opérations, un objet peut spécifier, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données `CLongBinary`à la source de données, la valeur, du type, est tirée du membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

### <a name="example"></a>Exemple

Voir [RFX_Text](#rfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_single"></a><a name="rfx_single"></a>RFX_Single

Transfère les données flottantes entre `CRecordset` les membres des données sur le terrain d’un objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_REAL.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Single(
   CFieldExchange* pFX,
   const char* szName,
   float& value);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations `CFieldExchange` sur les opérations, un objet peut spécifier, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, du **flotteur**de type, est tirée du membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

### <a name="example"></a>Exemple

Voir [RFX_Text](#rfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_text"></a><a name="rfx_text"></a>RFX_Text

Transfère les `CString` données entre `CRecordset` les membres des données sur le terrain d’un objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL ou SQL_NUMERIC.

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

*Pfx*<br/>
Un pointeur à `CFieldExchange`un objet de classe . Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations `CFieldExchange` sur les opérations, un objet peut spécifier, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données `CString`à la source de données, la valeur, du type, est tirée du membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

*nMaxLength (en)*<br/>
La longueur maximale autorisée de la chaîne ou du tableau étant transférée. La valeur par défaut de *nMaxLength* est de 255. Les valeurs juridiques sont de 1 à INT_MAX). Le cadre alloue cette quantité d’espace pour les données. Pour obtenir de meilleures performances, passez une valeur suffisamment grande pour accueillir le plus grand élément de données que vous attendez.

*nColumnType (en)*<br/>
Utilisé principalement pour les paramètres. Un intégrant indiquant le type de données du paramètre. Le type est un type de données ODBC du formulaire **SQL_XXX**.

*nScale (en)*<br/>
Spécifie l’échelle pour les valeurs de type ODBC SQL_DECIMAL ou SQL_NUMERIC. *nScale n’est* utile que lors de la définition des valeurs de paramètres. For more information, see the topic "Precision, Scale, Length, and Display Size" in Appendix D of the *ODBC SDK Programmer's Reference*.

### <a name="remarks"></a>Notes

Les données de la source de données de `CString` tous ces types sont cartographiées à l’ensemble des enregistrements et à partir de celles-ci.

### <a name="example"></a>Exemple

Cet exemple montre `RFX_Text`plusieurs appels à . Avis aussi les `CFieldExchange::SetFieldType`deux appels à . Pour les paramètres, vous `SetFieldType` devez écrire l’appel et son appel RFX. L’appel de colonne de sortie et ses appels RFX associés sont normalement écrits par un magicien du code.

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

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_binary_bulk"></a><a name="rfx_binary_bulk"></a>RFX_Binary_Bulk

Transfère plusieurs rangées de données byte à partir d’une `CRecordset`colonne d’une source de données ODBC à un tableau correspondant dans un objet dérivé.

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

*Pfx*<br/>
Un pointeur à un objet [CFieldExchange.](cfieldexchange-class.md) Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*prgByteVals*<br/>
Un pointeur à un éventail de valeurs BYTE. Ce tableau stockera les données à transférer de la source de données à l’ensemble d’enregistrements.

*prgLengths*<br/>
Un pointeur à un tableau de longs entiers. Ce tableau stockera la longueur des octets de chaque valeur dans le tableau pointé par *prgByteVals*. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur nulle. Pour plus de détails, consultez la `SQLBindCol` fonction API ODBC dans la *référence du programmeur SDK ODBC*.

*nMaxLength (en)*<br/>
La longueur maximale autorisée des valeurs stockées dans le tableau pointé par *prgByteVals*. Pour vous assurer que les données ne seront pas tronquées, passez une valeur suffisamment grande pour accueillir l’élément de données le plus important que vous attendez.

### <a name="remarks"></a>Notes

La colonne de source de données peut avoir un type ODBC de SQL_BINARY, SQL_VARBINARY ou SQL_LONGVARBINARY. Le jeu d’enregistrement doit définir un membre des données de terrain de type pointeur à BYTE.

Si vous initialisez *prgByteVals* et *prgLengths* à NULL, alors les tableaux qu’ils pointent à seront attribués automatiquement, avec des tailles égales à la taille rowset.

> [!NOTE]
> L’échange de champs d’enregistrement en vrac ne transfère que les données de la source de données à l’objet de l’ensemble d’enregistrements. Afin de rendre votre dossier mis à jour, vous devez `SQLSetPos`utiliser la fonction API ODBC .

Pour plus d’informations, voir les articles [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Voir [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_bool_bulk"></a><a name="rfx_bool_bulk"></a>RFX_Bool_Bulk

Transfère plusieurs lignes de données Boolean à partir d’une colonne `CRecordset`d’une source de données ODBC à un tableau correspondant dans un objet dérivé.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Bool_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BOOL** prgBoolVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet [CFieldExchange.](cfieldexchange-class.md) Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*prgBoolVals*<br/>
Un pointeur à un tableau de valeurs BOOL. Ce tableau stockera les données à transférer de la source de données à l’ensemble d’enregistrements.

*prgLengths*<br/>
Un pointeur à un tableau de longs entiers. Ce tableau stockera la longueur des octets de chaque valeur dans le tableau pointé par *prgBoolVals*. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur nulle. Pour plus de détails, consultez la `SQLBindCol` fonction API ODBC dans la *référence du programmeur SDK ODBC*.

### <a name="remarks"></a>Notes

La colonne de source de données doit avoir un type ODBC de SQL_BIT. Le jeu d’enregistrement doit définir un membre des données de terrain de type pointeur à BOOL.

Si vous initialisez *prgBoolVals* et *prgLengths* à NULL, alors les tableaux qu’ils pointent à seront attribués automatiquement, avec des tailles égales à la taille rowset.

> [!NOTE]
> L’échange de champs d’enregistrement en vrac ne transfère que les données de la source de données à l’objet de l’ensemble d’enregistrements. Pour rendre votre dossier mis à jour, vous devez `SQLSetPos`utiliser la fonction API ODBC .

Pour plus d’informations, voir les articles [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Voir [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_byte_bulk"></a><a name="rfx_byte_bulk"></a>RFX_Byte_Bulk

Transfère plusieurs rangées d’octets uniques à partir d’une `CRecordset`colonne d’une source de données ODBC à un tableau correspondant dans un objet dérivé.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Byte_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   BYTE** prgByteVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet [CFieldExchange.](cfieldexchange-class.md) Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*prgByteVals*<br/>
Un pointeur à un éventail de valeurs BYTE. Ce tableau stockera les données à transférer de la source de données à l’ensemble d’enregistrements.

*prgLengths*<br/>
Un pointeur à un tableau de longs entiers. Ce tableau stockera la longueur des octets de chaque valeur dans le tableau pointé par *prgByteVals*. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur nulle. Pour plus de détails, consultez la `SQLBindCol` fonction API ODBC dans la *référence du programmeur SDK ODBC*.

### <a name="remarks"></a>Notes

La colonne de source de données doit avoir un type ODBC de SQL_TINYINT. Le jeu d’enregistrement doit définir un membre des données de terrain de type pointeur à BYTE.

Si vous initialisez *prgByteVals* et *prgLengths* à NULL, alors les tableaux qu’ils pointent à seront attribués automatiquement, avec des tailles égales à la taille rowset.

> [!NOTE]
> L’échange de champs d’enregistrement en vrac ne transfère que les données de la source de données à l’objet de l’ensemble d’enregistrements. Pour rendre votre dossier mis à jour, vous devez `SQLSetPos`utiliser la fonction API ODBC .

Pour plus d’informations, voir les articles [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Voir [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_date_bulk"></a><a name="rfx_date_bulk"></a>RFX_Date_Bulk

Transfère plusieurs rangées de données TIMESTAMP_STRUCT à partir d’une colonne d’une source de données ODBC à un tableau correspondant dans un `CRecordset`objet dérivé.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Date_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   TIMESTAMP_STRUCT** prgTSVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet [CFieldExchange.](cfieldexchange-class.md) Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*prgTSVals*<br/>
Un pointeur à un éventail de valeurs TIMESTAMP_STRUCT. Ce tableau stockera les données à transférer de la source de données à l’ensemble d’enregistrements. Pour plus d’informations sur le type de données TIMESTAMP_STRUCT, voir le thème "C Data Types" à l’Annexe D de la *référence du programmeur SDK D D.*

*prgLengths*<br/>
Un pointeur à un tableau de longs entiers. Ce tableau stockera la longueur des octets de chaque valeur dans le tableau pointé par *prgTSVals*. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur nulle. Pour plus de détails, consultez la `SQLBindCol` fonction API ODBC dans la *référence du programmeur SDK ODBC*.

### <a name="remarks"></a>Notes

La colonne de source de données peut avoir un type ODBC de SQL_DATE, SQL_TIME, ou SQL_TIMESTAMP. Le jeu d’enregistrement doit définir un membre des données sur le terrain de type pointeur pour TIMESTAMP_STRUCT.

Si vous initialisez *prgTSVals* et *prgLengths* à NULL, alors les tableaux qu’ils pointent à seront attribués automatiquement, avec des tailles égales à la taille de rowset.

> [!NOTE]
> L’échange de champs d’enregistrement en vrac ne transfère que les données de la source de données à l’objet de l’ensemble d’enregistrements. Pour rendre votre dossier mis à jour, vous devez `SQLSetPos`utiliser la fonction API ODBC .

Pour plus d’informations, voir les articles [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Voir [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_double_bulk"></a><a name="rfx_double_bulk"></a>RFX_Double_Bulk

Transfère plusieurs lignes de données à double précision à point flottant à partir d’une colonne d’une source de données ODBC à un tableau correspondant dans un `CRecordset`objet dérivé.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Double_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   double** prgDblVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet [CFieldExchange.](cfieldexchange-class.md) Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*prgDblVals*<br/>
Un pointeur à un tableau de **valeurs doubles.** Ce tableau stockera les données à transférer de la source de données à l’ensemble d’enregistrements.

*prgLengths*<br/>
Un pointeur à un tableau de longs entiers. Ce tableau stockera la longueur des octets de chaque valeur dans le tableau pointé par *prgDblVals*. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur nulle. Pour plus de détails, consultez la `SQLBindCol` fonction API ODBC dans la *référence du programmeur SDK ODBC*.

### <a name="remarks"></a>Notes

La colonne de source de données doit avoir un type ODBC de SQL_DOUBLE. Le jeu d’enregistrement doit définir un membre des données de terrain de type pointeur pour **doubler**.

Si vous initialisez *prgDblVals* et *prgLengths* à NULL, alors les tableaux qu’ils pointent à seront attribués automatiquement, avec des tailles égales à la taille rowset.

> [!NOTE]
> L’échange de champs d’enregistrement en vrac ne transfère que les données de la source de données à l’objet de l’ensemble d’enregistrements. Pour rendre votre dossier mis à jour, vous devez `SQLSetPos`utiliser la fonction API ODBC .

Pour plus d’informations, voir les articles [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Voir [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_int_bulk"></a><a name="rfx_int_bulk"></a>RFX_Int_Bulk

Transfère les données d’intégration entre les membres des données sur le terrain d’un `CRecordset` objet et les colonnes d’un enregistrement sur la source de données de type ODBC SQL_SMALLINT.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Int(
   CFieldExchange* pFX,
   const char* szName,
   int& value);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CFieldExchange](cfieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations `CFieldExchange` sur les opérations, un objet peut spécifier, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, de type **int**, est prise à partir du membre de données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

### <a name="example"></a>Exemple

Voir [RFX_Text](#rfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_long_bulk"></a><a name="rfx_long_bulk"></a>RFX_Long_Bulk

Transfère plusieurs rangées de données d’intégrage long à partir d’une colonne d’une source de données ODBC à un tableau correspondant dans un `CRecordset`objet dérivé.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Long_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   long** prgLongVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet [CFieldExchange.](cfieldexchange-class.md) Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*prgLongVals*<br/>
Un pointeur à un tableau de longs entiers. Ce tableau stockera les données à transférer de la source de données à l’ensemble d’enregistrements.

*prgLengths*<br/>
Un pointeur à un tableau de longs entiers. Ce tableau stockera la longueur des octets de chaque valeur dans le tableau pointé par *prgLongVals*. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur nulle. Pour plus de détails, consultez la `SQLBindCol` fonction API ODBC dans la *référence du programmeur SDK ODBC*.

### <a name="remarks"></a>Notes

La colonne de source de données doit avoir un type ODBC de SQL_INTEGER. Le jeu d’enregistrement doit définir un membre des données de terrain de type pointeur à **long**.

Si vous initialisez *prgLongVals* et *prgLengths* à NULL, alors les tableaux qu’ils pointent à seront attribués automatiquement, avec des tailles égales à la taille de rowset.

> [!NOTE]
> L’échange de champs d’enregistrement en vrac ne transfère que les données de la source de données à l’objet de l’ensemble d’enregistrements. Pour rendre votre dossier mis à jour, vous devez `SQLSetPos`utiliser la fonction API ODBC .

Pour plus d’informations, voir les articles [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Voir [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_single_bulk"></a><a name="rfx_single_bulk"></a>RFX_Single_Bulk

Transfère plusieurs rangées de données à point flottant à partir d’une colonne d’une source de données ODBC à un tableau correspondant dans un `CRecordset`objet dérivé.

### <a name="syntax"></a>Syntaxe

```cpp
void RFX_Single_Bulk(
   CFieldExchange* pFX,
   LPCTSTR szName,
   float** prgFltVals,
   long** prgLengths);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet [CFieldExchange.](cfieldexchange-class.md) Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*prgFltVals*<br/>
Un pointeur à un tableau de valeurs **de flotteur.** Ce tableau stockera les données à transférer de la source de données à l’ensemble d’enregistrements.

*prgLengths*<br/>
Un pointeur à un tableau de longs entiers. Ce tableau stockera la longueur des octets de chaque valeur dans le tableau pointé par *prgFltVals*. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur nulle. Pour plus de détails, consultez la `SQLBindCol` fonction API ODBC dans la *référence du programmeur SDK ODBC*.

### <a name="remarks"></a>Notes

La colonne de source de données doit avoir un type ODBC de SQL_REAL. Le jeu d’enregistrement doit définir un membre des données de terrain de type pointeur pour **flotter**.

Si vous initialisez *prgFltVals* et *prgLengths* à NULL, alors les tableaux qu’ils pointent à seront attribués automatiquement, avec des tailles égales à la taille rowset.

> [!NOTE]
> L’échange de champs d’enregistrement en vrac ne transfère que les données de la source de données à l’objet de l’ensemble d’enregistrements. Pour rendre votre dossier mis à jour, vous devez `SQLSetPos`utiliser la fonction API ODBC .

Pour plus d’informations, voir les articles [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Voir [RFX_Text_Bulk](#rfx_text_bulk).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="rfx_text_bulk"></a><a name="rfx_text_bulk"></a>RFX_Text_Bulk

Transfère plusieurs lignes de données de caractères à partir d’une colonne d’une source de données ODBC à un tableau correspondant dans un `CRecordset`objet dérivé.

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

*Pfx*<br/>
Un pointeur à un objet [CFieldExchange.](cfieldexchange-class.md) Cet objet contient des informations pour définir le contexte de chaque appel de la fonction. Pour plus d’informations, voir l’article [Record Field Exchange: How RFX Works](../../data/odbc/record-field-exchange-how-rfx-works.md).

*szName (szName)*<br/>
Le nom d’une colonne de données.

*prgStrVals*<br/>
Un pointeur à un éventail de valeurs LPSTR. Ce tableau stockera les données à transférer de la source de données à l’ensemble d’enregistrements. Notez qu’avec la version actuelle d’ODBC, ces valeurs ne peuvent pas être Unicode.

*prgLengths*<br/>
Un pointeur à un tableau de longs entiers. Ce tableau stockera la longueur des octets de chaque valeur dans le tableau pointé par *prgStrVals*. Cette longueur exclut le caractère de résiliation nulle. Notez que la valeur SQL_NULL_DATA sera stockée si l’élément de données correspondant contient une valeur nulle. Pour plus de détails, consultez la `SQLBindCol` fonction API ODBC dans la *référence du programmeur SDK ODBC*.

*nMaxLength (en)*<br/>
La longueur maximale autorisée des valeurs stockées dans le tableau pointé par *prgStrVals*, y compris le caractère de terminaison nulle. Pour vous assurer que les données ne seront pas tronquées, passez une valeur suffisamment grande pour accueillir l’élément de données le plus important que vous attendez.

### <a name="remarks"></a>Notes

La colonne de source de données peut avoir un type ODBC de SQL_LONGVARCHAR, SQL_CHAR, SQL_VARCHAR, SQL_DECIMAL ou SQL_NUMERIC. Le jeu d’enregistrement doit définir un membre des données sur le terrain de type LPSTR.

Si vous initialisez *prgStrVals* et *prgLengths* à NULL, alors les tableaux qu’ils pointent à seront attribués automatiquement, avec des tailles égales à la taille de rowset.

> [!NOTE]
> L’échange de champs d’enregistrement en vrac ne transfère que les données de la source de données à l’objet de l’ensemble d’enregistrements. Pour rendre votre dossier mis à jour, vous devez `SQLSetPos`utiliser la fonction API ODBC .

Pour plus d’informations, voir les articles [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md) et [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

### <a name="example"></a>Exemple

Vous devez écrire manuellement `DoBulkFieldExchange` des appels dans votre remplacement. Cet exemple montre `RFX_Text_Bulk`un appel à , `RFX_Long_Bulk`ainsi qu’un appel à , pour le transfert de données. Ces appels sont précédés d’un appel à [CFieldExchange:SetFieldType](cfieldexchange-class.md#setfieldtype). Notez que pour les paramètres, vous devez appeler les fonctions RFX au lieu des fonctions RFX en vrac.

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

### <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="dfx_binary"></a><a name="dfx_binary"></a>DFX_Binary

Transfère des gammes d’octets entre les membres des données de terrain d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

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

*Pfx*<br/>
Un pointeur à un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, du type [CByteArray](cbytearray-class.md), est tirée du membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

*nPreAllocSize*<br/>
Le cadre prélocalise cette quantité de mémoire. Si vos données sont plus grandes, le cadre vous permettra d’allouer plus d’espace au besoin. Pour de meilleures performances, définissez cette taille à une valeur suffisamment grande pour éviter les réaffectations. La taille par défaut est définie dans l’AFXDAO. H fichier comme AFX_DAO_BINARY_DEFAULT_SIZE.

*dwBindOptions*<br/>
Une option qui vous permet de profiter du mécanisme de double tampon de MFC pour détecter les champs de records qui ont changé. La valeur par défaut, AFX_DAO_DISABLE_FIELD_CACHE, n’utilise pas de double tampon, et vous devez appeler [SetFieldDirty](cdaorecordset-class.md#setfielddirty) et [SetFieldNull](cdaorecordset-class.md#setfieldnull) vous-même. L’autre valeur possible, AFX_DAO_ENABLE_FIELD_CACHE, utilise double tampon, et vous n’avez pas à faire un travail supplémentaire pour marquer les champs sales ou null. Pour des raisons de performance et de mémoire, évitez cette valeur à moins que vos données binaires ne soient relativement petites.

> [!NOTE]
> Vous pouvez contrôler si les données sont doubles tamponnées pour tous les champs par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont cartographiées entre le type DAO_BYTES dans DAO et le type [CByteArray](cbytearray-class.md) dans le jeu d’enregistrement.

### <a name="example"></a>Exemple

Voir [DFX_Text](#dfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="dfx_bool"></a><a name="dfx_bool"></a>DFX_Bool

Transfère les données Boolean entre les membres des données sur le terrain d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Bool(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BOOL& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, de type BOOL, est prélevée sur le membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

*dwBindOptions*<br/>
Une option qui vous permet de profiter du mécanisme de double tampon de MFC pour détecter les champs de records qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise une double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas sur ce champ. Tu dois `SetFieldDirty` `SetFieldNull` appeler et toi-même.

> [!NOTE]
> Vous pouvez contrôler si les données sont doublement tamponnées par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont cartographiées entre le type DAO_BOOL dans DAO et le type BOOL dans le jeu d’enregistrement.

### <a name="example"></a>Exemple

Voir [DFX_Text](#dfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="dfx_byte"></a><a name="dfx_byte"></a>DFX_Byte

Transfère des octets uniques entre les membres des données de terrain d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Byte(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   BYTE& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, de type BYTE, est prélevée sur le membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

*dwBindOptions*<br/>
Une option qui vous permet de profiter du mécanisme de double tampon de MFC pour détecter les champs de records qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise une double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas sur ce champ. Tu dois `SetFieldDirty` `SetFieldNull` appeler et toi-même.

> [!NOTE]
> Vous pouvez contrôler si les données sont doublement tamponnées par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont cartographiées entre le type DAO_BYTES dans DAO et le type BYTE dans le jeu d’enregistrement.

### <a name="example"></a>Exemple

Voir [DFX_Text](#dfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="dfx_currency"></a><a name="dfx_currency"></a>DFX_Currency

Transfère les données de change entre les membres des données sur le terrain d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Currency(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleCurrency& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, cette valeur provient du membre des données spécifié, du type [COleCurrency](colecurrency-class.md). Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

*dwBindOptions*<br/>
Une option qui vous permet de profiter du mécanisme de double tampon de MFC pour détecter les champs de records qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise une double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas sur ce champ. Tu dois `SetFieldDirty` `SetFieldNull` appeler et toi-même.

> [!NOTE]
> Vous pouvez contrôler si les données sont doublement tamponnées par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont cartographiées entre le type DAO_CURRENCY dans DAO et le type [COleCurrency](colecurrency-class.md) dans le jeu d’enregistrement.

### <a name="example"></a>Exemple

Voir [DFX_Text](#dfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="dfx_datetime"></a><a name="dfx_datetime"></a>DFX_DateTime

Transfère les données d’heure et de date entre les membres des données sur le terrain d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_DateTime(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   COleDateTime& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. La fonction fait référence à un objet [COleDateTime.](../../atl-mfc-shared/reference/coledatetime-class.md) Pour un transfert de l’ensemble de données à la source de données, cette valeur provient du membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

*dwBindOptions*<br/>
Une option qui vous permet de profiter du mécanisme de double tampon de MFC pour détecter les champs de records qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise une double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas sur ce champ. Tu dois `SetFieldDirty` `SetFieldNull` appeler et toi-même.

> [!NOTE]
> Vous pouvez contrôler si les données sont doublement tamponnées par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont cartographiées entre le type DAO_DATE dans DAO et le type [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) dans le jeu d’enregistrement.

> [!NOTE]
> `COleDateTime`remplace [CTime](../../atl-mfc-shared/reference/ctime-class.md) et TIMESTAMP_STRUCT à cet effet dans les classes DAO. `CTime`et TIMESTAMP_STRUCT sont toujours utilisés pour les classes d’accès aux données basées sur l’ODBC.

### <a name="example"></a>Exemple

Voir [DFX_Text](#dfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="dfx_double"></a><a name="dfx_double"></a>DFX_Double

Transfère les données **de double flotteur** entre les membres des données de terrain d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Double(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   double& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, du **type double,** est tirée du membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

*dwBindOptions*<br/>
Une option qui vous permet de profiter du mécanisme de double tampon de MFC pour détecter les champs de records qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise une double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas sur ce champ. Tu dois `SetFieldDirty` `SetFieldNull` appeler et toi-même.

> [!NOTE]
> Vous pouvez contrôler si les données sont doublement tamponnées par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont cartographiées entre le type DAO_R8 dans DAO et le **double flotteur** de type dans l’enregistrement.

### <a name="example"></a>Exemple

Voir [DFX_Text](#dfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="dfx_long"></a><a name="dfx_long"></a>DFX_Long

Transfère les données d’un long intégrage entre les membres des données sur le terrain d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Long(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   long& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, de type **long,** est prise à partir du membre de données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

*dwBindOptions*<br/>
Une option qui vous permet de profiter du mécanisme de double tampon de MFC pour détecter les champs de records qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise une double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas sur ce champ. Tu dois `SetFieldDirty` `SetFieldNull` appeler et toi-même.

> [!NOTE]
> Vous pouvez contrôler si les données sont doublement tamponnées par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont cartographiées entre le type DAO_I4 dans DAO et le type **long** dans l’enregistrement.

### <a name="example"></a>Exemple

Voir [DFX_Text](#dfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="dfx_longbinary"></a><a name="dfx_longbinary"></a>DFX_LongBinary

**Important** Il est recommandé d’utiliser [DFX_Binary](#dfx_binary) au lieu de cette fonction.

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

*Pfx*<br/>
Un pointeur à un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, du type [CLongBinary](clongbinary-class.md), est tirée du membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

*dwPreAllocSize*<br/>
Le cadre prélocalise cette quantité de mémoire. Si vos données sont plus grandes, le cadre vous permettra d’allouer plus d’espace au besoin. Pour de meilleures performances, définissez cette taille à une valeur suffisamment grande pour éviter les réaffectations.

*dwBindOptions*<br/>
Une option qui vous permet de profiter du mécanisme de double tampon de MFC pour détecter les champs de records qui ont changé. La valeur par défaut, AFX_DISABLE_FIELD_CACHE, n’utilise pas la double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_ENABLE_FIELD_CACHE. Utilise double tampon, et vous n’avez pas à faire un travail supplémentaire pour marquer les champs sales ou Null. Pour des raisons de performance et de mémoire, évitez cette valeur à moins que vos données binaires ne soient relativement petites.

> [!NOTE]
> Vous pouvez contrôler si les données sont doublement tamponnées par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

`DFX_LongBinary`est prévu pour la compatibilité avec les classes MFC ODBC. La `DFX_LongBinary` fonction transfère les données binaires `CLongBinary` à gros objectif (BLOB) en utilisant la classe entre les membres des données de terrain d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données. Les données sont cartographiées entre le type DAO_BYTES dans DAO et le type [CLongBinary](clongbinary-class.md) dans le jeu d’enregistrement.

### <a name="example"></a>Exemple

Voir [DFX_Text](#dfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="dfx_short"></a><a name="dfx_short"></a>DFX_Short

Transfère de courtes données integer entre les membres des données de terrain d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Short(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   short& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, de type **court,** est prise à partir du membre de données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

*dwBindOptions*<br/>
Une option qui vous permet de profiter du mécanisme de double tampon de MFC pour détecter les champs de records qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise une double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas sur ce champ. Tu dois `SetFieldDirty` `SetFieldNull` appeler et toi-même.

> [!NOTE]
> Vous pouvez contrôler si les données sont doublement tamponnées par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont cartographiées entre le type DAO_I2 dans DAO et le **type court** dans l’enregistrement.

> [!NOTE]
> `DFX_Short`équivaut à [RFX_Int](#rfx_int) pour les classes basées sur l’ODBC.

### <a name="example"></a>Exemple

Voir [DFX_Text](#dfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="dfx_single"></a><a name="dfx_single"></a>DFX_Single

Transfère les données flottantes entre les membres des données de terrain d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI DFX_Single(
   CDaoFieldExchange* pFX,
   LPCTSTR szName,
   float& value,
   DWORD dwBindOptions = AFX_DAO_ENABLE_FIELD_CACHE);
```

### <a name="parameters"></a>Paramètres

*Pfx*<br/>
Un pointeur à un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, du **flotteur**de type, est tirée du membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

*dwBindOptions*<br/>
Une option qui vous permet de profiter du mécanisme de double tampon de MFC pour détecter les champs de records qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise une double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas sur ce champ. Tu dois `SetFieldDirty` `SetFieldNull` appeler et toi-même.

> [!NOTE]
> Vous pouvez contrôler si les données sont doublement tamponnées par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont cartographiées entre le type DAO_R4 dans DAO et le **flotteur** de type dans l’enregistrement.

### <a name="example"></a>Exemple

Voir [DFX_Text](#dfx_text).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="dfx_text"></a><a name="dfx_text"></a>DFX_Text

Transfère les `CString` données entre les membres des données sur le terrain d’un objet [CDaoRecordset](cdaorecordset-class.md) et les colonnes d’un enregistrement sur la source de données.

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

*Pfx*<br/>
Un pointeur à un objet de classe [CDaoFieldExchange](cdaofieldexchange-class.md). Cet objet contient des informations pour définir le contexte de chaque appel de la fonction.

*szName (szName)*<br/>
Le nom d’une colonne de données.

*value*<br/>
La valeur stockée dans le membre des données indiquée — la valeur à transférer. Pour un transfert de l’ensemble de données à la source de données, la valeur, du type [CString](../../atl-mfc-shared/reference/cstringt-class.md), est tirée du membre des données spécifié. Pour un transfert de source de données à l’enregistrement, la valeur est stockée dans le membre des données spécifiés.

*nPreAllocSize*<br/>
Le cadre prélocalise cette quantité de mémoire. Si vos données sont plus grandes, le cadre vous permettra d’allouer plus d’espace au besoin. Pour de meilleures performances, définissez cette taille à une valeur suffisamment grande pour éviter les réaffectations.

*dwBindOptions*<br/>
Une option qui vous permet de profiter du mécanisme de double tampon de MFC pour détecter les champs de records qui ont changé. La valeur par défaut, AFX_DAO_ENABLE_FIELD_CACHE, utilise une double mise en mémoire tampon. L’autre valeur possible est AFX_DAO_DISABLE_FIELD_CACHE. Si vous spécifiez cette valeur, MFC ne vérifie pas sur ce champ. Vous devez appeler [SetFieldDirty](cdaorecordset-class.md#setfielddirty) et [SetFieldNull](cdaorecordset-class.md#setfieldnull) vous-même.

> [!NOTE]
> Vous pouvez contrôler si les données sont doublement tamponnées par défaut en définissant [CDaoRecordset::m_bCheckCacheForDirtyFields](cdaorecordset-class.md#m_bcheckcachefordirtyfields).

### <a name="remarks"></a>Notes

Les données sont cartographiées entre le type DAO_CHAR dans DAO (ou, si le symbole _UNICODE est défini, DAO_WCHAR) et le type [CString](../../atl-mfc-shared/reference/cstringt-class.md) dans le jeu d’enregistrement.  n

### <a name="example"></a>Exemple

Cet exemple montre `DFX_Text`plusieurs appels à . Avis également les deux appels à [CDaoFieldExchange:SetFieldType](cdaofieldexchange-class.md#setfieldtype). Vous devez écrire le `SetFieldType` premier appel et son appel **DFX.** Le deuxième appel et ses appels **DFX** associés sont normalement écrits par l’assistant de code qui a généré la classe.

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

### <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[CRecordset::DoFieldExchange](crecordset-class.md#dofieldexchange)<br/>
[CRecordset::DoBulkFieldExchange](crecordset-class.md#dobulkfieldexchange)<br/>
[CDaoRecordset::DoFieldExchange](cdaorecordset-class.md#dofieldexchange)
