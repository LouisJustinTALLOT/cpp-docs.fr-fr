---
title: CDBVariant (classe)
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
ms.openlocfilehash: 48a2e08d056e3bfef8a06b80ae6607947923cbcb
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328946"
---
# <a name="cdbvariant-class"></a>CDBVariant (classe)

Représente un type de données variant pour les classes ODBC MFC.

## <a name="syntax"></a>Syntaxe

```
class CDBVariant
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CDBVariant::CDBVariant](#cdbvariant)|Construit un objet `CDBVariant`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CDBVariant::Clear](#clear)|Efface le `CDBVariant` objet.|

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[CDBVariant::m_dwType](#m_dwtype)|Contient le type de données de la valeur actuellement stockée. Tapez `DWORD`.|

### <a name="public-union-members"></a>Membres d’Union publiques

|Name|Description|
|----------|-----------------|
|[CDBVariant::m_boolVal](#m_boolval)|Contient une valeur de type **BOOL**.|
|[CDBVariant::m_chVal](#m_chval)|Contient une valeur de type **unsigned char**.|
|[CDBVariant::m_dblVal](#m_dblval)|Contient une valeur de type **double**.|
|[CDBVariant::m_fltVal](#m_fltval)|Contient une valeur de type **float**.|
|[CDBVariant::m_iVal](#m_ival)|Contient une valeur de type **court**.|
|[CDBVariant::m_lVal](#m_lval)|Contient une valeur de type **long**.|
|[CDBVariant::m_pbinary](#m_pbinary)|Contient un pointeur vers un objet de type `CLongBinary`.|
|[CDBVariant::m_pdate](#m_pdate)|Contient un pointeur vers un objet de type **TIMESTAMP_STRUCT**.|
|[CDBVariant::m_pstring](#m_pstring)|Contient un pointeur vers un objet de type `CString`.|
|[CDBVariant::m_pstringA](#m_pstringa)|Stocke un pointeur vers ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet.|
|[CDBVariant::m_pstringW](#m_pstringw)|Stocke un pointeur vers une large [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet.|

## <a name="remarks"></a>Notes

`CDBVariant` n’a pas d’une classe de base.

`CDBVariant` est similaire à [COleVariant](../../mfc/reference/colevariant-class.md); Cependant, `CDBVariant` n’utilise pas d’OLE. `CDBVariant` vous permet de stocker une valeur sans se préoccuper du type de données. `CDBVariant` suit le type de données de la valeur actuelle, qui est stocké dans une union.

Classe [CRecordset](../../mfc/reference/crecordset-class.md) utilise `CDBVariant` objets dans les trois fonctions de membre : `GetFieldValue`, `GetBookmark`, et `SetBookmark`. Par exemple, `GetFieldValue` vous permet d’extraire dynamiquement les données dans une colonne. Étant donné que le type de données de la colonne ne peut pas être connu au moment de l’exécution, `GetFieldValue` utilise un `CDBVariant` objet à stocker les données de la colonne.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CDBVariant`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdb.h

##  <a name="cdbvariant"></a>  CDBVariant::CDBVariant

Crée une valeur NULL `CDBVariant` objet.

```
CDBVariant();
```

### <a name="remarks"></a>Notes

