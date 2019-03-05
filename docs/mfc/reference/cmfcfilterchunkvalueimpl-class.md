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
ms.openlocfilehash: b883d442342dd9fbbd074d9f8fcab76f81ef9864
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264441"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>CMFCFilterChunkValueImpl, classe

Il s’agit d’une classe qui simplifie la logique de paire valeur segment et de propriété.

## <a name="syntax"></a>Syntaxe

```
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|Destruction de l’objet.|
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|Construit l’objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::Clear](#clear)|Efface le ChunkValue.|
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|Copie ce segment dans une structure qui décrit les caractéristiques d’un segment.|
|[CMFCFilterChunkValueImpl::CopyFrom](#copyfrom)|Initialise cette valeur de segment à partir de l’autre valeur.|
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|Récupère le GUID du segment.|
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|Récupère le segment PID (ID de propriété).|
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|Obtient segment type.|
|[CMFCFilterChunkValueImpl::GetString](#getstring)|Récupère la valeur de chaîne.|
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|Récupère la valeur comme un propvariant alloué.|
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|Retourne non alloué (valeur interne) la valeur.|
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|Vérifie si la valeur de cette propriété est valide ou non.|
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|Surchargé. Définit la propriété par clé à une valeur booléenne.|
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|Définit la propriété par clé vers une valeur DWORD.|
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|Définit la propriété par clé en filetime.|
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|Définit la propriété par clé en int64.|
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|Définit la propriété par clé à un entier.|
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|Définit la propriété par clé à la valeur de type LONG.|
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|Définit la propriété par clé à un SystemTime.|
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|Définit la propriété par clé en une chaîne Unicode.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|Une fonction d’assistance qui définit les propriétés communes du segment.|

## <a name="remarks"></a>Notes

Pour utiliser, vous créez simplement une cmfcfilterchunkvalueimpl, classe du type approprié

Exemple :

CMFCFilterChunkValueImpl chunk;

hr = chunk.SetBoolValue(PKEY_IsAttachment, true);

ou

hr = chunk.SetFileTimeValue(PKEY_ItemDate, ftLastModified);

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ATL::IFilterChunkValue`

[CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="clear"></a>  CMFCFilterChunkValueImpl::Clear

Efface le ChunkValue.

```
void Clear();
```

### <a name="remarks"></a>Notes

##  <a name="cmfcfilterchunkvalueimpl"></a>  CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl

Construit l’objet.

```
CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Notes

##  <a name="_dtorcmfcfilterchunkvalueimpl"></a>  CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl

Destruction de l’objet.

```
virtual ~CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Notes

##  <a name="copychunk"></a>  CMFCFilterChunkValueImpl::CopyChunk

Copie ce segment dans une structure qui décrit les caractéristiques d’un segment.

```
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```

### <a name="parameters"></a>Paramètres

*pStatChunk*<br/>
Pointeur vers la valeur de destination qui décrivent les caractéristiques du segment.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; sinon un code d’erreur.

### <a name="remarks"></a>Notes

##  <a name="copyfrom"></a>  CMFCFilterChunkValueImpl::CopyFrom

Initialise cette valeur de segment à partir de l’autre valeur.

```
void CopyFrom (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Paramètres

*pValue*<br/>
Spécifie la valeur source à copier à partir de.

### <a name="remarks"></a>Notes

##  <a name="getchunkguid"></a>  CMFCFilterChunkValueImpl::GetChunkGUID

Récupère le GUID du segment.

```
REFGUID GetChunkGUID() const;
```

### <a name="return-value"></a>Valeur de retour

Une référence à un GUID qui identifie le segment.

### <a name="remarks"></a>Notes

##  <a name="getchunkpid"></a>  CMFCFilterChunkValueImpl::GetChunkPID

Récupère le segment PID (ID de propriété).

```
DWORD GetChunkPID() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur DWORD contenant l’ID de propriété.

### <a name="remarks"></a>Notes

##  <a name="getchunktype"></a>  CMFCFilterChunkValueImpl::GetChunkType

Récupère le type de segment.

```
CHUNKSTATE GetChunkType() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur CHUNKSTATE énuméré, qui spécifie si le segment actuel est une propriété de type texte ou une propriété de type de valeur.

### <a name="remarks"></a>Notes

##  <a name="getstring"></a>  CMFCFilterChunkValueImpl::GetString

Récupère la valeur de chaîne.

```
CString &GetString();
```

### <a name="return-value"></a>Valeur de retour

Chaîne contenant la valeur du segment.

### <a name="remarks"></a>Notes

##  <a name="getvalue"></a>  CMFCFilterChunkValueImpl::GetValue

Récupère la valeur comme un propvariant alloué.

```
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```

### <a name="parameters"></a>Paramètres

*ppPropVariant*<br/>
Lorsque la fonction est retournée, ce paramètre contient la valeur du segment.

### <a name="return-value"></a>Valeur de retour

S_OK si PROPVARIANT a été allouée avec succès et que la valeur de segment a été copiée correctement dans *ppPropVariant*; sinon un code d’erreur.

### <a name="remarks"></a>Notes

##  <a name="getvaluenoalloc"></a>  CMFCFilterChunkValueImpl::GetValueNoAlloc

Retourne la valeur non alloué (valeur interne).

```
PROPVARIANT GetValueNoAlloc ();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de segment actuel.

### <a name="remarks"></a>Notes

##  <a name="isvalid"></a>  CMFCFilterChunkValueImpl::IsValid

Vérifie si la valeur de cette propriété est valide ou non.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la valeur de segment actuel est valide ; Sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="setboolvalue"></a>  CMFCFilterChunkValueImpl::SetBoolValue

Surchargé. Définit la propriété par clé à une valeur booléenne.

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

*bVal*<br/>
Spécifie la valeur du segment à définir.

*chunkType*<br/>
Indicateurs indiquent si ce segment contient un type de texte ou une propriété de type de valeur. Valeurs d’indicateur sont tirés de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et la sous-langue associé à un bloc de texte. Paramètres régionaux de segment sont utilisé par les indexeurs de documents pour effectuer lexicale correcte du texte. Si le segment est de type texte, ni un type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
La longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. La valeur zéro signifie la correspondance de caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’aucune cette correspondance directe n’existe.

*cwcStartSource*<br/>
Le décalage à partir de laquelle le texte source pour un segment dérivé démarre dans le bloc de code source.

*chunkBreakType*<br/>
Le type de saut qui sépare le segment précédent le segment actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; sinon un code d’erreur.

### <a name="remarks"></a>Notes

##  <a name="setchunk"></a>  CMFCFilterChunkValueImpl::SetChunk

Une fonction d’assistance qui définit les propriétés communes du segment.

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
Indicateurs indiquent si ce segment contient un type de texte ou une propriété de type de valeur. Valeurs d’indicateur sont tirés de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et la sous-langue associé à un bloc de texte. Paramètres régionaux de segment sont utilisé par les indexeurs de documents pour effectuer lexicale correcte du texte. Si le segment est de type texte, ni un type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
La longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. La valeur zéro signifie la correspondance de caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’aucune cette correspondance directe n’existe.

*cwcStartSource*<br/>
Le décalage à partir de laquelle le texte source pour un segment dérivé démarre dans le bloc de code source.

*chunkBreakType*<br/>
Le type de saut qui sépare le segment précédent le segment actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; code d’erreur dans le cas contraire.

### <a name="remarks"></a>Notes

##  <a name="setdwordvalue"></a>  CMFCFilterChunkValueImpl::SetDwordValue

Définissez la propriété par clé vers une valeur DWORD.

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

*dwVal*<br/>
Spécifie la valeur du segment à définir.

*chunkType*<br/>
Indicateurs indiquent si ce segment contient un type de texte ou une propriété de type de valeur. Valeurs d’indicateur sont tirés de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et la sous-langue associé à un bloc de texte. Paramètres régionaux de segment sont utilisé par les indexeurs de documents pour effectuer lexicale correcte du texte. Si le segment est de type texte, ni un type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
La longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. La valeur zéro signifie la correspondance de caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’aucune cette correspondance directe n’existe.

*cwcStartSource*<br/>
Le décalage à partir de laquelle le texte source pour un segment dérivé démarre dans le bloc de code source.

*chunkBreakType*<br/>
Le type de saut qui sépare le segment précédent le segment actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; sinon un code d’erreur.

### <a name="remarks"></a>Notes

##  <a name="setfiletimevalue"></a>  CMFCFilterChunkValueImpl::SetFileTimeValue

Définissez la propriété par clé en filetime.

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

*dtVal*<br/>
Spécifie la valeur du segment à définir.

*chunkType*<br/>
Indicateurs indiquent si ce segment contient un type de texte ou une propriété de type de valeur. Valeurs d’indicateur sont tirés de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et la sous-langue associé à un bloc de texte. Paramètres régionaux de segment sont utilisé par les indexeurs de documents pour effectuer lexicale correcte du texte. Si le segment est de type texte, ni un type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
La longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. La valeur zéro signifie la correspondance de caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’aucune cette correspondance directe n’existe.

*cwcStartSource*<br/>
Le décalage à partir de laquelle le texte source pour un segment dérivé démarre dans le bloc de code source.

*chunkBreakType*<br/>
Le type de saut qui sépare le segment précédent le segment actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; sinon un code d’erreur.

### <a name="remarks"></a>Notes

##  <a name="setint64value"></a>  CMFCFilterChunkValueImpl::SetInt64Value

Définissez la propriété par clé en int64.

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

*nVal*<br/>
Spécifie la valeur du segment à définir.

*chunkType*<br/>
Indicateurs indiquent si ce segment contient un type de texte ou une propriété de type de valeur. Valeurs d’indicateur sont tirés de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et la sous-langue associé à un bloc de texte. Paramètres régionaux de segment sont utilisé par les indexeurs de documents pour effectuer lexicale correcte du texte. Si le segment est de type texte, ni un type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
La longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. La valeur zéro signifie la correspondance de caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’aucune cette correspondance directe n’existe.

*cwcStartSource*<br/>
Le décalage à partir de laquelle le texte source pour un segment dérivé démarre dans le bloc de code source.

*chunkBreakType*<br/>
Le type de saut qui sépare le segment précédent le segment actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; sinon un code d’erreur.

### <a name="remarks"></a>Notes

##  <a name="setintvalue"></a>  CMFCFilterChunkValueImpl::SetIntValue

Définissez la propriété par clé à un entier.

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

*nVal*<br/>
Spécifie la valeur du segment à définir.

*chunkType*<br/>
Indicateurs indiquent si ce segment contient un type de texte ou une propriété de type de valeur. Valeurs d’indicateur sont tirés de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et la sous-langue associé à un bloc de texte. Paramètres régionaux de segment sont utilisé par les indexeurs de documents pour effectuer lexicale correcte du texte. Si le segment est de type texte, ni un type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
La longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. La valeur zéro signifie la correspondance de caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’aucune cette correspondance directe n’existe.

*cwcStartSource*<br/>
Le décalage à partir de laquelle le texte source pour un segment dérivé démarre dans le bloc de code source.

*chunkBreakType*<br/>
Le type de saut qui sépare le segment précédent le segment actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; sinon un code d’erreur.

### <a name="remarks"></a>Notes

##  <a name="setlongvalue"></a>  CMFCFilterChunkValueImpl::SetLongValue

Définissez la propriété par clé à la valeur de type LONG.

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

*lVal*<br/>
Spécifie la valeur du segment à définir.

*chunkType*<br/>
Indicateurs indiquent si ce segment contient un type de texte ou une propriété de type de valeur. Valeurs d’indicateur sont tirés de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et la sous-langue associé à un bloc de texte. Paramètres régionaux de segment sont utilisé par les indexeurs de documents pour effectuer lexicale correcte du texte. Si le segment est de type texte, ni un type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
La longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. La valeur zéro signifie la correspondance de caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’aucune cette correspondance directe n’existe.

*cwcStartSource*<br/>
Le décalage à partir de laquelle le texte source pour un segment dérivé démarre dans le bloc de code source.

*chunkBreakType*<br/>
Le type de saut qui sépare le segment précédent le segment actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; sinon un code d’erreur.

### <a name="remarks"></a>Notes

##  <a name="setsystemtimevalue"></a>  CMFCFilterChunkValueImpl::SetSystemTimeValue

Définit la propriété par clé à un SystemTime.

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

*systemTime*<br/>
Spécifie la valeur du segment à définir.

*chunkType*<br/>
Indicateurs indiquent si ce segment contient un type de texte ou une propriété de type de valeur. Valeurs d’indicateur sont tirés de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et la sous-langue associé à un bloc de texte. Paramètres régionaux de segment sont utilisé par les indexeurs de documents pour effectuer lexicale correcte du texte. Si le segment est de type texte, ni un type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
La longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. La valeur zéro signifie la correspondance de caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’aucune cette correspondance directe n’existe.

*cwcStartSource*<br/>
Le décalage à partir de laquelle le texte source pour un segment dérivé démarre dans le bloc de code source.

*chunkBreakType*<br/>
Le type de saut qui sépare le segment précédent le segment actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; sinon un code d’erreur.

### <a name="remarks"></a>Notes

##  <a name="settextvalue"></a>  CMFCFilterChunkValueImpl::SetTextValue

Définit la propriété par clé en une chaîne Unicode.

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
Spécifie la valeur du segment à définir.

*chunkType*<br/>
Indicateurs indiquent si ce segment contient un type de texte ou une propriété de type de valeur. Valeurs d’indicateur sont tirés de l’énumération CHUNKSTATE.

*locale*<br/>
La langue et la sous-langue associé à un bloc de texte. Paramètres régionaux de segment sont utilisé par les indexeurs de documents pour effectuer lexicale correcte du texte. Si le segment est de type texte, ni un type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
La longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. La valeur zéro signifie la correspondance de caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’aucune cette correspondance directe n’existe.

*cwcStartSource*<br/>
Le décalage à partir de laquelle le texte source pour un segment dérivé démarre dans le bloc de code source.

*chunkBreakType*<br/>
Le type de saut qui sépare le segment précédent le segment actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; sinon un code d’erreur.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
