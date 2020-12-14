---
description: 'En savoir plus sur : classe Cmfcfilterchunkvalueimpl,'
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
ms.openlocfilehash: f2db7fdf6d6d24cb906b3190d34310e1f6724194
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265465"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>CMFCFilterChunkValueImpl, classe

Il s’agit d’une classe qui simplifie la logique de paire de valeurs de segment et de propriété.

## <a name="syntax"></a>Syntaxe

```
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cmfcfilterchunkvalueimpl, :: ~ Cmfcfilterchunkvalueimpl,](#_dtorcmfcfilterchunkvalueimpl)|Détruit l’objet.|
|[Cmfcfilterchunkvalueimpl, :: Cmfcfilterchunkvalueimpl,](#cmfcfilterchunkvalueimpl)|Construit l’objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cmfcfilterchunkvalueimpl, :: Clear](#clear)|Efface le ChunkValue.|
|[Cmfcfilterchunkvalueimpl, :: CopyChunk](#copychunk)|Copie ce segment dans une structure décrivant les caractéristiques d’un bloc.|
|[Cmfcfilterchunkvalueimpl, :: CopyFrom](#copyfrom)|Initialise cette valeur de segment à partir de l’autre valeur.|
|[Cmfcfilterchunkvalueimpl, :: GetChunkGUID](#getchunkguid)|Récupère le GUID du bloc.|
|[Cmfcfilterchunkvalueimpl, :: GetChunkPID](#getchunkpid)|Récupère le PID de bloc (ID de propriété).|
|[Cmfcfilterchunkvalueimpl, :: GetChunkType](#getchunktype)|Obtient le type de bloc.|
|[Cmfcfilterchunkvalueimpl, :: GetString](#getstring)|Récupère la valeur de chaîne.|
|[Cmfcfilterchunkvalueimpl, :: GetValue](#getvalue)|Récupère la valeur en tant que PROPVARIANT alloué.|
|[Cmfcfilterchunkvalueimpl, :: GetValueNoAlloc](#getvaluenoalloc)|Retourne une valeur non allouée (valeur interne).|
|[Cmfcfilterchunkvalueimpl, :: IsValid](#isvalid)|Vérifie si cette valeur de propriété est valide ou non.|
|[Cmfcfilterchunkvalueimpl, :: SetBoolValue,](#setboolvalue)|Surchargé. Affecte une valeur booléenne à la propriété par clé.|
|[Cmfcfilterchunkvalueimpl, :: SetDwordValue](#setdwordvalue)|Affecte une valeur DWORD à la propriété par clé.|
|[Cmfcfilterchunkvalueimpl, :: SetFileTimeValue](#setfiletimevalue)|Définit la propriété par clé sur un FILETIME.|
|[Cmfcfilterchunkvalueimpl, :: SetInt64Value](#setint64value)|Définit la propriété par clé sur un Int64.|
|[Cmfcfilterchunkvalueimpl, :: SetIntValue](#setintvalue)|Affecte une valeur int à la propriété par clé.|
|[Cmfcfilterchunkvalueimpl, :: SetLongValue](#setlongvalue)|Définit la propriété par clé sur une valeur LONG.|
|[Cmfcfilterchunkvalueimpl, :: SetSystemTimeValue](#setsystemtimevalue)|Affecte une valeur SystemTime à la propriété par clé.|
|[Cmfcfilterchunkvalueimpl, :: SetTextValue](#settextvalue)|Définit la propriété par clé sur une chaîne Unicode.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[Cmfcfilterchunkvalueimpl, :: SetChunk](#setchunk)|Fonction d’assistance qui définit les propriétés communes du bloc.|

## <a name="remarks"></a>Notes

Pour utiliser, il vous suffit de créer une classe Cmfcfilterchunkvalueimpl, du type approprié.

Exemple :

Segment Cmfcfilterchunkvalueimpl,;

HR = Chunk. SetBoolValue, (PKEY_IsAttachment, true);

ou

HR = Chunk. SetFileTimeValue (PKEY_ItemDate, ftLastModified);

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ATL::IFilterChunkValue`