Définit le [m_dwType](#m_dwtype) DBVT_NULL des données membres.

##  <a name="clear"></a>  CDBVariant::Clear

Appelez cette fonction membre pour effacer le `CDBVariant` objet.

```
void Clear();
```

### <a name="remarks"></a>Notes

Si la valeur de la [m_dwType](#m_dwtype) membre de données est DBVT_DATE, DBVT_STRING ou DBVT_BINARY, `Clear` libère la mémoire associée au membre de l’union de pointeur. `Clear` définit `m_dwType` à DBVT_NULL.

Le `CDBVariant` appels de destructeur `Clear`.

##  <a name="m_boolval"></a>  CDBVariant::m_boolVal

Stocke une valeur de type BOOL.

### <a name="remarks"></a>Notes

Le `m_boolVal` membre de données appartient à une union. Avant d’accéder à `m_boolVal`, vérifiez tout d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_BOOL, puis `m_boolVal` contiendra une valeur valide ; sinon, l’accès à `m_boolVal` produira des résultats imprévisibles.

##  <a name="m_chval"></a>  CDBVariant::m_chVal

Stocke une valeur de type **unsigned char**.

### <a name="remarks"></a>Notes

Le `m_chVal` membre de données appartient à une union. Avant d’accéder à `m_chVal`, vérifiez tout d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_UCHAR, puis `m_chVal` contient une valeur valide ; sinon, l’accès à `m_chVal` produira des résultats imprévisibles.

##  <a name="m_dblval"></a>  CDBVariant::m_dblVal

Stocke une valeur de type **double**.

### <a name="remarks"></a>Notes

Le `m_dblVal` membre de données appartient à une union. Avant d’accéder à `m_dblVal`, vérifiez tout d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_DOUBLE, puis `m_dblVal` contient une valeur valide ; sinon, l’accès à `m_dblVal` produira des résultats imprévisibles.

##  <a name="m_dwtype"></a>  CDBVariant::m_dwType

Ce membre de données contient le type de données pour la valeur actuellement stockée dans le `CDBVariant` membre de données d’union de l’objet.

### <a name="remarks"></a>Notes

Avant d’accéder à cette union, vous devez vérifier la valeur de `m_dwType` afin de déterminer le membre de données d’union à accéder. Le tableau suivant répertorie les valeurs possibles pour `m_dwType` et le membre de données d’union correspondant.

|m_dwType|Membre de données d’union|
|---------------|-----------------------|
|DBVT_NULL|Aucun membre union est valide pour l’accès.|
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

##  <a name="m_fltval"></a>  CDBVariant::m_fltVal

Stocke une valeur de type **float**.

### <a name="remarks"></a>Notes

Le `m_fltVal` membre de données appartient à une union. Avant d’accéder à `m_fltVal`, vérifiez tout d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_SINGLE, puis `m_fltVal` contient une valeur valide ; sinon, l’accès à `m_fltVal` produira des résultats imprévisibles.

##  <a name="m_ival"></a>  CDBVariant::m_iVal

Stocke une valeur de type **court**.

### <a name="remarks"></a>Notes

Le `m_iVal` membre de données appartient à une union. Avant d’accéder à `m_iVal`, vérifiez tout d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_SHORT, puis `m_iVal` contient une valeur valide ; sinon, l’accès à `m_iVal` produira des résultats imprévisibles.

##  <a name="m_lval"></a>  CDBVariant::m_lVal

Stocke une valeur de type **long**.

### <a name="remarks"></a>Notes

Le `m_lVal` membre de données appartient à une union. Avant d’accéder à `m_lVal`, vérifiez tout d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_LONG, puis `m_lVal` contient une valeur valide ; sinon, l’accès à `m_lVal` produira des résultats imprévisibles.

##  <a name="m_pbinary"></a>  CDBVariant::m_pbinary

Stocke un pointeur vers un objet de type [CLongBinary](../../mfc/reference/clongbinary-class.md).

### <a name="remarks"></a>Notes

Le `m_pbinary` membre de données appartient à une union. Avant d’accéder à `m_pbinary`, vérifiez tout d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_BINARY, puis `m_pbinary` contient un pointeur valide ; sinon, l’accès à `m_pbinary` produira des résultats imprévisibles.

##  <a name="m_pdate"></a>  CDBVariant::m_pdate

Stocke un pointeur vers un objet de type TIMESTAMP_STRUCT.

### <a name="remarks"></a>Notes

Le `m_pdate` membre de données appartient à une union. Avant d’accéder à `m_pdate`, vérifiez tout d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_DATE, puis `m_pdate` contient un pointeur valide ; sinon, l’accès à `m_pdate` produira des résultats imprévisibles.

Pour plus d’informations sur le type de données TIMESTAMP_STRUCT, consultez la rubrique [les Types de données C](/sql/odbc/reference/appendixes/c-data-types) dans l’annexe D de la *de référence du programmeur ODBC* dans le SDK Windows.

##  <a name="m_pstring"></a>  CDBVariant::m_pstring

Stocke un pointeur vers un objet de type [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Notes

Le `m_pstring` membre de données appartient à une union. Avant d’accéder à `m_pstring`, vérifiez tout d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_STRING, puis `m_pstring` contient un pointeur valide ; sinon, l’accès à `m_pstring` produira des résultats imprévisibles.

##  <a name="m_pstringa"></a>  CDBVariant::m_pstringA

Stocke un pointeur vers ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet.

### <a name="remarks"></a>Notes

Le `m_pstringA` membre de données appartient à une union. Avant d’accéder à `m_pstringA`, vérifiez tout d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_ASTRING, puis `m_pstringA` contient un pointeur valide ; sinon, l’accès à `m_pstringA` produira des résultats imprévisibles.

##  <a name="m_pstringw"></a>  CDBVariant::m_pstringW

Stocke un pointeur vers une large [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet.

### <a name="remarks"></a>Notes

Le `m_pstringW` membre de données appartient à une union. Avant d’accéder à `m_pstringW`, vérifiez tout d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` a la valeur DBVT_WSTRING, puis `m_pstringW` contient un pointeur valide ; sinon, l’accès à `m_pstringW` produira des résultats imprévisibles.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CRecordset, classe](../../mfc/reference/crecordset-class.md)
