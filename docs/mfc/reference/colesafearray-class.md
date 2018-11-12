---
title: COleSafeArray, classe
ms.date: 08/27/2018
f1_keywords:
- COleSafeArray
- AFXDISP/COleSafeArray
- AFXDISP/COleSafeArray::COleSafeArray
- AFXDISP/COleSafeArray::AccessData
- AFXDISP/COleSafeArray::AllocData
- AFXDISP/COleSafeArray::AllocDescriptor
- AFXDISP/COleSafeArray::Attach
- AFXDISP/COleSafeArray::Clear
- AFXDISP/COleSafeArray::Copy
- AFXDISP/COleSafeArray::Create
- AFXDISP/COleSafeArray::CreateOneDim
- AFXDISP/COleSafeArray::Destroy
- AFXDISP/COleSafeArray::DestroyData
- AFXDISP/COleSafeArray::DestroyDescriptor
- AFXDISP/COleSafeArray::Detach
- AFXDISP/COleSafeArray::GetByteArray
- AFXDISP/COleSafeArray::GetDim
- AFXDISP/COleSafeArray::GetElement
- AFXDISP/COleSafeArray::GetElemSize
- AFXDISP/COleSafeArray::GetLBound
- AFXDISP/COleSafeArray::GetOneDimSize
- AFXDISP/COleSafeArray::GetUBound
- AFXDISP/COleSafeArray::Lock
- AFXDISP/COleSafeArray::PtrOfIndex
- AFXDISP/COleSafeArray::PutElement
- AFXDISP/COleSafeArray::Redim
- AFXDISP/COleSafeArray::ResizeOneDim
- AFXDISP/COleSafeArray::UnaccessData
- AFXDISP/COleSafeArray::Unlock
helpviewer_keywords:
- COleSafeArray [MFC], COleSafeArray
- COleSafeArray [MFC], AccessData
- COleSafeArray [MFC], AllocData
- COleSafeArray [MFC], AllocDescriptor
- COleSafeArray [MFC], Attach
- COleSafeArray [MFC], Clear
- COleSafeArray [MFC], Copy
- COleSafeArray [MFC], Create
- COleSafeArray [MFC], CreateOneDim
- COleSafeArray [MFC], Destroy
- COleSafeArray [MFC], DestroyData
- COleSafeArray [MFC], DestroyDescriptor
- COleSafeArray [MFC], Detach
- COleSafeArray [MFC], GetByteArray
- COleSafeArray [MFC], GetDim
- COleSafeArray [MFC], GetElement
- COleSafeArray [MFC], GetElemSize
- COleSafeArray [MFC], GetLBound
- COleSafeArray [MFC], GetOneDimSize
- COleSafeArray [MFC], GetUBound
- COleSafeArray [MFC], Lock
- COleSafeArray [MFC], PtrOfIndex
- COleSafeArray [MFC], PutElement
- COleSafeArray [MFC], Redim
- COleSafeArray [MFC], ResizeOneDim
- COleSafeArray [MFC], UnaccessData
- COleSafeArray [MFC], Unlock
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
ms.openlocfilehash: efffa6057f6322f3de3d9d0bfe050d6d2021d9b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648095"
---
# <a name="colesafearray-class"></a>COleSafeArray, classe

Classe pour utiliser des tableaux de type et de dimension arbitraires.

