---
description: 'En savoir plus sur : classe COleSafeArray'
title: COleSafeArray, classe
ms.date: 08/29/2019
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
ms.openlocfilehash: 6c33f58f71167c492883a25b05fce6bb8fb09916
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226699"
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
|[COleSafeArray :: COleSafeArray](#colesafearray)|Construit un objet `COleSafeArray`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleSafeArray :: AccessData](#accessdata)|Récupère un pointeur vers les données du tableau.|
|[COleSafeArray :: AllocData](#allocdata)|Alloue de la mémoire pour le tableau.|
|[COleSafeArray :: AllocDescriptor](#allocdescriptor)|Alloue de la mémoire pour le descripteur de tableau sécurisé.|
|[COleSafeArray :: Attach](#attach)|Donne le contrôle du `VARIANT` tableau existant à l' `COleSafeArray` objet.|
|[COleSafeArray :: Clear](#clear)|Libère toutes les données dans le sous-jacent `VARIANT` .|
|[COleSafeArray :: Copy](#copy)|Crée une copie d’un tableau existant.|
|[COleSafeArray :: Create](#create)|Crée un tableau sécurisé.|
|[COleSafeArray :: CreateOneDim](#createonedim)|Crée un objet unidimensionnel `COleSafeArray` .|
|[COleSafeArray ::D estroy](#destroy)|Détruit un tableau existant.|
|[COleSafeArray ::D estroyData](#destroydata)|Détruit des données dans un tableau sécurisé.|
|[COleSafeArray ::D estroyDescriptor](#destroydescriptor)|Détruit un descripteur d’un tableau sécurisé.|
|[COleSafeArray ::D Etach](#detach)|Détache le tableau de VARIANT de l' `COleSafeArray` objet (afin que les données ne soient pas libérées).|
|[COleSafeArray :: GetByteArray](#getbytearray)|Copie le contenu du tableau sécurisé dans un [CByteArray](../../mfc/reference/cbytearray-class.md).|
|[COleSafeArray :: GetDim](#getdim)|Retourne le nombre de dimensions du tableau.|
|[COleSafeArray :: GetElement](#getelement)|Récupère un élément unique du tableau sécurisé.|
|[COleSafeArray :: GetElemSize](#getelemsize)|Retourne la taille, en octets, d’un élément dans un tableau sécurisé.|
|[COleSafeArray :: GetLBound](#getlbound)|Retourne la limite inférieure d’une dimension d’un tableau sécurisé.|
|[COleSafeArray :: GetOneDimSize](#getonedimsize)|Retourne le nombre d’éléments dans l’objet unidimensionnel `COleSafeArray` .|
|[COleSafeArray :: GetUBound](#getubound)|Retourne la limite supérieure d’une dimension d’un tableau sécurisé.|
|[COleSafeArray :: Lock](#lock)|Incrémente le nombre de verrous d’un tableau et place un pointeur vers les données du tableau dans le descripteur de tableau.|
|[COleSafeArray ::P trOfIndex](#ptrofindex)|Retourne un pointeur vers l’élément indexé.|
|[COleSafeArray ::P utElement](#putelement)|Affecte un élément unique dans le tableau.|
|[COleSafeArray :: ReDim](#redim)|Modifie la liaison la moins significative (la plus à droite) d’un tableau sécurisé.|
|[COleSafeArray :: ResizeOneDim](#resizeonedim)|Modifie le nombre d’éléments dans un objet unidimensionnel `COleSafeArray` .|
|[COleSafeArray :: UnaccessData](#unaccessdata)|Décrémente le nombre de verrous d’un tableau et invalide le pointeur récupéré par `AccessData` .|
|[COleSafeArray :: Unlock](#unlock)|Décrémente le nombre de verrous d’un tableau afin qu’il puisse être libéré ou redimensionné.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[COleSafeArray :: Operator LPCVARIANT](#operator_lpcvariant)|Accède à la structure sous-jacente `VARIANT` de l' `COleSafeArray` objet.|
|[COleSafeArray :: Operator LPVARIANT](#operator_lpvariant)|Accède à la structure sous-jacente `VARIANT` de l' `COleSafeArray` objet.|
|[COleSafeArray :: Operator =](#operator_eq)|Copie des valeurs dans un `COleSafeArray` objet ( `SAFEARRAY` tableau,, `VARIANT` `COleVariant` ou `COleSafeArray` ).|
|[COleSafeArray :: Operator = =](#operator_eq_eq)|Compare deux tableaux de variants `SAFEARRAY` ( `VARIANT` tableaux,, `COleVariant` ou `COleSafeArray` ).|
|[COleSafeArray ::, opérateur &lt;&lt;](#operator_lt_lt)|Renvoie le contenu d’un `COleSafeArray` objet dans le contexte de vidage.|

## <a name="remarks"></a>Notes

`COleSafeArray` dérive de la `VARIANT` structure OLE. Les `SAFEARRAY` fonctions membres OLE sont disponibles par le biais de `COleSafeArray` , ainsi qu’un ensemble de fonctions membres spécifiquement conçues pour les tableaux unidimensionnels d’octets.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="colesafearrayaccessdata"></a><a name="accessdata"></a> COleSafeArray :: AccessData

Récupère un pointeur vers les données du tableau.

```cpp
void AccessData(void** ppvData);
```

### <a name="parameters"></a>Paramètres

*ppvData*<br/>
Pointeur vers un pointeur vers les données du tableau.

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

## <a name="colesafearrayallocdata"></a><a name="allocdata"></a> COleSafeArray :: AllocData

Alloue de la mémoire pour un tableau sécurisé.

```cpp
void AllocData();
```

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearrayallocdescriptor"></a><a name="allocdescriptor"></a> COleSafeArray :: AllocDescriptor

Alloue de la mémoire pour le descripteur d’un tableau sécurisé.

```cpp
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>Paramètres

*dwDims*<br/>
Nombre de dimensions dans le tableau sécurisé.

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearrayattach"></a><a name="attach"></a> COleSafeArray :: Attach

Donne le contrôle des données d’un `VARIANT` tableau existant à l' `COleSafeArray` objet.

```cpp
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Paramètres

*varSrc*<br/>
Objet `VARIANT`. Le paramètre *varSrc* doit avoir la [VT_ARRAY](/windows/win32/api/wtypes/ne-wtypes-varenum)VarType.

### <a name="remarks"></a>Notes

Le `VARIANT` type de la source est défini sur VT_EMPTY. Cette fonction efface les données actuelles du tableau, le cas échéant.

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleSafeArray :: AccessData](#accessdata).

## <a name="colesafearrayclear"></a><a name="clear"></a> COleSafeArray :: Clear

Efface le tableau sécurisé.

```cpp
void Clear();
```

### <a name="remarks"></a>Notes

La fonction efface un tableau sécurisé en affectant `VARTYPE` à l’objet de la valeur VT_EMPTY. Le contenu actuel est libéré et le tableau est libéré.

## <a name="colesafearraycolesafearray"></a><a name="colesafearray"></a> COleSafeArray :: COleSafeArray

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
Objet existant `COleSafeArray` ou `SAFEARRAY` à copier dans le nouvel `COleSafeArray` objet.

*vtSrc*<br/>
VARTYPE du nouvel `COleSafeArray` objet.

*psaSrc*<br/>
Pointeur vers un `SAFEARRAY` à copier dans le nouvel `COleSafeArray` objet.

*varSrc*<br/>
`VARIANT`Objet ou existant `COleVariant` à copier dans le nouvel `COleSafeArray` objet.

*pSrc*<br/>
Pointeur vers un `VARIANT` objet à copier dans le nouvel `COleSafeArray` objet.

### <a name="remarks"></a>Notes

Tous ces constructeurs créent des `COleSafeArray` objets. S’il n’y a aucun paramètre, un `COleSafeArray` objet vide est créé (VT_EMPTY). Si le `COleSafeArray` est copié à partir d’un autre tableau dont le VarType est connu implicitement (a `COleSafeArray` , `COleVariant` ou `VARIANT` ), le VarType du tableau source est conservé et n’a pas besoin d’être spécifié. Si le `COleSafeArray` est copié à partir d’un autre tableau dont VarType n’est pas connu ( `SAFEARRAY` ), VarType doit être spécifié dans le paramètre *vtSrc* .

En cas d’erreur, la fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraycopy"></a><a name="copy"></a> COleSafeArray :: Copy

Crée une copie d’un tableau sécurisé existant.

```cpp
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>Paramètres

*ppsa*<br/>
Pointeur vers un emplacement dans lequel retourner le nouveau descripteur de tableau.

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraycreate"></a><a name="create"></a> COleSafeArray :: Create

Alloue et initialise les données pour le tableau.

```cpp
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
Type de base du tableau (autrement dit, le VARTYPE de chaque élément du tableau). VARTYPE est limité à un sous-ensemble des types variant. Ni la VT_ARRAY ni l’indicateur VT_BYREF ne peuvent être définis. VT_EMPTY et VT_NULL ne sont pas des types de base valides pour le tableau. Tous les autres types sont légaux.

*dwDims*<br/>
Nombre de dimensions dans le tableau. Cela peut être modifié après la création du tableau avec [ReDim](#redim).

*rgElements*<br/>
Pointeur vers un tableau du nombre d’éléments pour chaque dimension du tableau.

*rgsabounds*<br/>
Pointeur vers un vecteur de limites (une pour chaque dimension) à allouer pour le tableau.

### <a name="remarks"></a>Notes

Cette fonction efface les données actuelles du tableau, si nécessaire. En cas d’erreur, la fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraycreateonedim"></a><a name="createonedim"></a> COleSafeArray :: CreateOneDim

Crée un nouvel objet unidimensionnel `COleSafeArray` .

```cpp
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>Paramètres

*vtSrc*<br/>
Type de base du tableau (autrement dit, le VARTYPE de chaque élément du tableau).

*dwElements*<br/>
Nombre d’éléments dans le tableau. Cela peut être modifié après la création du tableau avec [ResizeOneDim](#resizeonedim).

*pvSrcData*<br/>
Pointeur vers les données à copier dans le tableau.

*nLBound*<br/>
Limite inférieure du tableau.

### <a name="remarks"></a>Notes

La fonction alloue et initialise les données pour le tableau, en copiant les données spécifiées si le pointeur *pvSrcData* n’est pas null.

En cas d’erreur, la fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

## <a name="colesafearraydestroy"></a><a name="destroy"></a> COleSafeArray ::D estroy

Détruit un descripteur de tableau existant et toutes les données dans le tableau.

```cpp
void Destroy();
```

### <a name="remarks"></a>Notes

Si les objets sont stockés dans le tableau, chaque objet est libéré. En cas d’erreur, la fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraydestroydata"></a><a name="destroydata"></a> COleSafeArray ::D estroyData

Détruit toutes les données d’un tableau sécurisé.

```cpp
void DestroyData();
```

### <a name="remarks"></a>Notes

Si les objets sont stockés dans le tableau, chaque objet est libéré. En cas d’erreur, la fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraydestroydescriptor"></a><a name="destroydescriptor"></a> COleSafeArray ::D estroyDescriptor

Détruit un descripteur d’un tableau sécurisé.

```cpp
void DestroyDescriptor();
```

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraydetach"></a><a name="detach"></a> COleSafeArray ::D Etach

Détache les `VARIANT` données de l' `COleSafeArray` objet.

```
VARIANT Detach();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur sous-jacente `VARIANT` dans l' `COleSafeArray` objet.

### <a name="remarks"></a>Notes

La fonction détache les données dans un tableau sécurisé en affectant à VARTYPE de l’objet la valeur VT_EMPTY. Il incombe à l’appelant de libérer le tableau en appelant la fonction Windows [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear).

En cas d’erreur, la fonction lève une [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

  Consultez l’exemple pour [COleSafeArray ::P utelement](#putelement).

## <a name="colesafearraygetbytearray"></a><a name="getbytearray"></a> COleSafeArray :: GetByteArray

Copie le contenu du tableau sécurisé dans un `CByteArray` .

```cpp
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>Paramètres

*bytes*<br/>
Référence à un objet [CByteArray](../../mfc/reference/cbytearray-class.md) .

## <a name="colesafearraygetdim"></a><a name="getdim"></a> COleSafeArray :: GetDim

Retourne le nombre de dimensions dans l' `COleSafeArray` objet.

```
DWORD GetDim();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de dimensions dans le tableau sécurisé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraygetelement"></a><a name="getelement"></a> COleSafeArray :: GetElement

Récupère un élément unique du tableau sécurisé.

```cpp
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Paramètres

*rgIndices*<br/>
Pointeur vers un tableau d'index pour chaque dimension du tableau.

*pvData*<br/>
Pointeur vers l’emplacement où placer l’élément du tableau.

### <a name="remarks"></a>Notes

Cette fonction appelle automatiquement les fonctions Windows `SafeArrayLock` et `SafeArrayUnlock` avant et après la récupération de l’élément. Si l’élément de données est une chaîne, un objet ou une variante, la fonction copie l’élément de la manière correcte. Le paramètre *pvData* doit pointer vers une mémoire tampon suffisamment grande pour contenir l’élément.

En cas d’erreur, la fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

## <a name="colesafearraygetelemsize"></a><a name="getelemsize"></a> COleSafeArray :: GetElemSize

Récupère la taille d’un élément dans un `COleSafeArray` objet.

```
DWORD GetElemSize();
```

### <a name="return-value"></a>Valeur renvoyée

Taille, en octets, des éléments d’un tableau sécurisé.

## <a name="colesafearraygetlbound"></a><a name="getlbound"></a> COleSafeArray :: GetLBound

Retourne la limite inférieure d’une dimension d’un `COleSafeArray` objet.

```cpp
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>Paramètres

*dwDim*<br/>
Dimension du tableau pour laquelle obtenir la limite inférieure.

*pLBound*<br/>
Pointeur vers l’emplacement où retourner la limite inférieure.

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève une [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

## <a name="colesafearraygetonedimsize"></a><a name="getonedimsize"></a> COleSafeArray :: GetOneDimSize

Retourne le nombre d’éléments dans l’objet unidimensionnel `COleSafeArray` .

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments dans le tableau sécurisé unidimensionnel.

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleSafeArray :: CreateOneDim](#createonedim).

## <a name="colesafearraygetubound"></a><a name="getubound"></a> COleSafeArray :: GetUBound

Retourne la limite supérieure d’une dimension d’un tableau sécurisé.

```cpp
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>Paramètres

*dwDim*<br/>
Dimension du tableau pour laquelle obtenir la limite supérieure.

*pUBound*<br/>
Pointeur vers l’emplacement où retourner la limite supérieure.

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève une [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

## <a name="colesafearraylock"></a><a name="lock"></a> COleSafeArray :: Lock

Incrémente le nombre de verrous d’un tableau et place un pointeur vers les données du tableau dans le descripteur de tableau.

```cpp
void Lock();
```

### <a name="remarks"></a>Notes

En cas d’erreur, elle lève une [COleException](../../mfc/reference/coleexception-class.md).

Le pointeur dans le descripteur de tableau est valide jusqu’à ce que `Unlock` soit appelé. Les appels à `Lock` peuvent être imbriqués ; un nombre égal d’appels à `Unlock` sont requis.

Un tableau ne peut pas être supprimé tant qu’il est verrouillé.

## <a name="colesafearrayoperator-lpcvariant"></a><a name="operator_lpcvariant"></a> COleSafeArray :: Operator LPCVARIANT

Appelez cet opérateur de cast pour accéder à la structure sous-jacente `VARIANT` de cet `COleSafeArray` objet.

```
operator LPCVARIANT() const;
```

## <a name="colesafearrayoperator-lpvariant"></a><a name="operator_lpvariant"></a> COleSafeArray :: Operator LPVARIANT

Appelez cet opérateur de cast pour accéder à la structure sous-jacente `VARIANT` de cet `COleSafeArray` objet.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Notes

Notez que la modification de la valeur de la `VARIANT` structure accessible par le pointeur retourné par cette fonction modifie la valeur de cet `COleSafeArray` objet.

## <a name="colesafearrayoperator-"></a><a name="operator_eq"></a> COleSafeArray :: Operator =

Ces opérateurs d’assignation surchargés copient la valeur source dans cet `COleSafeArray` objet.

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>Notes

Voici une brève description de chaque opérateur :

- **opérateur = (** *saSrc* **)** Copie un `COleSafeArray` objet existant dans cet objet.

- **opérateur = (** *varSrc* **)** Copie un `VARIANT` tableau ou existant `COleVariant` dans cet objet.

- **opérateur = (** *pSrc* **)** Copie l' `VARIANT` objet de tableau accessible par *pSrc* dans cet objet.

## <a name="colesafearrayoperator-"></a><a name="operator_eq_eq"></a> COleSafeArray :: Operator = =

Cet opérateur compare deux tableaux ( `SAFEARRAY` , `VARIANT` , `COleVariant` ou `COleSafeArray` tableaux) et retourne une valeur différente de zéro s’ils sont égaux ; sinon, 0.

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>Notes

Deux tableaux sont égaux s’ils ont un nombre égal de dimensions, une taille égale dans chaque dimension et des valeurs d’éléments égales.

## <a name="colesafearrayoperator-ltlt"></a><a name="operator_lt_lt"></a> COleSafeArray ::, opérateur &lt;&lt;

L' `COleSafeArray` opérateur d’insertion (<<) prend en charge le vidage des diagnostics et le stockage d’un `COleSafeArray` objet dans une archive.

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

## <a name="colesafearrayptrofindex"></a><a name="ptrofindex"></a> COleSafeArray ::P trOfIndex

Retourne un pointeur vers l’élément spécifié par les valeurs d’index.

```cpp
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>Paramètres

*rgIndices*<br/>
Tableau de valeurs d’index qui identifient un élément du tableau. Tous les index de l’élément doivent être spécifiés.

*ppvData*<br/>
Au retour, pointeur vers l’élément identifié par les valeurs dans *rgIndices*.

## <a name="colesafearrayputelement"></a><a name="putelement"></a> COleSafeArray ::P utElement

Affecte un élément unique dans le tableau.

```cpp
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Paramètres

*rgIndices*<br/>
Pointeur vers un tableau d'index pour chaque dimension du tableau.

*pvData*<br/>
Pointeur vers les données à affecter au groupe. Les types variant VT_DISPATCH, VT_UNKNOWN et VT_BSTR sont des pointeurs et ne nécessitent pas d’autre niveau d’indirection.

### <a name="remarks"></a>Notes

Cette fonction appelle automatiquement les fonctions Windows [SafeArrayLock](/windows/win32/api/oleauto/nf-oleauto-safearraylock) et [SafeArrayUnlock](/windows/win32/api/oleauto/nf-oleauto-safearrayunlock) avant et après l’assignation de l’élément. Si l'élément de données est une chaîne, un objet ou un variant, la fonction le copie correctement ; si l'élément existant est une chaîne, un objet ou un variant, il est effacé correctement.

Il est à noter qu'un tableau peut avoir plusieurs verrous. Il est donc possible de placer des éléments dans un tableau pendant que le tableau est verrouillé par d'autres opérations.

En cas d’erreur, la fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

## <a name="colesafearrayredim"></a><a name="redim"></a> COleSafeArray :: ReDim

Modifie la liaison la moins significative (la plus à droite) d’un tableau sécurisé.

```cpp
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>Paramètres

*psaboundNew*<br/>
Pointeur vers une nouvelle structure liée à un tableau sécurisé contenant le nouveau lié au tableau. Seule la dimension la moins significative d’un tableau peut être modifiée.

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève une [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearrayresizeonedim"></a><a name="resizeonedim"></a> COleSafeArray :: ResizeOneDim

Modifie le nombre d’éléments dans un objet unidimensionnel `COleSafeArray` .

```cpp
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>Paramètres

*dwElements*<br/>
Nombre d’éléments dans le tableau sécurisé unidimensionnel.

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève une [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleSafeArray :: CreateOneDim](#createonedim).

## <a name="colesafearrayunaccessdata"></a><a name="unaccessdata"></a> COleSafeArray :: UnaccessData

Décrémente le nombre de verrous d’un tableau et invalide le pointeur récupéré par `AccessData` .

```cpp
void UnaccessData();
```

### <a name="remarks"></a>Notes

En cas d’erreur, la fonction lève une [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleSafeArray :: AccessData](#accessdata).

## <a name="colesafearrayunlock"></a><a name="unlock"></a> COleSafeArray :: Unlock

Décrémente le nombre de verrous d’un tableau afin qu’il puisse être libéré ou redimensionné.

```cpp
void Unlock();
```

### <a name="remarks"></a>Notes

Cette fonction est appelée après la fin de l’accès aux données d’un tableau. En cas d’erreur, elle lève une [COleException](../../mfc/reference/coleexception-class.md).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleVariant, classe](../../mfc/reference/colevariant-class.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[CDatabase, classe](../../mfc/reference/cdatabase-class.md)<br/>
