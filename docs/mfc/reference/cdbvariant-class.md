---
description: 'En savoir plus sur : classe CDBVariant'
title: CDBVariant, classe
ms.date: 11/04/2016
f1_keywords:
- CDBVariant
- AFXDB/CDBVariant
- AFXDB/CDBVariant::CDBVariant
- AFXDB/CDBVariant::Clear
- AFXDB/CDBVariant::m_dwType
- AFXDB/CDBVariant::m_boolVal
- AFXDB/CDBVariant::m_chVal
- AFXDB/CDBVariant::m_dblVal
- AFXDB/CDBVariant::m_fltVal
- AFXDB/CDBVariant::m_iVal
- AFXDB/CDBVariant::m_lVal
- AFXDB/CDBVariant::m_pbinary
- AFXDB/CDBVariant::m_pdate
- AFXDB/CDBVariant::m_pstring
- AFXDB/CDBVariant::m_pstringA
- AFXDB/CDBVariant::m_pstringW
helpviewer_keywords:
- CDBVariant [MFC], CDBVariant
- CDBVariant [MFC], Clear
- CDBVariant [MFC], m_dwType
- CDBVariant [MFC], m_boolVal
- CDBVariant [MFC], m_chVal
- CDBVariant [MFC], m_dblVal
- CDBVariant [MFC], m_fltVal
- CDBVariant [MFC], m_iVal
- CDBVariant [MFC], m_lVal
- CDBVariant [MFC], m_pbinary
- CDBVariant [MFC], m_pdate
- CDBVariant [MFC], m_pstring
- CDBVariant [MFC], m_pstringA
- CDBVariant [MFC], m_pstringW
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
ms.openlocfilehash: 54fc432998a15d79ab51165b280e4cc4ced94455
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247940"
---
# <a name="cdbvariant-class"></a>CDBVariant, classe

Représente un type de données variant pour les classes ODBC MFC.

## <a name="syntax"></a>Syntaxe

```
class CDBVariant
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDBVariant::CDBVariant](#cdbvariant)|Construit un objet `CDBVariant`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDBVariant :: Clear](#clear)|Efface l' `CDBVariant` objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDBVariant :: m_dwType](#m_dwtype)|Contient le type de données de la valeur actuellement stockée. Tapez `DWORD`.|

### <a name="public-union-members"></a>Membres de l’Union publique

|Nom|Description|
|----------|-----------------|
|[CDBVariant :: m_boolVal](#m_boolval)|Contient une valeur de type **bool**.|
|[CDBVariant :: m_chVal](#m_chval)|Contient une valeur de type **`unsigned char`** .|
|[CDBVariant :: m_dblVal](#m_dblval)|Contient une valeur de type **`double`** .|
|[CDBVariant :: m_fltVal](#m_fltval)|Contient une valeur de type **`float`** .|
|[CDBVariant :: m_iVal](#m_ival)|Contient une valeur de type **`short`** .|
|[CDBVariant :: m_lVal](#m_lval)|Contient une valeur de type **`long`** .|
|[CDBVariant :: m_pbinary](#m_pbinary)|Contient un pointeur vers un objet de type `CLongBinary` .|
|[CDBVariant :: m_pdate](#m_pdate)|Contient un pointeur vers un objet de type **TIMESTAMP_STRUCT**.|
|[CDBVariant :: m_pstring](#m_pstring)|Contient un pointeur vers un objet de type `CString` .|
|[CDBVariant :: m_pstringA](#m_pstringa)|Stocke un pointeur vers un objet [CSTRING](../../atl-mfc-shared/reference/cstringt-class.md) ASCII.|
|[CDBVariant :: m_pstringW](#m_pstringw)|Stocke un pointeur vers un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) étendu.|

## <a name="remarks"></a>Notes

`CDBVariant` n’a pas de classe de base.

`CDBVariant` est semblable à [COleVariant](../../mfc/reference/colevariant-class.md); Toutefois, `CDBVariant` n’utilise pas OLE. `CDBVariant` vous permet de stocker une valeur sans vous préoccuper du type de données de la valeur. `CDBVariant` effectue le suivi du type de données de la valeur actuelle, qui est stockée dans une Union.

La classe [CRecordset](../../mfc/reference/crecordset-class.md) utilise `CDBVariant` des objets dans trois fonctions membres : `GetFieldValue` , `GetBookmark` et `SetBookmark` . Par exemple, `GetFieldValue` vous permet d’extraire dynamiquement des données dans une colonne. Étant donné que le type de données de la colonne peut ne pas être connu au moment de l’exécution, `GetFieldValue` utilise un `CDBVariant` objet pour stocker les données de la colonne.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CDBVariant`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXDB. h