## <a name="syntax"></a>Syntaxe

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleSafeArray::COleSafeArray](#colesafearray)|Construit un objet `COleSafeArray`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleSafeArray::AccessData](#accessdata)|Récupère un pointeur vers les données de tableau.|
|[COleSafeArray::AllocData](#allocdata)|Alloue de la mémoire pour le tableau.|
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|Alloue de la mémoire pour le descripteur de tableau sécurisé.|
|[COleSafeArray::Attach](#attach)|Donne le contrôle du existant `VARIANT` de tableau à la `COleSafeArray` objet.|
|[COleSafeArray::Clear](#clear)|Libère toutes les données sous-jacentes `VARIANT`.|
|[COleSafeArray::Copy](#copy)|Crée une copie d’un tableau existant.|
|[COleSafeArray::Create](#create)|Crée un tableau sécurisé.|
|[COleSafeArray::CreateOneDim](#createonedim)|Crée une dimension `COleSafeArray` objet.|
|[COleSafeArray::Destroy](#destroy)|Détruit un tableau existant.|
|[COleSafeArray::DestroyData](#destroydata)|Détruit les données dans un tableau sécurisé.|
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|Détruit un descripteur d’un tableau sécurisé.|
|[COleSafeArray::Detach](#detach)|Détache le tableau de type VARIANT à partir du `COleSafeArray` (afin que les données ne seront pas libérées) de l’objet.|
|[COleSafeArray::GetByteArray](#getbytearray)|Copie le contenu du tableau sécurisé dans un [CByteArray](../../mfc/reference/cbytearray-class.md).|
|[COleSafeArray::GetDim](#getdim)|Retourne le nombre de dimensions du tableau.|
|[COleSafeArray::GetElement](#getelement)|Récupère un élément unique du tableau sécurisé.|
|[COleSafeArray::GetElemSize](#getelemsize)|Retourne la taille, en octets, d’un seul élément dans un tableau sécurisé.|
|[COleSafeArray::GetLBound](#getlbound)|Retourne la limite inférieure d’une dimension d’un tableau sécurisé.|
|[COleSafeArray::GetOneDimSize](#getonedimsize)|Retourne le nombre d’éléments dans la dimension `COleSafeArray` objet.|
|[COleSafeArray::GetUBound](#getubound)|Retourne la limite supérieure d’une dimension d’un tableau sécurisé.|
|[COleSafeArray::Lock](#lock)|Incrémente le nombre de verrous d’un tableau et place un pointeur vers les données de tableau dans le descripteur de tableau.|
|[COleSafeArray::PtrOfIndex](#ptrofindex)|Retourne un pointeur vers l’élément indexé.|
|[COleSafeArray::PutElement](#putelement)|Affecte un élément unique dans le tableau.|
|[COleSafeArray::Redim](#redim)|Modifie la limite moins significative (le plus à droite) d’un tableau sécurisé.|
|[COleSafeArray::ResizeOneDim](#resizeonedim)|Modifie le nombre d’éléments dans une dimension `COleSafeArray` objet.|
|[COleSafeArray::UnaccessData](#unaccessdata)|Décrémente le verrou compter d’un tableau et invalide le pointeur récupéré par `AccessData`.|
|[COleSafeArray::Unlock](#unlock)|Décrémente le nombre de verrous d’un tableau afin qu’elle peut être libérée ou redimensionnée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[COleSafeArray::operator LPCVARIANT](#operator_lpcvariant)|Accède à sous-jacent `VARIANT` structure de le `COleSafeArray` objet.|
|[COleSafeArray::operator LPVARIANT](#operator_lpvariant)|Accède à sous-jacent `VARIANT` structure de le `COleSafeArray` objet.|
|[COleSafeArray::operator =](#operator_eq)|Copie les valeurs dans un `COleSafeArray` objet (`SAFEARRAY`, `VARIANT`, `COleVariant`, ou `COleSafeArray` tableau).|
|[COleSafeArray::operator ==](#operator_eq_eq)|Compare deux tableaux variants (`SAFEARRAY`, `VARIANT`, `COleVariant`, ou `COleSafeArray` tableaux).|
|[COleSafeArray::operator &lt;&lt;](#operator_lt_lt)|Génère le contenu d’un `COleSafeArray` objet dans le contexte de dump.|

## <a name="remarks"></a>Notes

`COleSafeArray` dérive le OLE `VARIANT` structure. OLE `SAFEARRAY` fonctions membres sont disponibles via `COleSafeArray`, ainsi que comme un ensemble de fonctions membres spécialement conçue pour les tableaux unidimensionnels d’octets.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

##  <a name="accessdata"></a>  COleSafeArray::AccessData

Récupère un pointeur vers les données de tableau.

```
void AccessData(void** ppvData);
```

### <a name="parameters"></a>Paramètres

*ppvData*<br/>
Pointeur vers un pointeur vers les données de tableau.

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

##  <a name="allocdata"></a>  COleSafeArray::AllocData

Alloue la mémoire pour un tableau sécurisé.

```
void AllocData();
```

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="allocdescriptor"></a>  COleSafeArray::AllocDescriptor

Alloue de la mémoire pour le descripteur d’un tableau sécurisé.

```
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>Paramètres

*dwDims*<br/>
Nombre de dimensions dans le tableau sécurisé.

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="attach"></a>  COleSafeArray::Attach

Permet de contrôler les données dans une existante `VARIANT` de tableau à la `COleSafeArray` objet.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Paramètres

*varSrc*<br/>
Objet `VARIANT`. Le *varSrc* le paramètre doit avoir le VARTYPE [VT_ARRAY](/windows/desktop/api/wtypes/ne-wtypes-varenum).

### <a name="remarks"></a>Notes

La source `VARIANT`du type a la valeur VT_EMPTY. Cette fonction efface les données de tableau en cours, le cas échéant.

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleSafeArray::AccessData](#accessdata).

##  <a name="clear"></a>  COleSafeArray::Clear

Efface le tableau sécurisé.

```
void Clear();
```

### <a name="remarks"></a>Notes

La fonction efface un tableau sécurisé en définissant le `VARTYPE` de l’objet avec la valeur VT_EMPTY. Le contenu actuel est libéré et que le tableau est libéré.

##  <a name="colesafearray"></a>  COleSafeArray::COleSafeArray

Construit un objet `COleSafeArray`.

```
COleSafeArray();

COleSafeArray(
    const SAFEARRAY& saSrc,
    VARTYPE vtSrc);

COleSafeArray(
    LPCSAFEARRAY pSrc,
    VARTYPE vtSrc);

COleSafeArray(const COleSafeArray& saSrc);
COleSafeArray(const VARIANT& varSrc);
  COleSafeArray(LPCVARIANT pSrc);
COleSafeArray(const COleVariant& varSrc);
```

### <a name="parameters"></a>Paramètres

*saSrc*<br/>
Un existant `COleSafeArray` objet ou `SAFEARRAY` doit être copié dans le nouveau `COleSafeArray` objet.

*vtSrc*<br/>
VARTYPE du nouveau `COleSafeArray` objet.

*psaSrc*<br/>
Un pointeur vers un `SAFEARRAY` doit être copié dans le nouveau `COleSafeArray` objet.

*varSrc*<br/>
Un existant `VARIANT` ou `COleVariant` objet doit être copié dans le nouveau `COleSafeArray` objet.

*pSrc*<br/>
Un pointeur vers un `VARIANT` objet doit être copié dans le nouveau `COleSafeArray` objet.

### <a name="remarks"></a>Notes

Toutes ces constructeurs créent `COleSafeArray` objets. S’il n’existe aucun paramètre, vide `COleSafeArray` objet est créé (VT_EMPTY). Si le `COleSafeArray` est copié à partir d’un autre tableau dont VARTYPE est implicitement connu (un `COleSafeArray`, `COleVariant`, ou `VARIANT`), VARTYPE du tableau source est conservé et ne doivent pas être spécifié. Si le `COleSafeArray` est copié à partir d’un autre tableau dont VARTYPE n’est pas connu (`SAFEARRAY`), VARTYPE doit être spécifié dans le *vtSrc* paramètre.

En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="copy"></a>  COleSafeArray::Copy

Crée une copie d’un tableau sécurisé existant.

```
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>Paramètres

*ppsa*<br/>
Pointeur vers un emplacement dans lequel retourner le nouveau descripteur de tableau.

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="create"></a>  COleSafeArray::Create

Alloue et initialise les données pour le tableau.

```
void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    DWORD* rgElements);

void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    SAFEARRAYBOUND* rgsabounds);
```

### <a name="parameters"></a>Paramètres

*vtSrc*<br/>
Le type de base du tableau (autrement dit, VARTYPE de chaque élément du tableau). VARTYPE est limité à un sous-ensemble des types variants. Ni le VT_ARRAY ni l’indicateur VT_BYREF peut être définie. VT_EMPTY et VT_NULL ne sont pas des types de base valides pour le tableau. Tous les autres types sont autorisés.

*dwDims*<br/>
Nombre de dimensions dans le tableau. Cela peut être modifié une fois que le tableau est créé avec [Redim](#redim).

*rgElements*<br/>
Pointeur vers un tableau du nombre d’éléments pour chaque dimension du tableau.

*rgsabounds*<br/>
Pointeur vers un vecteur de limites (une pour chaque dimension) à allouer pour le tableau.

### <a name="remarks"></a>Notes

Cette fonction efface les données de tableau en cours si nécessaire. En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="createonedim"></a>  COleSafeArray::CreateOneDim

Crée un nouveau unidimensionnel `COleSafeArray` objet.

```
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>Paramètres

*vtSrc*<br/>
Le type de base du tableau (autrement dit, VARTYPE de chaque élément du tableau).

*dwElements*<br/>
Nombre d’éléments dans le tableau. Cela peut être modifié une fois que le tableau est créé avec [ResizeOneDim](#resizeonedim).

*pvSrcData*<br/>
Pointeur vers les données à copier dans le tableau.

*nLBound*<br/>
La limite inférieure du tableau.

### <a name="remarks"></a>Notes

La fonction alloue et initialise les données pour le tableau, en copiant les données spécifiées si le pointeur *pvSrcData* n’est pas NULL.

En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

##  <a name="destroy"></a>  COleSafeArray::Destroy

Détruit un descripteur de tableau existant et toutes les données dans le tableau.

```
void Destroy();
```

### <a name="remarks"></a>Notes

Si les objets sont stockés dans le tableau, chaque objet est libéré. En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="destroydata"></a>  COleSafeArray::DestroyData

Détruit toutes les données dans un tableau sécurisé.

```
void DestroyData();
```

### <a name="remarks"></a>Notes

Si les objets sont stockés dans le tableau, chaque objet est libéré. En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="destroydescriptor"></a>  COleSafeArray::DestroyDescriptor

Détruit un descripteur d’un tableau sécurisé.

```
void DestroyDescriptor();
```

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="detach"></a>  COleSafeArray::Detach

Détache le `VARIANT` données à partir de la `COleSafeArray` objet.

```
VARIANT Detach();
```

### <a name="return-value"></a>Valeur de retour

Sous-jacent `VARIANT` valeur dans le `COleSafeArray` objet.

### <a name="remarks"></a>Notes

La fonction détache les données dans un tableau sécurisé en définissant le VARTYPE de l’objet avec la valeur VT_EMPTY. Il revient l’appelant de libérer le tableau en appelant la fonction Windows [VariantClear](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantclear).

En cas d’erreur, la fonction lève un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleSafeArray::PutElement](#putelement).

##  <a name="getbytearray"></a>  COleSafeArray::GetByteArray

Copie le contenu du tableau sécurisé dans un `CByteArray`.

```
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>Paramètres

*Octets*<br/>
Une référence à un [CByteArray](../../mfc/reference/cbytearray-class.md) objet.

##  <a name="getdim"></a>  COleSafeArray::GetDim

Retourne le nombre de dimensions dans le `COleSafeArray` objet.

```
DWORD GetDim();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de dimensions dans le tableau sécurisé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="getelement"></a>  COleSafeArray::GetElement

Récupère un élément unique du tableau sécurisé.

```
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Paramètres

*rgIndices*<br/>
Pointeur vers un tableau d'index pour chaque dimension du tableau.

*pvData*<br/>
Pointeur vers l’emplacement pour placer l’élément du tableau.

### <a name="remarks"></a>Notes

Cette fonction appelle automatiquement les fonctions windows `SafeArrayLock` et `SafeArrayUnlock` avant et après avoir récupéré l’élément. Si l’élément de données est une chaîne, un objet ou un variant, la fonction copie l’élément de la façon correcte. Le paramètre *pvData* doit pointer vers une grande mémoire tampon insuffisante pour contenir l’élément.

En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

##  <a name="getelemsize"></a>  COleSafeArray::GetElemSize

Récupère la taille d’un élément dans un `COleSafeArray` objet.

```
DWORD GetElemSize();
```

### <a name="return-value"></a>Valeur de retour

La taille, en octets, des éléments d’un tableau sécurisé.

##  <a name="getlbound"></a>  COleSafeArray::GetLBound

Retourne la limite inférieure d’une dimension d’un `COleSafeArray` objet.

```
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>Paramètres

*dwDim*<br/>
La dimension de tableau pour lequel obtenir la limite inférieure.

*pLBound*<br/>
Pointeur vers l’emplacement pour retourner la limite inférieure.

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

##  <a name="getonedimsize"></a>  COleSafeArray::GetOneDimSize

Retourne le nombre d’éléments dans la dimension `COleSafeArray` objet.

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans le tableau unidimensionnel de sécurité.

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleSafeArray::CreateOneDim](#createonedim).

##  <a name="getubound"></a>  COleSafeArray::GetUBound

Retourne la limite supérieure d’une dimension d’un tableau sécurisé.

```
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>Paramètres

*dwDim*<br/>
La dimension de tableau pour lequel obtenir la limite supérieure.

*pUBound*<br/>
Pointeur vers l’emplacement pour retourner la limite supérieure.

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

##  <a name="lock"></a>  COleSafeArray::Lock

Incrémente le nombre de verrous d’un tableau et le place un pointeur vers les données de tableau dans le descripteur de tableau.

```
void Lock();
```

### <a name="remarks"></a>Notes

En cas d’erreur, elle lève une [COleException](../../mfc/reference/coleexception-class.md).

Le pointeur dans le descripteur de tableau est valide jusqu'à ce que `Unlock` est appelée. Les appels à `Lock` peuvent être imbriqués ; un nombre égal d’appels à `Unlock` sont requis.

Un tableau ne peut pas être supprimé lorsqu’il est verrouillé.

##  <a name="operator_lpcvariant"></a>  COleSafeArray::operator LPCVARIANT

Appeler cet opérateur de cast pour accéder à sous-jacent `VARIANT` structure pour ce `COleSafeArray` objet.

```
operator LPCVARIANT() const;
```

##  <a name="operator_lpvariant"></a>  COleSafeArray::operator LPVARIANT

Appeler cet opérateur de cast pour accéder à sous-jacent `VARIANT` structure pour ce `COleSafeArray` objet.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Notes

Notez que si vous modifiez la valeur dans le `VARIANT` structure accédé par le pointeur retourné par cette fonction modifie la valeur de ce `COleSafeArray` objet.

##  <a name="operator_eq"></a>  COleSafeArray::operator =

Ces opérateurs d’assignation surchargés copier la valeur source dans cette `COleSafeArray` objet.

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
  COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>Notes

Une brève description de chaque opérateur suit :

- **opérateur = (** *saSrc* **)** copie existante `COleSafeArray` objet dans cet objet.

- **opérateur = (** *varSrc* **)** copie existante `VARIANT` ou `COleVariant` tableau dans cet objet.

- **opérateur = (** *pSrc* **)** Copies le `VARIANT` objet tableau accédé par *pSrc* dans cet objet.

##  <a name="operator_eq_eq"></a>  COleSafeArray::operator ==

Cet opérateur compare deux tableaux (`SAFEARRAY`, `VARIANT`, `COleVariant`, ou `COleSafeArray` tableaux) et retourne zéro si elles sont égales ; sinon, 0.

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>Notes

Deux tableaux sont égaux s’ils ont le même nombre de dimensions, de taille égale dans chaque dimension et un élément égal.

##  <a name="operator_lt_lt"></a>  COleSafeArray::operator &lt;&lt;

Le `COleSafeArray` insertion (<<) prend en charge l’opérateur dump et de stockage de diagnostic un `COleSafeArray` objet dans une archive.

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

##  <a name="ptrofindex"></a>  COleSafeArray::PtrOfIndex

Retourne un pointeur vers l’élément spécifié par les valeurs d’index.

```
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>Paramètres

*rgIndices*<br/>
Un tableau de valeurs d’index qui identifient un élément du tableau. Tous les index de l’élément doivent être spécifiés.

*ppvData*<br/>
De retour, pointeur vers l’élément identifié par les valeurs de *rgIndices*.

##  <a name="putelement"></a>  COleSafeArray::PutElement

Affecte un élément unique dans le tableau.

```
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Paramètres

*rgIndices*<br/>
Pointeur vers un tableau d'index pour chaque dimension du tableau.

*pvData*<br/>
Pointeur vers les données à affecter au groupe. Types variant VT_DISPATCH VT_UNKNOWN et VT_BSTR sont des pointeurs et ne nécessitent pas d’un autre niveau d’indirection.

### <a name="remarks"></a>Notes

Cette fonction appelle automatiquement les fonctions Windows [SafeArrayLock](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraylock) et [SafeArrayUnlock](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearrayunlock) avant et après l’affectation de l’élément. Si l'élément de données est une chaîne, un objet ou un variant, la fonction le copie correctement ; si l'élément existant est une chaîne, un objet ou un variant, il est effacé correctement.

Il est à noter qu'un tableau peut avoir plusieurs verrous. Il est donc possible de placer des éléments dans un tableau pendant que le tableau est verrouillé par d'autres opérations.

En cas d’erreur, la fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

##  <a name="redim"></a>  COleSafeArray::Redim

Modifie la limite moins significative (le plus à droite) d’un tableau sécurisé.

```
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>Paramètres

*psaboundNew*<br/>
Pointeur vers un nouveau tableau sécurisé lié structure contenant le nouveau tableau lié. Uniquement la dimension la moins significative d’un tableau peut être modifiée.

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève un [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="resizeonedim"></a>  COleSafeArray::ResizeOneDim

Modifie le nombre d’éléments dans une dimension `COleSafeArray` objet.

```
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>Paramètres

*dwElements*<br/>
Nombre d’éléments dans le tableau unidimensionnel de sécurité.

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleSafeArray::CreateOneDim](#createonedim).

##  <a name="unaccessdata"></a>  COleSafeArray::UnaccessData

Décrémente le verrou compter d’un tableau et invalide le pointeur récupéré par `AccessData`.

```
void UnaccessData();
```

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleSafeArray::AccessData](#accessdata).

##  <a name="unlock"></a>  COleSafeArray::Unlock

Décrémente le nombre de verrous d’un tableau afin qu’elle peut être libérée ou redimensionnée.

```
void Unlock();
```

### <a name="remarks"></a>Notes

Cette fonction est appelée une fois l’accès aux données dans un tableau est terminé. En cas d’erreur, elle lève une [COleException](../../mfc/reference/coleexception-class.md).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleVariant, classe](../../mfc/reference/colevariant-class.md)<br/>
[CRecordset, classe](../../mfc/reference/crecordset-class.md)<br/>
[CDatabase, classe](../../mfc/reference/cdatabase-class.md)<br/>
