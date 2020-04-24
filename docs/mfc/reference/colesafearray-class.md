---
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
ms.openlocfilehash: 10e9975bac776429a38bfc707215a9465ce35c2e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753768"
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
|[COleSafeArray::AccessData](#accessdata)|Récupère un pointeur sur les données du tableau.|
|[COleSafeArray::AllocData](#allocdata)|Alloue la mémoire pour le tableau.|
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|Alloue la mémoire pour le descripteur de tableau de sécurité.|
|[COleSafeArray::Attach](#attach)|Donne le contrôle `VARIANT` du `COleSafeArray` tableau existant à l’objet.|
|[COleSafeArray::Clair](#clear)|Libère toutes les données `VARIANT`sous-jacentes .|
|[COleSafeArray::Copier](#copy)|Crée une copie d’un tableau existant.|
|[COleSafeArray::Créer](#create)|Crée un tableau sûr.|
|[COleSafeArray::CreateOneDim](#createonedim)|Crée un objet `COleSafeArray` unidimensionnel.|
|[COleSafeArray::Destroy](#destroy)|Détruit un tableau existant.|
|[COleSafeArray::DestroyData](#destroydata)|Détruit les données dans un tableau sûr.|
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|Détruit un descripteur d’un tableau sûr.|
|[COleSafeArray::Detach](#detach)|Détache le tableau VARIANT `COleSafeArray` de l’objet (de sorte que les données ne seront pas libérées).|
|[COleSafeArray::GetByteArray](#getbytearray)|Copie le contenu du tableau de sécurité dans un [CByteArray](../../mfc/reference/cbytearray-class.md).|
|[COleSafeArray::GetDim](#getdim)|Retourne le nombre de dimensions du tableau.|
|[COleSafeArray::GetElement](#getelement)|Récupère un seul élément du tableau de sécurité.|
|[COleSafeArray::GetElemSize](#getelemsize)|Retourne la taille, dans les octets, d’un élément dans un tableau sûr.|
|[COleSafeArray::GetLBound](#getlbound)|Retourne la limite inférieure pour n’importe quelle dimension d’un tableau sûr.|
|[COleSafeArray::GetOneDimSize](#getonedimsize)|Retourne le nombre d’éléments `COleSafeArray` de l’objet unidimensionnel.|
|[COleSafeArray::GetUBound](#getubound)|Retourne la limite supérieure pour n’importe quelle dimension d’un tableau sûr.|
|[COleSafeArray::Lock](#lock)|Incréments le nombre de verrouillage d’un tableau et place un pointeur aux données de tableau dans le descripteur de tableau.|
|[COleSafeArray::PtrOfIndex](#ptrofindex)|Retourne un pointeur à l’élément indexé.|
|[COleSafeArray::PutElement](#putelement)|Affecte un élément unique dans le tableau.|
|[COleSafeArray::Redim](#redim)|Change le moins significatif (le plus à droite) lié d’un tableau sûr.|
|[COleSafeArray::ResizeOneDim](#resizeonedim)|Modifie le nombre d’éléments `COleSafeArray` d’un objet unidimensionnel.|
|[COleSafeArray::UnaccessData](#unaccessdata)|Décrément le nombre de serrures d’un tableau `AccessData`et invalide le pointeur récupéré par .|
|[COleSafeArray::Unlock](#unlock)|Décrément le nombre de serrures d’un tableau afin qu’il puisse être libéré ou resized.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[COleSafeArray::opérateur LPCVARIANT](#operator_lpcvariant)|Accéde à `VARIANT` la `COleSafeArray` structure sous-jacente de l’objet.|
|[COleSafeArray::opérateur LPVARIANT](#operator_lpvariant)|Accéde à `VARIANT` la `COleSafeArray` structure sous-jacente de l’objet.|
|[COleSafeArray::opérateur](#operator_eq)|Copies des `COleSafeArray` valeurs`SAFEARRAY`dans `VARIANT` `COleVariant`un `COleSafeArray` objet ( , , , , ou tableau).|
|[COleSafeArray::opérateur](#operator_eq_eq)|Compare deux tableaux de`SAFEARRAY` `VARIANT`variantes (, , , `COleVariant`ou `COleSafeArray` tableaux).|
|[COleSafeArray::opérateur&lt;&lt;](#operator_lt_lt)|Sortie du contenu `COleSafeArray` d’un objet au contexte du dépotoir.|

## <a name="remarks"></a>Notes

`COleSafeArray`dérive de la `VARIANT` structure OLE. Les fonctions des membres `SAFEARRAY` `COleSafeArray`OLE sont disponibles à travers , ainsi qu’un ensemble de fonctions membres spécialement conçues pour les tableaux unidimensionnels d’octets.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="colesafearrayaccessdata"></a><a name="accessdata"></a>COleSafeArray::AccessData

Récupère un pointeur sur les données du tableau.

```cpp
void AccessData(void** ppvData);
```

### <a name="parameters"></a>Paramètres

*ppvData (en)*<br/>
Un pointeur à un pointeur pour les données de tableau.

### <a name="remarks"></a>Notes

Sur l’erreur, la fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

## <a name="colesafearrayallocdata"></a><a name="allocdata"></a>COleSafeArray::AllocData

Alloue la mémoire pour un tableau sûr.

```cpp
void AllocData();
```

### <a name="remarks"></a>Notes

Sur l’erreur, la fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearrayallocdescriptor"></a><a name="allocdescriptor"></a>COleSafeArray::AllocDescriptor

Alloue la mémoire au descripteur d’un tableau sûr.

```cpp
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>Paramètres

*dwDims dwDims*<br/>
Nombre de dimensions dans le tableau de sécurité.

### <a name="remarks"></a>Notes

Sur l’erreur, la fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearrayattach"></a><a name="attach"></a>COleSafeArray::Attach

Donne le contrôle des `VARIANT` données dans `COleSafeArray` un tableau existant à l’objet.

```cpp
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Paramètres

*varSrc*<br/>
Objet `VARIANT` . Le *paramètre varSrc* doit avoir le VARTYPE [VT_ARRAY](/windows/win32/api/wtypes/ne-wtypes-varenum).

### <a name="remarks"></a>Notes

Le `VARIANT`type de la source est réglé pour VT_EMPTY. Cette fonction efface les données de tableau actuelles, le cas échéant.

### <a name="example"></a>Exemple

  Voir l’exemple pour [COleSafeArray::AccessData](#accessdata).

## <a name="colesafearrayclear"></a><a name="clear"></a>COleSafeArray::Clair

Efface le tableau de sécurité.

```cpp
void Clear();
```

### <a name="remarks"></a>Notes

La fonction efface un tableau `VARTYPE` de sécurité en définissant l’objet à VT_EMPTY. Le contenu actuel est libéré et le tableau est libéré.

## <a name="colesafearraycolesafearray"></a><a name="colesafearray"></a>COleSafeArray::COleSafeArray

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
Un `COleSafeArray` objet `SAFEARRAY` existant ou à copier `COleSafeArray` dans le nouvel objet.

*vtSrc*<br/>
Le VARTYPE du `COleSafeArray` nouvel objet.

*psaSrc*<br/>
Un pointeur `SAFEARRAY` à un à `COleSafeArray` copier dans le nouvel objet.

*varSrc*<br/>
Un `VARIANT` objet `COleVariant` existant ou à copier `COleSafeArray` dans le nouvel objet.

*pSrc (en)*<br/>
Un pointeur `VARIANT` à un objet à `COleSafeArray` copier dans le nouvel objet.

### <a name="remarks"></a>Notes

Tous ces constructeurs `COleSafeArray` créent de nouveaux objets. S’il n’y `COleSafeArray` a pas de paramètre, un objet vide est créé (VT_EMPTY). Si `COleSafeArray` le est copié à partir d’un autre `COleSafeArray`tableau `COleVariant`dont `VARIANT`VARTYPE est connu implicitement (a , , ou ), le VARTYPE du tableau source est conservé et n’a pas besoin d’être spécifié. Si `COleSafeArray` le est copié à partir d’un`SAFEARRAY`autre tableau dont VARTYPE n’est pas connu ( ), le VARTYPE doit être spécifié dans le paramètre *vtSrc.*

Sur l’erreur, la fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraycopy"></a><a name="copy"></a>COleSafeArray::Copier

Crée une copie d’un tableau de sécurité existant.

```cpp
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>Paramètres

*Ppsa*<br/>
Pointeur vers un endroit où retourner le nouveau descripteur de tableau.

### <a name="remarks"></a>Notes

Sur l’erreur, la fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraycreate"></a><a name="create"></a>COleSafeArray::Créer

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
Le type de base du tableau (c’est-à-dire le VARTYPE de chaque élément du tableau). Le VARTYPE est limité à un sous-ensemble des types de variantes. Ni le VT_ARRAY ni le drapeau VT_BYREF ne peuvent être fixés. VT_EMPTY et VT_NULL ne sont pas des types de base valides pour le tableau. Tous les autres types sont légaux.

*dwDims dwDims*<br/>
Nombre de dimensions dans le tableau. Cela peut être changé après le tableau est créé avec [Redim](#redim).

*rgElements*<br/>
Pointeur vers un tableau du nombre d’éléments pour chaque dimension du tableau.

*rgsabounds*<br/>
Pointeur vers un vecteur de limites (un pour chaque dimension) à allouer pour le tableau.

### <a name="remarks"></a>Notes

Cette fonction effacera les données de tableau actuelles si nécessaire. Sur l’erreur, la fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraycreateonedim"></a><a name="createonedim"></a>COleSafeArray::CreateOneDim

Crée un nouvel `COleSafeArray` objet unidimensionnel.

```cpp
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>Paramètres

*vtSrc*<br/>
Le type de base du tableau (c’est-à-dire le VARTYPE de chaque élément du tableau).

*dwElements*<br/>
Nombre d’éléments dans le tableau. Cela peut être changé après la création du tableau avec [ResizeOneDim](#resizeonedim).

*pvSrcData*<br/>
Pointeur vers les données à copier dans le tableau.

*nLBound (en anglais)*<br/>
La limite inférieure du tableau.

### <a name="remarks"></a>Notes

La fonction alloue et initialise les données pour le tableau, en copiant les données spécifiées si le pointeur *pvSrcData* n’est pas NULL.

Sur l’erreur, la fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

## <a name="colesafearraydestroy"></a><a name="destroy"></a>COleSafeArray::Destroy

Détruit un descripteur de tableau existant et toutes les données dans le tableau.

```cpp
void Destroy();
```

### <a name="remarks"></a>Notes

Si des objets sont stockés dans le tableau, chaque objet est libéré. Sur l’erreur, la fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraydestroydata"></a><a name="destroydata"></a>COleSafeArray::DestroyData

Détruit toutes les données dans un tableau sécurisé.

```cpp
void DestroyData();
```

### <a name="remarks"></a>Notes

Si des objets sont stockés dans le tableau, chaque objet est libéré. Sur l’erreur, la fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraydestroydescriptor"></a><a name="destroydescriptor"></a>COleSafeArray::DestroyDescriptor

Détruit un descripteur d’un tableau sûr.

```cpp
void DestroyDescriptor();
```

### <a name="remarks"></a>Notes

Sur l’erreur, la fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraydetach"></a><a name="detach"></a>COleSafeArray::Detach

Détache les `VARIANT` données de `COleSafeArray` l’objet.

```
VARIANT Detach();
```

### <a name="return-value"></a>Valeur de retour

La `VARIANT` valeur sous-jacente de l’objet. `COleSafeArray`

### <a name="remarks"></a>Notes

La fonction détache les données dans un tableau de sécurité en définissant le VARTYPE de l’objet à VT_EMPTY. Il est de la responsabilité de l’appelant de libérer le tableau en appelant la fonction Windows [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear).

Sur l’erreur, la fonction jette un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

  Voir l’exemple pour [COleSafeArray::PutElement](#putelement).

## <a name="colesafearraygetbytearray"></a><a name="getbytearray"></a>COleSafeArray::GetByteArray

Copie le contenu du tableau `CByteArray`de sécurité dans un .

```cpp
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>Paramètres

*Octets*<br/>
Une référence à un objet [CByteArray.](../../mfc/reference/cbytearray-class.md)

## <a name="colesafearraygetdim"></a><a name="getdim"></a>COleSafeArray::GetDim

Retourne le nombre de `COleSafeArray` dimensions dans l’objet.

```
DWORD GetDim();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de dimensions dans le tableau de sécurité.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraygetelement"></a><a name="getelement"></a>COleSafeArray::GetElement

Récupère un seul élément du tableau de sécurité.

```cpp
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Paramètres

*rgIndices*<br/>
Pointeur vers un tableau d'index pour chaque dimension du tableau.

*pvData (en)*<br/>
Pointeur à l’emplacement pour placer l’élément du tableau.

### <a name="remarks"></a>Notes

Cette fonction appelle automatiquement `SafeArrayLock` les `SafeArrayUnlock` fonctions windows et avant et après la récupération de l’élément. Si l’élément de données est une chaîne, un objet ou une variante, la fonction copie l’élément de la bonne manière. Le paramètre *pvData* doit indiquer un tampon assez grand pour contenir l’élément.

Sur l’erreur, la fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

## <a name="colesafearraygetelemsize"></a><a name="getelemsize"></a>COleSafeArray::GetElemSize

Récupère la taille d’un `COleSafeArray` élément dans un objet.

```
DWORD GetElemSize();
```

### <a name="return-value"></a>Valeur de retour

La taille, dans les octets, des éléments d’un tableau de sécurité.

## <a name="colesafearraygetlbound"></a><a name="getlbound"></a>COleSafeArray::GetLBound

Retourne la limite inférieure pour `COleSafeArray` n’importe quelle dimension d’un objet.

```cpp
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>Paramètres

*dwDim dwDim*<br/>
La dimension de tableau pour laquelle obtenir la limite inférieure.

*pLBound (en anglais)*<br/>
Pointeur à l’emplacement pour retourner la limite inférieure.

### <a name="remarks"></a>Notes

Sur l’erreur, la fonction jette un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

## <a name="colesafearraygetonedimsize"></a><a name="getonedimsize"></a>COleSafeArray::GetOneDimSize

Retourne le nombre d’éléments `COleSafeArray` de l’objet unidimensionnel.

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans le tableau de sécurité unidimensionnel.

### <a name="example"></a>Exemple

  Voir l’exemple pour [COleSafeArray::CreateOneDim](#createonedim).

## <a name="colesafearraygetubound"></a><a name="getubound"></a>COleSafeArray::GetUBound

Retourne la limite supérieure pour n’importe quelle dimension d’un tableau sûr.

```cpp
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>Paramètres

*dwDim dwDim*<br/>
La dimension de tableau pour laquelle obtenir la limite supérieure.

*pUBound (en)*<br/>
Pointeur à l’emplacement pour retourner la limite supérieure.

### <a name="remarks"></a>Notes

Sur l’erreur, la fonction jette un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

## <a name="colesafearraylock"></a><a name="lock"></a>COleSafeArray::Lock

Incréments le nombre de verrouillage d’un tableau et place un pointeur aux données de tableau dans le descripteur de tableau.

```cpp
void Lock();
```

### <a name="remarks"></a>Notes

Sur l’erreur, il jette un [COleException](../../mfc/reference/coleexception-class.md).

Le pointeur dans le descripteur de tableau est valide jusqu’à ce qu’il `Unlock` soit appelé. Les `Lock` appels peuvent être imbriqués; un nombre égal `Unlock` d’appels sont requis.

Un tableau ne peut pas être supprimé pendant qu’il est verrouillé.

## <a name="colesafearrayoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleSafeArray::opérateur LPCVARIANT

Appelez cet opérateur de `VARIANT` coulée `COleSafeArray` pour accéder à la structure sous-jacente de cet objet.

```
operator LPCVARIANT() const;
```

## <a name="colesafearrayoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleSafeArray::opérateur LPVARIANT

Appelez cet opérateur de `VARIANT` coulée `COleSafeArray` pour accéder à la structure sous-jacente de cet objet.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Notes

Notez que la `VARIANT` modification de la valeur de la structure accessible `COleSafeArray` par le pointeur retourné par cette fonction modifiera la valeur de cet objet.

## <a name="colesafearrayoperator-"></a><a name="operator_eq"></a>COleSafeArray::opérateur

Ces opérateurs d’affectation surchargés copient la valeur source dans cet `COleSafeArray` objet.

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>Notes

Une brève description de chaque opérateur suit :

- **opérateur** *(saSrc)* **)** Copie d’un objet existant `COleSafeArray` dans cet objet.

- **opérateur** *(varSrc)* **)** Copie d’un `VARIANT` `COleVariant` ou d’un tableau existant dans cet objet.

- **opérateur** *(pSrc)* **)** Copie `VARIANT` de l’objet de tableau accessible par *pSrc* dans cet objet.

## <a name="colesafearrayoperator-"></a><a name="operator_eq_eq"></a>COleSafeArray::opérateur

Cet opérateur compare deux`SAFEARRAY`tableaux `VARIANT` `COleVariant`(, `COleSafeArray` , , ou tableaux) et retourne nonzero s’ils sont égaux; sinon 0.

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>Notes

Deux tableaux sont égaux s’ils ont un nombre égal de dimensions, une taille égale dans chaque dimension et des valeurs d’éléments égaux.

## <a name="colesafearrayoperator-ltlt"></a><a name="operator_lt_lt"></a>COleSafeArray::opérateur&lt;&lt;

L’opérateur `COleSafeArray` d’insertion (<<) prend en `COleSafeArray` charge le dumping diagnostique et le stockage d’un objet à une archive.

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

## <a name="colesafearrayptrofindex"></a><a name="ptrofindex"></a>COleSafeArray::PtrOfIndex

Retourne un pointeur à l’élément spécifié par les valeurs indiciels.

```cpp
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>Paramètres

*rgIndices*<br/>
Un éventail de valeurs indiciels qui identifient un élément du tableau. Tous les index de l’élément doivent être spécifiés.

*ppvData (en)*<br/>
Au retour, pointeur à l’élément identifié par les valeurs dans *rgIndices*.

## <a name="colesafearrayputelement"></a><a name="putelement"></a>COleSafeArray::PutElement

Affecte un élément unique dans le tableau.

```cpp
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Paramètres

*rgIndices*<br/>
Pointeur vers un tableau d'index pour chaque dimension du tableau.

*pvData (en)*<br/>
Pointeur vers les données à affecter au groupe. VT_DISPATCH, VT_UNKNOWN et VT_BSTR types de variantes sont des pointeurs et ne nécessitent pas un autre niveau d’indirection.

### <a name="remarks"></a>Notes

Cette fonction appelle automatiquement les fonctions Windows [SafeArrayLock](/windows/win32/api/oleauto/nf-oleauto-safearraylock) et [SafeArrayUnlock](/windows/win32/api/oleauto/nf-oleauto-safearrayunlock) avant et après l’attribution de l’élément. Si l'élément de données est une chaîne, un objet ou un variant, la fonction le copie correctement ; si l'élément existant est une chaîne, un objet ou un variant, il est effacé correctement.

Il est à noter qu'un tableau peut avoir plusieurs verrous. Il est donc possible de placer des éléments dans un tableau pendant que le tableau est verrouillé par d'autres opérations.

Sur l’erreur, la fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

## <a name="colesafearrayredim"></a><a name="redim"></a>COleSafeArray::Redim

Change le moins significatif (le plus à droite) lié d’un tableau sûr.

```cpp
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>Paramètres

*psaboundNew*<br/>
Pointeur vers une nouvelle structure reliée à un tableau de sécurité contenant le nouveau tableau lié. Seule la dimension la moins importante d’un tableau peut être modifiée.

### <a name="remarks"></a>Notes

Sur l’erreur, la fonction jette un [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearrayresizeonedim"></a><a name="resizeonedim"></a>COleSafeArray::ResizeOneDim

Modifie le nombre d’éléments `COleSafeArray` d’un objet unidimensionnel.

```cpp
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>Paramètres

*dwElements*<br/>
Nombre d’éléments dans le tableau de sécurité unidimensionnel.

### <a name="remarks"></a>Notes

Sur l’erreur, la fonction jette un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

  Voir l’exemple pour [COleSafeArray::CreateOneDim](#createonedim).

## <a name="colesafearrayunaccessdata"></a><a name="unaccessdata"></a>COleSafeArray::UnaccessData

Décrément le nombre de serrures d’un tableau `AccessData`et invalide le pointeur récupéré par .

```cpp
void UnaccessData();
```

### <a name="remarks"></a>Notes

Sur l’erreur, la fonction jette un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Exemple

  Voir l’exemple pour [COleSafeArray::AccessData](#accessdata).

## <a name="colesafearrayunlock"></a><a name="unlock"></a>COleSafeArray::Unlock

Décrément le nombre de serrures d’un tableau afin qu’il puisse être libéré ou resized.

```cpp
void Unlock();
```

### <a name="remarks"></a>Notes

Cette fonction est appelée après l’accès aux données dans un tableau est terminé. Sur l’erreur, il jette un [COleException](../../mfc/reference/coleexception-class.md).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleVariant, classe](../../mfc/reference/colevariant-class.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Classe CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
