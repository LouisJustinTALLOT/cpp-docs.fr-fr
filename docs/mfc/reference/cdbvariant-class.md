---
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
ms.openlocfilehash: 9bb70acb43f2e73ade86b753ebbb7949759ce88d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754599"
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
|[CDBVariant::Clair](#clear)|Dégage l' `CDBVariant` objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDBVariant::m_dwType](#m_dwtype)|Contient le type de données de la valeur actuellement stockée. Tapez `DWORD`.|

### <a name="public-union-members"></a>Membres de l’Union publique

|Nom|Description|
|----------|-----------------|
|[CDBVariant::m_boolVal](#m_boolval)|Contient une valeur de type **BOOL**.|
|[CDBVariant::m_chVal](#m_chval)|Contient une valeur de type **char non signé**.|
|[CDBVariant::m_dblVal](#m_dblval)|Contient une valeur de type **double**.|
|[CDBVariant::m_fltVal](#m_fltval)|Contient une valeur de type **flotteur**.|
|[CDBVariant::m_iVal](#m_ival)|Contient une valeur de type **court**.|
|[CDBVariant::m_lVal](#m_lval)|Contient une valeur de type **long**.|
|[CDBVariant::m_pbinary](#m_pbinary)|Contient un pointeur à `CLongBinary`un objet de type .|
|[CDBVariant::m_pdate](#m_pdate)|Contient un pointeur à un objet de type **TIMESTAMP_STRUCT**.|
|[CDBVariant::m_pstring](#m_pstring)|Contient un pointeur à `CString`un objet de type .|
|[CDBVariant::m_pstringA](#m_pstringa)|Stocke un pointeur sur un objet ASCII [CString.](../../atl-mfc-shared/reference/cstringt-class.md)|
|[CDBVariant::m_pstringW](#m_pstringw)|Stocke un pointeur sur un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) large.|

## <a name="remarks"></a>Notes

`CDBVariant`n’a pas de classe de base.

`CDBVariant`est similaire à [COleVariant;](../../mfc/reference/colevariant-class.md) cependant, `CDBVariant` n’utilise pas OLE. `CDBVariant`vous permet de stocker une valeur sans vous soucier du type de données de la valeur. `CDBVariant`suit le type de données de la valeur actuelle, qui est stocké dans une union.

Classe [CRecordset](../../mfc/reference/crecordset-class.md) `CDBVariant` utilise des objets dans `GetFieldValue` `GetBookmark`trois `SetBookmark`fonctions membres: , , et . Par exemple, `GetFieldValue` vous permet d’obtenir dynamiquement des données dans une colonne. Étant donné que le type de données de `GetFieldValue` la `CDBVariant` colonne peut ne pas être connu au moment de l’exécution, utilise un objet pour stocker les données de la colonne.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CDBVariant`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdb.h

## <a name="cdbvariantcdbvariant"></a><a name="cdbvariant"></a>CDBVariant::CDBVariant

Crée un `CDBVariant` objet NULL.

```
CDBVariant();
```

### <a name="remarks"></a>Notes

Définit [le](#m_dwtype) m_dwType membre des données à DBVT_NULL.

## <a name="cdbvariantclear"></a><a name="clear"></a>CDBVariant::Clair

Appelez cette fonction de `CDBVariant` membre pour effacer l’objet.

```cpp
void Clear();
```

### <a name="remarks"></a>Notes

Si la valeur du membre de la [m_dwType](#m_dwtype) des données est DBVT_DATE, DBVT_STRING `Clear` ou DBVT_BINARY, libère la mémoire associée au membre du pointeur syndical. `Clear`s’DBVT_NULL. `m_dwType`

Le `CDBVariant` destructor `Clear`appelle .

## <a name="cdbvariantm_boolval"></a><a name="m_boolval"></a>CDBVariant::m_boolVal

Stocke une valeur de type BOOL.

### <a name="remarks"></a>Notes

Le `m_boolVal` membre des données appartient à un syndicat. Avant d’accéder `m_boolVal`, vérifiez d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` elle est réglée pour `m_boolVal` DBVT_BOOL, cela contiendra une valeur valide; autrement, l’accès `m_boolVal` produira des résultats peu fiables.

## <a name="cdbvariantm_chval"></a><a name="m_chval"></a>CDBVariant::m_chVal

Stocke une valeur de type **char non signé**.

### <a name="remarks"></a>Notes

Le `m_chVal` membre des données appartient à un syndicat. Avant d’accéder `m_chVal`, vérifiez d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` elle est réglée pour `m_chVal` DBVT_UCHAR, contient alors une valeur valide; autrement, l’accès `m_chVal` produira des résultats peu fiables.

## <a name="cdbvariantm_dblval"></a><a name="m_dblval"></a>CDBVariant::m_dblVal

Stocke une valeur de type **double**.

### <a name="remarks"></a>Notes

Le `m_dblVal` membre des données appartient à un syndicat. Avant d’accéder `m_dblVal`, vérifiez d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` elle est réglée pour `m_dblVal` DBVT_DOUBLE, contient alors une valeur valide; autrement, l’accès `m_dblVal` produira des résultats peu fiables.

## <a name="cdbvariantm_dwtype"></a><a name="m_dwtype"></a>CDBVariant::m_dwType

Ce membre des données contient le type de `CDBVariant` données pour la valeur qui est actuellement stockée dans le membre des données syndicales de l’objet.

### <a name="remarks"></a>Notes

Avant d’accéder à ce syndicat, `m_dwType` vous devez vérifier la valeur de afin de déterminer quel membre des données syndicales à accéder. Le tableau suivant énumère `m_dwType` les valeurs possibles et le membre correspondant des données syndicales.

|m_dwType|Membre des données syndicales|
|---------------|-----------------------|
|DBVT_NULL|Aucun membre du syndicat n’est valide pour l’accès.|
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

## <a name="cdbvariantm_fltval"></a><a name="m_fltval"></a>CDBVariant::m_fltVal

Stocke une valeur de type **flotteur**.

### <a name="remarks"></a>Notes

Le `m_fltVal` membre des données appartient à un syndicat. Avant d’accéder `m_fltVal`, vérifiez d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` elle est réglée pour `m_fltVal` DBVT_SINGLE, contient alors une valeur valide; autrement, l’accès `m_fltVal` produira des résultats peu fiables.

## <a name="cdbvariantm_ival"></a><a name="m_ival"></a>CDBVariant::m_iVal

Stocke une valeur de type **court**.

### <a name="remarks"></a>Notes

Le `m_iVal` membre des données appartient à un syndicat. Avant d’accéder `m_iVal`, vérifiez d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` elle est réglée pour `m_iVal` DBVT_SHORT, contient alors une valeur valide; autrement, l’accès `m_iVal` produira des résultats peu fiables.

## <a name="cdbvariantm_lval"></a><a name="m_lval"></a>CDBVariant::m_lVal

Stocke une valeur de type **long**.

### <a name="remarks"></a>Notes

Le `m_lVal` membre des données appartient à un syndicat. Avant d’accéder `m_lVal`, vérifiez d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` elle est réglée pour `m_lVal` DBVT_LONG, contient alors une valeur valide; autrement, l’accès `m_lVal` produira des résultats peu fiables.

## <a name="cdbvariantm_pbinary"></a><a name="m_pbinary"></a>CDBVariant::m_pbinary

Stocke un pointeur à un objet de type [CLongBinary](../../mfc/reference/clongbinary-class.md).

### <a name="remarks"></a>Notes

Le `m_pbinary` membre des données appartient à un syndicat. Avant d’accéder `m_pbinary`, vérifiez d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` elle est réglée pour `m_pbinary` DBVT_BINARY, contient alors un pointeur valide; autrement, l’accès `m_pbinary` produira des résultats peu fiables.

## <a name="cdbvariantm_pdate"></a><a name="m_pdate"></a>CDBVariant::m_pdate

Stocke un pointeur sur un objet de type TIMESTAMP_STRUCT.

### <a name="remarks"></a>Notes

Le `m_pdate` membre des données appartient à un syndicat. Avant d’accéder `m_pdate`, vérifiez d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` elle est réglée pour `m_pdate` DBVT_DATE, contient alors un pointeur valide; autrement, l’accès `m_pdate` produira des résultats peu fiables.

Pour plus d’informations sur le type de données TIMESTAMP_STRUCT, consultez le sujet [C Data Types](/sql/odbc/reference/appendixes/c-data-types) à l’annexe D de la référence du *programmeur ODBC* dans le SDK Windows.

## <a name="cdbvariantm_pstring"></a><a name="m_pstring"></a>CDBVariant::m_pstring

Stocke un pointeur à un objet de type [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Notes

Le `m_pstring` membre des données appartient à un syndicat. Avant d’accéder `m_pstring`, vérifiez d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` elle est réglée pour `m_pstring` DBVT_STRING, contient alors un pointeur valide; autrement, l’accès `m_pstring` produira des résultats peu fiables.

## <a name="cdbvariantm_pstringa"></a><a name="m_pstringa"></a>CDBVariant::m_pstringA

Stocke un pointeur sur un objet ASCII [CString.](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>Notes

Le `m_pstringA` membre des données appartient à un syndicat. Avant d’accéder `m_pstringA`, vérifiez d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` elle est réglée pour `m_pstringA` DBVT_ASTRING, contient alors un pointeur valide; autrement, l’accès `m_pstringA` produira des résultats peu fiables.

## <a name="cdbvariantm_pstringw"></a><a name="m_pstringw"></a>CDBVariant::m_pstringW

Stocke un pointeur sur un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) large.

### <a name="remarks"></a>Notes

Le `m_pstringW` membre des données appartient à un syndicat. Avant d’accéder `m_pstringW`, vérifiez d’abord la valeur de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` elle est réglée pour `m_pstringW` DBVT_WSTRING, contient alors un pointeur valide; autrement, l’accès `m_pstringW` produira des résultats peu fiables.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)