## <a name="cdbvariantcdbvariant"></a><a name="cdbvariant"></a> CDBVariant::CDBVariant

Crée un `CDBVariant` objet null.

```
CDBVariant();
```

### <a name="remarks"></a>Notes

Définit le membre de données [m_dwType](#m_dwtype) sur DBVT_NULL.

## <a name="cdbvariantclear"></a><a name="clear"></a> CDBVariant :: Clear

Appelez cette fonction membre pour effacer l' `CDBVariant` objet.

```cpp
void Clear();
```

### <a name="remarks"></a>Notes

Si la valeur du membre de données [m_dwType](#m_dwtype) est DBVT_DATE, DBVT_STRING ou DBVT_BINARY, `Clear` libère la mémoire associée au membre du pointeur d’Union. `Clear` définit `m_dwType` sur DBVT_NULL.

Le `CDBVariant` destructeur appelle `Clear` .

## <a name="cdbvariantm_boolval"></a><a name="m_boolval"></a> CDBVariant :: m_boolVal

Stocke une valeur de type BOOL.

### <a name="remarks"></a>Notes

Le `m_boolVal` membre de données appartient à une Union. Avant d’accéder à `m_boolVal` , vérifiez d’abord la valeur de [CDBVariant :: m_dwType](#m_dwtype). Si `m_dwType` a `m_boolVal` la valeur DBVT_BOOL, contiendra une valeur valide ; sinon, l’accès à `m_boolVal` produira des résultats non fiables.

## <a name="cdbvariantm_chval"></a><a name="m_chval"></a> CDBVariant :: m_chVal

Stocke une valeur de type **`unsigned char`** .

### <a name="remarks"></a>Notes

Le `m_chVal` membre de données appartient à une Union. Avant d’accéder à `m_chVal` , vérifiez d’abord la valeur de [CDBVariant :: m_dwType](#m_dwtype). Si `m_dwType` a `m_chVal` la valeur DBVT_UCHAR, contient une valeur valide ; sinon, l’accès à `m_chVal` produira des résultats non fiables.

## <a name="cdbvariantm_dblval"></a><a name="m_dblval"></a> CDBVariant :: m_dblVal

Stocke une valeur de type **`double`** .

### <a name="remarks"></a>Notes

Le `m_dblVal` membre de données appartient à une Union. Avant d’accéder à `m_dblVal` , vérifiez d’abord la valeur de [CDBVariant :: m_dwType](#m_dwtype). Si `m_dwType` a `m_dblVal` la valeur DBVT_DOUBLE, contient une valeur valide ; sinon, l’accès à `m_dblVal` produira des résultats non fiables.

## <a name="cdbvariantm_dwtype"></a><a name="m_dwtype"></a> CDBVariant :: m_dwType

Ce membre de données contient le type de données pour la valeur actuellement stockée dans le `CDBVariant` membre de données d’Union de l’objet.

### <a name="remarks"></a>Notes

Avant d’accéder à cette Union, vous devez vérifier la valeur de afin de `m_dwType` déterminer le membre de données d’Union auquel accéder. Le tableau suivant répertorie les valeurs possibles pour `m_dwType` et le membre de données d’Union correspondant.

|m_dwType|Membre de données d’Union|
|---------------|-----------------------|
|DBVT_NULL|Aucun membre d’Union n’est valide pour l’accès.|
|DBVT_BOOL|[m_boolVal](#m_boolval)|
|DBVT_UCHAR|[m_chVal](#m_chval)|
|DBVT_SHORT|[m_iVal](#m_ival)|
|DBVT_LONG|[m_lVal](#m_lval)|
|DBVT_SINGLE|[m_fltVal](#m_fltval)|
|DBVT_DOUBLE|[m_dblVal](#m_dblval)|
|DBVT_DATE|[m_pdate](#m_pdate)|
|DBVT_STRING|[m_pstring](#m_pstring)|
|DBVT_BINARY|[m_pbinary](#m_pbinary)|
|DBVT_ASTRING|[m_pstringA](#m_pstringa)|
|DBVT_WSTRING|[m_pstringW](#m_pstringw)|

## <a name="cdbvariantm_fltval"></a><a name="m_fltval"></a> CDBVariant :: m_fltVal

Stocke une valeur de type **`float`** .

### <a name="remarks"></a>Notes

Le `m_fltVal` membre de données appartient à une Union. Avant d’accéder à `m_fltVal` , vérifiez d’abord la valeur de [CDBVariant :: m_dwType](#m_dwtype). Si `m_dwType` a `m_fltVal` la valeur DBVT_SINGLE, contient une valeur valide ; sinon, l’accès à `m_fltVal` produira des résultats non fiables.

## <a name="cdbvariantm_ival"></a><a name="m_ival"></a> CDBVariant :: m_iVal

Stocke une valeur de type **`short`** .

### <a name="remarks"></a>Notes

Le `m_iVal` membre de données appartient à une Union. Avant d’accéder à `m_iVal` , vérifiez d’abord la valeur de [CDBVariant :: m_dwType](#m_dwtype). Si `m_dwType` a `m_iVal` la valeur DBVT_SHORT, contient une valeur valide ; sinon, l’accès à `m_iVal` produira des résultats non fiables.

## <a name="cdbvariantm_lval"></a><a name="m_lval"></a> CDBVariant :: m_lVal

Stocke une valeur de type **`long`** .

### <a name="remarks"></a>Notes

Le `m_lVal` membre de données appartient à une Union. Avant d’accéder à `m_lVal` , vérifiez d’abord la valeur de [CDBVariant :: m_dwType](#m_dwtype). Si `m_dwType` a `m_lVal` la valeur DBVT_LONG, contient une valeur valide ; sinon, l’accès à `m_lVal` produira des résultats non fiables.

## <a name="cdbvariantm_pbinary"></a><a name="m_pbinary"></a> CDBVariant :: m_pbinary

Stocke un pointeur vers un objet de type [CLongBinary](../../mfc/reference/clongbinary-class.md).

### <a name="remarks"></a>Notes

Le `m_pbinary` membre de données appartient à une Union. Avant d’accéder à `m_pbinary` , vérifiez d’abord la valeur de [CDBVariant :: m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_BINARY, `m_pbinary` contient un pointeur valide ; sinon, l’accès à `m_pbinary` produira des résultats non fiables.

## <a name="cdbvariantm_pdate"></a><a name="m_pdate"></a> CDBVariant :: m_pdate

Stocke un pointeur vers un objet de type TIMESTAMP_STRUCT.

### <a name="remarks"></a>Notes

Le `m_pdate` membre de données appartient à une Union. Avant d’accéder à `m_pdate` , vérifiez d’abord la valeur de [CDBVariant :: m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_DATE, `m_pdate` contient un pointeur valide ; sinon, l’accès à `m_pdate` produira des résultats non fiables.

Pour plus d’informations sur le type de données TIMESTAMP_STRUCT, consultez la rubrique [types de données C](/sql/odbc/reference/appendixes/c-data-types) dans l’annexe D du *Guide de référence du programmeur ODBC* dans le SDK Windows.

## <a name="cdbvariantm_pstring"></a><a name="m_pstring"></a> CDBVariant :: m_pstring

Stocke un pointeur vers un objet de type [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Notes

Le `m_pstring` membre de données appartient à une Union. Avant d’accéder à `m_pstring` , vérifiez d’abord la valeur de [CDBVariant :: m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_STRING, `m_pstring` contient un pointeur valide ; sinon, l’accès à `m_pstring` produira des résultats non fiables.

## <a name="cdbvariantm_pstringa"></a><a name="m_pstringa"></a> CDBVariant :: m_pstringA

Stocke un pointeur vers un objet [CSTRING](../../atl-mfc-shared/reference/cstringt-class.md) ASCII.

### <a name="remarks"></a>Notes

Le `m_pstringA` membre de données appartient à une Union. Avant d’accéder à `m_pstringA` , vérifiez d’abord la valeur de [CDBVariant :: m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_ASTRING, `m_pstringA` contient un pointeur valide ; sinon, l’accès à `m_pstringA` produira des résultats non fiables.

## <a name="cdbvariantm_pstringw"></a><a name="m_pstringw"></a> CDBVariant :: m_pstringW

Stocke un pointeur vers un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) étendu.

### <a name="remarks"></a>Notes

Le `m_pstringW` membre de données appartient à une Union. Avant d’accéder à `m_pstringW` , vérifiez d’abord la valeur de [CDBVariant :: m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_WSTRING, `m_pstringW` contient un pointeur valide ; sinon, l’accès à `m_pstringW` produira des résultats non fiables.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)
