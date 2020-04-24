---
title: CMFCFilterChunkValueImpl, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::Clear
- AFXWIN/CMFCFilterChunkValueImpl::CopyChunk
- AFXWIN/CMFCFilterChunkValueImpl::CopyFrom
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkGUID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkPID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkType
- AFXWIN/CMFCFilterChunkValueImpl::GetString
- AFXWIN/CMFCFilterChunkValueImpl::GetValue
- AFXWIN/CMFCFilterChunkValueImpl::GetValueNoAlloc
- AFXWIN/CMFCFilterChunkValueImpl::IsValid
- AFXWIN/CMFCFilterChunkValueImpl::SetBoolValue
- AFXWIN/CMFCFilterChunkValueImpl::SetDwordValue
- AFXWIN/CMFCFilterChunkValueImpl::SetFileTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetInt64Value
- AFXWIN/CMFCFilterChunkValueImpl::SetIntValue
- AFXWIN/CMFCFilterChunkValueImpl::SetLongValue
- AFXWIN/CMFCFilterChunkValueImpl::SetSystemTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetTextValue
- AFXWIN/CMFCFilterChunkValueImpl::SetChunk
helpviewer_keywords:
- CMFCFilterChunkValueImpl [MFC], CMFCFilterChunkValueImpl
- CMFCFilterChunkValueImpl [MFC], Clear
- CMFCFilterChunkValueImpl [MFC], CopyChunk
- CMFCFilterChunkValueImpl [MFC], CopyFrom
- CMFCFilterChunkValueImpl [MFC], GetChunkGUID
- CMFCFilterChunkValueImpl [MFC], GetChunkPID
- CMFCFilterChunkValueImpl [MFC], GetChunkType
- CMFCFilterChunkValueImpl [MFC], GetString
- CMFCFilterChunkValueImpl [MFC], GetValue
- CMFCFilterChunkValueImpl [MFC], GetValueNoAlloc
- CMFCFilterChunkValueImpl [MFC], IsValid
- CMFCFilterChunkValueImpl [MFC], SetBoolValue
- CMFCFilterChunkValueImpl [MFC], SetDwordValue
- CMFCFilterChunkValueImpl [MFC], SetFileTimeValue
- CMFCFilterChunkValueImpl [MFC], SetInt64Value
- CMFCFilterChunkValueImpl [MFC], SetIntValue
- CMFCFilterChunkValueImpl [MFC], SetLongValue
- CMFCFilterChunkValueImpl [MFC], SetSystemTimeValue
- CMFCFilterChunkValueImpl [MFC], SetTextValue
- CMFCFilterChunkValueImpl [MFC], SetChunk
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
ms.openlocfilehash: c89d41f7db43d9504bfc22cbf35a59fcceb511e2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752363"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>CMFCFilterChunkValueImpl, classe

Il s’agit d’une classe qui simplifie à la fois le morceau et la logique de paire de valeur de propriété.

## <a name="syntax"></a>Syntaxe

```
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|Destruction de l’objet.|
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|Construit l’objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::Clair](#clear)|Efface le ChunkValue.|
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|Copie ce morceau à une structure décrivant les caractéristiques d’un morceau.|
|[CMFCFilterChunkValueImpl::CopyDe](#copyfrom)|Initialise cette valeur de morceau de l’autre valeur.|
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|Récupère le morceau DE GUID.|
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|Récupère le morceau PID (ID de propriété).|
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|Obtient type de morceau.|
|[CMFCFilterChunkValueImpl::GetString](#getstring)|Récupère la valeur de la chaîne.|
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|Récupère la valeur en tant que propvariant alloué.|
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|Rendements valeur (valeur interne) non allouée.|
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|Vérifie si cette valeur de propriété est valide ou non.|
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|Surchargé. Définit la propriété par la clé d’un Boolean.|
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|Définit la propriété par la clé d’un DWORD.|
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|Définit la propriété par la clé d’un temps de fichier.|
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|Définit la propriété par la clé d’un int64.|
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|Définit la propriété par la clé d’un int.|
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|Définit la propriété par la clé d’un LONG.|
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|Définit la propriété par la clé d’un SystemTime.|
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|Définit la propriété par la clé d’une chaîne Unicode.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|Une fonction d’aide qui définit les propriétés communes du morceau.|

## <a name="remarks"></a>Notes

Pour l’utiliser, il vous suffit de créer une classe CMFCFilterChunkValueImpl du bon type

Exemple :

CMFCFilterChunkValueImpl morceau;

hr et morceau. SetBoolValue (PKEY_IsAttachment, vrai);

or

hr et morceau. SetFileTimeValue (PKEY_ItemDate, ftLastModified);

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ATL::IFilterChunkValue`

[CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cmfcfilterchunkvalueimplclear"></a><a name="clear"></a>CMFCFilterChunkValueImpl::Clair

Efface le ChunkValue.

```cpp
void Clear();
```

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="cmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl

Construit l’objet.

```
CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="_dtorcmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl

Destruction de l’objet.

```
virtual ~CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplcopychunk"></a><a name="copychunk"></a>CMFCFilterChunkValueImpl::CopyChunk

Copie ce morceau à une structure décrivant les caractéristiques d’un morceau.

```
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```

### <a name="parameters"></a>Paramètres

*pStatChunk*<br/>
Un pointeur à la valeur de destination décrivant les caractéristiques du morceau.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; sinon un code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplcopyfrom"></a><a name="copyfrom"></a>CMFCFilterChunkValueImpl::CopyDe

Initialise cette valeur de morceau de l’autre valeur.

```cpp
void CopyFrom (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Paramètres

*pValue*<br/>
Spécifie la valeur source à copier.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplgetchunkguid"></a><a name="getchunkguid"></a>CMFCFilterChunkValueImpl::GetChunkGUID

Récupère le morceau DE GUID.

```
REFGUID GetChunkGUID() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence à un GUID identifiant le morceau.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplgetchunkpid"></a><a name="getchunkpid"></a>CMFCFilterChunkValueImpl::GetChunkPID

Récupère le morceau PID (ID de propriété).

```
DWORD GetChunkPID() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD contenant l’ID de propriété.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplgetchunktype"></a><a name="getchunktype"></a>CMFCFilterChunkValueImpl::GetChunkType

Récupère le type de morceau.

```
CHUNKSTATE GetChunkType() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur énumérée CHUNKSTATE, qui précise si le morceau actuel est une propriété de type texte ou une propriété de type valeur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplgetstring"></a><a name="getstring"></a>CMFCFilterChunkValueImpl::GetString

Récupère la valeur de la chaîne.

```
CString &GetString();
```

### <a name="return-value"></a>Valeur de retour

Une ficelle contenant la valeur du morceau.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplgetvalue"></a><a name="getvalue"></a>CMFCFilterChunkValueImpl::GetValue

Récupère la valeur en tant que propvariant alloué.

```
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```

### <a name="parameters"></a>Paramètres

*ppPropVariant*<br/>
Lorsque la fonction revient, ce paramètre contient la valeur du morceau.

### <a name="return-value"></a>Valeur de retour

S_OK si PROPVARIANT a été alloué avec succès et la valeur du morceau a été copié avec succès à *ppPropVariant;* sinon un code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplgetvaluenoalloc"></a><a name="getvaluenoalloc"></a>CMFCFilterChunkValueImpl::GetValueNoAlloc

Retourne la valeur non allouée (valeur interne).

```
PROPVARIANT GetValueNoAlloc ();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur actuelle du morceau.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplisvalid"></a><a name="isvalid"></a>CMFCFilterChunkValueImpl::IsValid

Vérifie si cette valeur de propriété est valide ou non.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la valeur actuelle du morceau est valide; autrement FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetboolvalue"></a><a name="setboolvalue"></a>CMFCFilterChunkValueImpl::SetBoolValue

Surchargé. Définit la propriété par la clé d’un Boolean.

```
HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);

HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    VARIANT_BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Paramètres

*pkey*<br/>
Spécifie une clé de propriété.

*bVal (En)*<br/>
Spécifie la valeur du morceau à définir.

*chunkType*<br/>
Les drapeaux indiquent si ce morceau contient un texte de type texte ou une propriété de type valeur. Les valeurs du drapeau sont tirées de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et le sous-langage associés à un morceau de texte. Chunk local est utilisé par les indexateurs de documents pour effectuer la rupture de mot appropriée du texte. Si le morceau n’est ni de type texte ni de type valeur avec des VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource (en)*<br/>
La longueur des caractères du texte source à partir duquel le morceau actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par personnage entre le texte source et le texte dérivé. Une valeur non zéro signifie qu’il n’existe pas de correspondance directe de ce type.

*cwcStartSource (en)*<br/>
Le décalage à partir duquel le texte source pour un morceau dérivé commence dans le morceau source.

*chunkBreakType*<br/>
Le type de rupture qui sépare le morceau précédent du morceau actuel. Les valeurs sont issues de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; sinon un code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetchunk"></a><a name="setchunk"></a>CMFCFilterChunkValueImpl::SetChunk

Une fonction d’aide qui définit les propriétés communes du morceau.

```
HRESULT SetChunk(
    REFPROPERTYKEY pkey,
    CHUNKSTATE chunkType=CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Paramètres

*pkey*<br/>
Spécifie une clé de propriété.

*chunkType*<br/>
Les drapeaux indiquent si ce morceau contient un texte de type texte ou une propriété de type valeur. Les valeurs du drapeau sont tirées de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et le sous-langage associés à un morceau de texte. Chunk local est utilisé par les indexateurs de documents pour effectuer la rupture de mot appropriée du texte. Si le morceau n’est ni de type texte ni de type valeur avec des VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource (en)*<br/>
La longueur des caractères du texte source à partir duquel le morceau actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par personnage entre le texte source et le texte dérivé. Une valeur non zéro signifie qu’il n’existe pas de correspondance directe de ce type.

*cwcStartSource (en)*<br/>
Le décalage à partir duquel le texte source pour un morceau dérivé commence dans le morceau source.

*chunkBreakType*<br/>
Le type de rupture qui sépare le morceau précédent du morceau actuel. Les valeurs sont issues de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; autrement code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetdwordvalue"></a><a name="setdwordvalue"></a>CMFCFilterChunkValueImpl::SetDwordValue

Réglez la propriété par la clé d’un DWORD.

```
HRESULT SetDwordValue(
    REFPROPERTYKEY pkey,
    DWORD dwVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Paramètres

*pkey*<br/>
Spécifie une clé de propriété.

*dwVal (en)*<br/>
Spécifie la valeur du morceau à définir.

*chunkType*<br/>
Les drapeaux indiquent si ce morceau contient un texte de type texte ou une propriété de type valeur. Les valeurs du drapeau sont tirées de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et le sous-langage associés à un morceau de texte. Chunk local est utilisé par les indexateurs de documents pour effectuer la rupture de mot appropriée du texte. Si le morceau n’est ni de type texte ni de type valeur avec des VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource (en)*<br/>
La longueur des caractères du texte source à partir duquel le morceau actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par personnage entre le texte source et le texte dérivé. Une valeur non zéro signifie qu’il n’existe pas de correspondance directe de ce type.

*cwcStartSource (en)*<br/>
Le décalage à partir duquel le texte source pour un morceau dérivé commence dans le morceau source.

*chunkBreakType*<br/>
Le type de rupture qui sépare le morceau précédent du morceau actuel. Les valeurs sont issues de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; sinon un code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetfiletimevalue"></a><a name="setfiletimevalue"></a>CMFCFilterChunkValueImpl::SetFileTimeValue

Réglez la propriété par la clé d’un temps de fichier.

```
HRESULT SetFileTimeValue(
    REFPROPERTYKEY pkey,
    FILETIME dtVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Paramètres

*pkey*<br/>
Spécifie une clé de propriété.

*dtVal (en)*<br/>
Spécifie la valeur du morceau à définir.

*chunkType*<br/>
Les drapeaux indiquent si ce morceau contient un texte de type texte ou une propriété de type valeur. Les valeurs du drapeau sont tirées de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et le sous-langage associés à un morceau de texte. Chunk local est utilisé par les indexateurs de documents pour effectuer la rupture de mot appropriée du texte. Si le morceau n’est ni de type texte ni de type valeur avec des VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource (en)*<br/>
La longueur des caractères du texte source à partir duquel le morceau actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par personnage entre le texte source et le texte dérivé. Une valeur non zéro signifie qu’il n’existe pas de correspondance directe de ce type.

*cwcStartSource (en)*<br/>
Le décalage à partir duquel le texte source pour un morceau dérivé commence dans le morceau source.

*chunkBreakType*<br/>
Le type de rupture qui sépare le morceau précédent du morceau actuel. Les valeurs sont issues de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; sinon un code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetint64value"></a><a name="setint64value"></a>CMFCFilterChunkValueImpl::SetInt64Value

Réglez la propriété par la clé d’un int64.

```
HRESULT SetInt64Value(
    REFPROPERTYKEY pkey,
    __int64 nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Paramètres

*pkey*<br/>
Spécifie une clé de propriété.

*nVal (en)*<br/>
Spécifie la valeur du morceau à définir.

*chunkType*<br/>
Les drapeaux indiquent si ce morceau contient un texte de type texte ou une propriété de type valeur. Les valeurs du drapeau sont tirées de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et le sous-langage associés à un morceau de texte. Chunk local est utilisé par les indexateurs de documents pour effectuer la rupture de mot appropriée du texte. Si le morceau n’est ni de type texte ni de type valeur avec des VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource (en)*<br/>
La longueur des caractères du texte source à partir duquel le morceau actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par personnage entre le texte source et le texte dérivé. Une valeur non zéro signifie qu’il n’existe pas de correspondance directe de ce type.

*cwcStartSource (en)*<br/>
Le décalage à partir duquel le texte source pour un morceau dérivé commence dans le morceau source.

*chunkBreakType*<br/>
Le type de rupture qui sépare le morceau précédent du morceau actuel. Les valeurs sont issues de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; sinon un code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetintvalue"></a><a name="setintvalue"></a>CMFCFilterChunkValueImpl::SetIntValue

Réglez la propriété par la clé d’un int.

```
HRESULT SetIntValue(
    REFPROPERTYKEY pkey,
    int nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Paramètres

*pkey*<br/>
Spécifie une clé de propriété.

*nVal (en)*<br/>
Spécifie la valeur du morceau à définir.

*chunkType*<br/>
Les drapeaux indiquent si ce morceau contient un texte de type texte ou une propriété de type valeur. Les valeurs du drapeau sont tirées de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et le sous-langage associés à un morceau de texte. Chunk local est utilisé par les indexateurs de documents pour effectuer la rupture de mot appropriée du texte. Si le morceau n’est ni de type texte ni de type valeur avec des VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource (en)*<br/>
La longueur des caractères du texte source à partir duquel le morceau actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par personnage entre le texte source et le texte dérivé. Une valeur non zéro signifie qu’il n’existe pas de correspondance directe de ce type.

*cwcStartSource (en)*<br/>
Le décalage à partir duquel le texte source pour un morceau dérivé commence dans le morceau source.

*chunkBreakType*<br/>
Le type de rupture qui sépare le morceau précédent du morceau actuel. Les valeurs sont issues de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; sinon un code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetlongvalue"></a><a name="setlongvalue"></a>CMFCFilterChunkValueImpl::SetLongValue

Réglez la propriété par la clé d’un LONG.

```
HRESULT SetLongValue(
    REFPROPERTYKEY pkey,
    long lVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Paramètres

*pkey*<br/>
Spécifie une clé de propriété.

*lVal (En)*<br/>
Spécifie la valeur du morceau à définir.

*chunkType*<br/>
Les drapeaux indiquent si ce morceau contient un texte de type texte ou une propriété de type valeur. Les valeurs du drapeau sont tirées de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et le sous-langage associés à un morceau de texte. Chunk local est utilisé par les indexateurs de documents pour effectuer la rupture de mot appropriée du texte. Si le morceau n’est ni de type texte ni de type valeur avec des VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource (en)*<br/>
La longueur des caractères du texte source à partir duquel le morceau actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par personnage entre le texte source et le texte dérivé. Une valeur non zéro signifie qu’il n’existe pas de correspondance directe de ce type.

*cwcStartSource (en)*<br/>
Le décalage à partir duquel le texte source pour un morceau dérivé commence dans le morceau source.

*chunkBreakType*<br/>
Le type de rupture qui sépare le morceau précédent du morceau actuel. Les valeurs sont issues de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; sinon un code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetsystemtimevalue"></a><a name="setsystemtimevalue"></a>CMFCFilterChunkValueImpl::SetSystemTimeValue

Définit la propriété par la clé d’un SystemTime.

```
HRESULT SetSystemTimeValue(
    REFPROPERTYKEY pkey,
    const SYSTEMTIME& systemTime,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Paramètres

*pkey*<br/>
Spécifie une clé de propriété.

*systemTime (en)*<br/>
Spécifie la valeur du morceau à définir.

*chunkType*<br/>
Les drapeaux indiquent si ce morceau contient un texte de type texte ou une propriété de type valeur. Les valeurs du drapeau sont tirées de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et le sous-langage associés à un morceau de texte. Chunk local est utilisé par les indexateurs de documents pour effectuer la rupture de mot appropriée du texte. Si le morceau n’est ni de type texte ni de type valeur avec des VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource (en)*<br/>
La longueur des caractères du texte source à partir duquel le morceau actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par personnage entre le texte source et le texte dérivé. Une valeur non zéro signifie qu’il n’existe pas de correspondance directe de ce type.

*cwcStartSource (en)*<br/>
Le décalage à partir duquel le texte source pour un morceau dérivé commence dans le morceau source.

*chunkBreakType*<br/>
Le type de rupture qui sépare le morceau précédent du morceau actuel. Les valeurs sont issues de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; sinon un code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsettextvalue"></a><a name="settextvalue"></a>CMFCFilterChunkValueImpl::SetTextValue

Définit la propriété par la clé d’une chaîne Unicode.

```
HRESULT SetTextValue(
    REFPROPERTYKEY pkey,
    LPCTSTR pszValue,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Paramètres

*pkey*<br/>
Spécifie une clé de propriété.

*pszValue*<br/>
Spécifie la valeur du morceau à définir.

*chunkType*<br/>
Les drapeaux indiquent si ce morceau contient un texte de type texte ou une propriété de type valeur. Les valeurs du drapeau sont tirées de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et le sous-langage associés à un morceau de texte. Chunk local est utilisé par les indexateurs de documents pour effectuer la rupture de mot appropriée du texte. Si le morceau n’est ni de type texte ni de type valeur avec des VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource (en)*<br/>
La longueur des caractères du texte source à partir duquel le morceau actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par personnage entre le texte source et le texte dérivé. Une valeur non zéro signifie qu’il n’existe pas de correspondance directe de ce type.

*cwcStartSource (en)*<br/>
Le décalage à partir duquel le texte source pour un morceau dérivé commence dans le morceau source.

*chunkBreakType*<br/>
Le type de rupture qui sépare le morceau précédent du morceau actuel. Les valeurs sont issues de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; sinon un code d’erreur.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