[Cmfcfilterchunkvalueimpl,](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cmfcfilterchunkvalueimplclear"></a><a name="clear"></a> Cmfcfilterchunkvalueimpl, :: Clear

Efface le ChunkValue.

```cpp
void Clear();
```

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="cmfcfilterchunkvalueimpl"></a> Cmfcfilterchunkvalueimpl, :: Cmfcfilterchunkvalueimpl,

Construit l’objet.

```
CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="_dtorcmfcfilterchunkvalueimpl"></a> Cmfcfilterchunkvalueimpl, :: ~ Cmfcfilterchunkvalueimpl,

Détruit l’objet.

```
virtual ~CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplcopychunk"></a><a name="copychunk"></a> Cmfcfilterchunkvalueimpl, :: CopyChunk

Copie ce segment dans une structure décrivant les caractéristiques d’un bloc.

```
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```

### <a name="parameters"></a>Paramètres

*pStatChunk*<br/>
Pointeur vers une valeur de destination décrivant les caractéristiques du bloc.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplcopyfrom"></a><a name="copyfrom"></a> Cmfcfilterchunkvalueimpl, :: CopyFrom

Initialise cette valeur de segment à partir de l’autre valeur.

```cpp
void CopyFrom (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Paramètres

*pValue*<br/>
Spécifie la valeur source à partir de laquelle effectuer la copie.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplgetchunkguid"></a><a name="getchunkguid"></a> Cmfcfilterchunkvalueimpl, :: GetChunkGUID

Récupère le GUID du bloc.

```
REFGUID GetChunkGUID() const;
```

### <a name="return-value"></a>Valeur renvoyée

Référence à un GUID identifiant le bloc.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplgetchunkpid"></a><a name="getchunkpid"></a> Cmfcfilterchunkvalueimpl, :: GetChunkPID

Récupère le PID de bloc (ID de propriété).

```
DWORD GetChunkPID() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur DWORD contenant l’ID de propriété.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplgetchunktype"></a><a name="getchunktype"></a> Cmfcfilterchunkvalueimpl, :: GetChunkType

Récupère le type de segment.

```
CHUNKSTATE GetChunkType() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur énumérée de CHUNKSTATE, qui spécifie si le segment actuel est une propriété de type texte ou une propriété de type valeur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplgetstring"></a><a name="getstring"></a> Cmfcfilterchunkvalueimpl, :: GetString

Récupère la valeur de chaîne.

```
CString &GetString();
```

### <a name="return-value"></a>Valeur renvoyée

Chaîne contenant la valeur de segment.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplgetvalue"></a><a name="getvalue"></a> Cmfcfilterchunkvalueimpl, :: GetValue

Récupère la valeur en tant que PROPVARIANT alloué.

```
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```

### <a name="parameters"></a>Paramètres

*ppPropVariant*<br/>
Quand la fonction retourne, ce paramètre contient la valeur de segment.

### <a name="return-value"></a>Valeur renvoyée

S_OK si PROPVARIANT a été alloué avec succès et si la valeur de segment a été copiée avec succès vers *ppPropVariant*; Sinon, code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplgetvaluenoalloc"></a><a name="getvaluenoalloc"></a> Cmfcfilterchunkvalueimpl, :: GetValueNoAlloc

Retourne la valeur non allouée (valeur interne).

```
PROPVARIANT GetValueNoAlloc ();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur de segment actuelle.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplisvalid"></a><a name="isvalid"></a> Cmfcfilterchunkvalueimpl, :: IsValid

Vérifie si cette valeur de propriété est valide ou non.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la valeur de segment actuelle est valide ; Sinon, FALSe.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetboolvalue"></a><a name="setboolvalue"></a> Cmfcfilterchunkvalueimpl, :: SetBoolValue,

Surchargé. Affecte une valeur booléenne à la propriété par clé.

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
Spécifie la valeur de segment à définir.

*chunkType*<br/>
Les indicateurs indiquent si ce segment contient un type de texte ou une propriété de type valeur. Les valeurs d’indicateur proviennent de l’énumération CHUNKSTATE.

*locale*<br/>
Langue et sous-langue associée à un segment de texte. Les paramètres régionaux de segment sont utilisés par les indexeurs de documents pour effectuer des césures de mots appropriées. Si le segment n’est ni de type texte, ni de type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
Longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’il n’existe aucune correspondance directe.

*cwcStartSource*<br/>
Offset à partir duquel le texte source d’un segment dérivé commence dans le bloc source.

*chunkBreakType*<br/>
Type d’arrêt qui sépare le bloc précédent du bloc actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetchunk"></a><a name="setchunk"></a> Cmfcfilterchunkvalueimpl, :: SetChunk

Fonction d’assistance qui définit les propriétés communes du bloc.

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
Les indicateurs indiquent si ce segment contient un type de texte ou une propriété de type valeur. Les valeurs d’indicateur proviennent de l’énumération CHUNKSTATE.

*locale*<br/>
Langue et sous-langue associée à un segment de texte. Les paramètres régionaux de segment sont utilisés par les indexeurs de documents pour effectuer des césures de mots appropriées. Si le segment n’est ni de type texte, ni de type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
Longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’il n’existe aucune correspondance directe.

*cwcStartSource*<br/>
Offset à partir duquel le texte source d’un segment dérivé commence dans le bloc source.

*chunkBreakType*<br/>
Type d’arrêt qui sépare le bloc précédent du bloc actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetdwordvalue"></a><a name="setdwordvalue"></a> Cmfcfilterchunkvalueimpl, :: SetDwordValue

Définissez la propriété par clé sur une valeur DWORD.

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
Spécifie la valeur de segment à définir.

*chunkType*<br/>
Les indicateurs indiquent si ce segment contient un type de texte ou une propriété de type valeur. Les valeurs d’indicateur proviennent de l’énumération CHUNKSTATE.

*locale*<br/>
Langue et sous-langue associée à un segment de texte. Les paramètres régionaux de segment sont utilisés par les indexeurs de documents pour effectuer des césures de mots appropriées. Si le segment n’est ni de type texte, ni de type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
Longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’il n’existe aucune correspondance directe.

*cwcStartSource*<br/>
Offset à partir duquel le texte source d’un segment dérivé commence dans le bloc source.

*chunkBreakType*<br/>
Type d’arrêt qui sépare le bloc précédent du bloc actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetfiletimevalue"></a><a name="setfiletimevalue"></a> Cmfcfilterchunkvalueimpl, :: SetFileTimeValue

Définissez la propriété par clé sur FILETIME.

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
Spécifie la valeur de segment à définir.

*chunkType*<br/>
Les indicateurs indiquent si ce segment contient un type de texte ou une propriété de type valeur. Les valeurs d’indicateur proviennent de l’énumération CHUNKSTATE.

*locale*<br/>
Langue et sous-langue associée à un segment de texte. Les paramètres régionaux de segment sont utilisés par les indexeurs de documents pour effectuer des césures de mots appropriées. Si le segment n’est ni de type texte, ni de type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
Longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’il n’existe aucune correspondance directe.

*cwcStartSource*<br/>
Offset à partir duquel le texte source d’un segment dérivé commence dans le bloc source.

*chunkBreakType*<br/>
Type d’arrêt qui sépare le bloc précédent du bloc actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetint64value"></a><a name="setint64value"></a> Cmfcfilterchunkvalueimpl, :: SetInt64Value

Affectez à la propriété la valeur d’une clé Int64.

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
Spécifie la valeur de segment à définir.

*chunkType*<br/>
Les indicateurs indiquent si ce segment contient un type de texte ou une propriété de type valeur. Les valeurs d’indicateur proviennent de l’énumération CHUNKSTATE.

*locale*<br/>
Langue et sous-langue associée à un segment de texte. Les paramètres régionaux de segment sont utilisés par les indexeurs de documents pour effectuer des césures de mots appropriées. Si le segment n’est ni de type texte, ni de type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
Longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’il n’existe aucune correspondance directe.

*cwcStartSource*<br/>
Offset à partir duquel le texte source d’un segment dérivé commence dans le bloc source.

*chunkBreakType*<br/>
Type d’arrêt qui sépare le bloc précédent du bloc actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetintvalue"></a><a name="setintvalue"></a> Cmfcfilterchunkvalueimpl, :: SetIntValue

Affectez la valeur int à la propriété par clé.

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
Spécifie la valeur de segment à définir.

*chunkType*<br/>
Les indicateurs indiquent si ce segment contient un type de texte ou une propriété de type valeur. Les valeurs d’indicateur proviennent de l’énumération CHUNKSTATE.

*locale*<br/>
Langue et sous-langue associée à un segment de texte. Les paramètres régionaux de segment sont utilisés par les indexeurs de documents pour effectuer des césures de mots appropriées. Si le segment n’est ni de type texte, ni de type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
Longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’il n’existe aucune correspondance directe.

*cwcStartSource*<br/>
Offset à partir duquel le texte source d’un segment dérivé commence dans le bloc source.

*chunkBreakType*<br/>
Type d’arrêt qui sépare le bloc précédent du bloc actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetlongvalue"></a><a name="setlongvalue"></a> Cmfcfilterchunkvalueimpl, :: SetLongValue

Définissez la propriété en spécifiant une valeur de clé longue.

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
Spécifie la valeur de segment à définir.

*chunkType*<br/>
Les indicateurs indiquent si ce segment contient un type de texte ou une propriété de type valeur. Les valeurs d’indicateur proviennent de l’énumération CHUNKSTATE.

*locale*<br/>
Langue et sous-langue associée à un segment de texte. Les paramètres régionaux de segment sont utilisés par les indexeurs de documents pour effectuer des césures de mots appropriées. Si le segment n’est ni de type texte, ni de type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
Longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’il n’existe aucune correspondance directe.

*cwcStartSource*<br/>
Offset à partir duquel le texte source d’un segment dérivé commence dans le bloc source.

*chunkBreakType*<br/>
Type d’arrêt qui sépare le bloc précédent du bloc actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsetsystemtimevalue"></a><a name="setsystemtimevalue"></a> Cmfcfilterchunkvalueimpl, :: SetSystemTimeValue

Affecte une valeur SystemTime à la propriété par clé.

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
Spécifie la valeur de segment à définir.

*chunkType*<br/>
Les indicateurs indiquent si ce segment contient un type de texte ou une propriété de type valeur. Les valeurs d’indicateur proviennent de l’énumération CHUNKSTATE.

*locale*<br/>
Langue et sous-langue associée à un segment de texte. Les paramètres régionaux de segment sont utilisés par les indexeurs de documents pour effectuer des césures de mots appropriées. Si le segment n’est ni de type texte, ni de type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
Longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’il n’existe aucune correspondance directe.

*cwcStartSource*<br/>
Offset à partir duquel le texte source d’un segment dérivé commence dans le bloc source.

*chunkBreakType*<br/>
Type d’arrêt qui sépare le bloc précédent du bloc actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, code d’erreur.

### <a name="remarks"></a>Notes

## <a name="cmfcfilterchunkvalueimplsettextvalue"></a><a name="settextvalue"></a> Cmfcfilterchunkvalueimpl, :: SetTextValue

Définit la propriété par clé sur une chaîne Unicode.

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
Spécifie la valeur de segment à définir.

*chunkType*<br/>
Les indicateurs indiquent si ce segment contient un type de texte ou une propriété de type valeur. Les valeurs d’indicateur proviennent de l’énumération CHUNKSTATE.

*locale*<br/>
Langue et sous-langue associée à un segment de texte. Les paramètres régionaux de segment sont utilisés par les indexeurs de documents pour effectuer des césures de mots appropriées. Si le segment n’est ni de type texte, ni de type valeur avec le type de données VT_LPWSTR, VT_LPSTR ou VT_BSTR, ce champ est ignoré.

*cwcLenSource*<br/>
Longueur en caractères du texte source à partir duquel le segment actuel a été dérivé. Une valeur zéro signifie la correspondance caractère par caractère entre le texte source et le texte dérivé. Une valeur différente de zéro signifie qu’il n’existe aucune correspondance directe.

*cwcStartSource*<br/>
Offset à partir duquel le texte source d’un segment dérivé commence dans le bloc source.

*chunkBreakType*<br/>
Type d’arrêt qui sépare le bloc précédent du bloc actuel. Les valeurs proviennent de l’énumération CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, code d’erreur.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)
