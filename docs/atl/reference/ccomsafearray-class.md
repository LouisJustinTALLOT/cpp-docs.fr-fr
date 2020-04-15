---
title: CComSafeArray, classe
ms.date: 05/06/2019
f1_keywords:
- CComSafeArray
- ATLSAFE/ATL::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::Add
- ATLSAFE/ATL::CComSafeArray::Attach
- ATLSAFE/ATL::CComSafeArray::CopyFrom
- ATLSAFE/ATL::CComSafeArray::CopyTo
- ATLSAFE/ATL::CComSafeArray::Create
- ATLSAFE/ATL::CComSafeArray::Destroy
- ATLSAFE/ATL::CComSafeArray::Detach
- ATLSAFE/ATL::CComSafeArray::GetAt
- ATLSAFE/ATL::CComSafeArray::GetCount
- ATLSAFE/ATL::CComSafeArray::GetDimensions
- ATLSAFE/ATL::CComSafeArray::GetLowerBound
- ATLSAFE/ATL::CComSafeArray::GetSafeArrayPtr
- ATLSAFE/ATL::CComSafeArray::GetType
- ATLSAFE/ATL::CComSafeArray::GetUpperBound
- ATLSAFE/ATL::CComSafeArray::IsSizable
- ATLSAFE/ATL::CComSafeArray::MultiDimGetAt
- ATLSAFE/ATL::CComSafeArray::MultiDimSetAt
- ATLSAFE/ATL::CComSafeArray::Resize
- ATLSAFE/ATL::CComSafeArray::SetAt
- ATLSAFE/ATL::CComSafeArray::m_psa
helpviewer_keywords:
- CComSafeArray class
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
ms.openlocfilehash: d1e72d364858ea31541d574ed77bdc8ccca7d748
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327401"
---
# <a name="ccomsafearray-class"></a>CComSafeArray, classe

Cette classe est un `SAFEARRAY` emballage pour la structure.

## <a name="syntax"></a>Syntaxe

```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données à stocker dans le tableau.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComSafeArray::CComSafeArray](#ccomsafearray)|Constructeur.|
|[CComSafeArray:](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComSafeArray::Ajouter](#add)|Ajoute un ou plusieurs `SAFEARRAY` éléments, ou `CComSafeArray`une structure, à un .|
|[CComSafeArray::Attach](#attach)|Attache une `SAFEARRAY` structure `CComSafeArray` à un objet.|
|[CComSafeArray::CopyDe](#copyfrom)|Copie le contenu `SAFEARRAY` d’une structure dans l’objet. `CComSafeArray`|
|[CComSafeArray::CopyTo](#copyto)|Crée une copie de l'objet `CComSafeArray`.|
|[CComSafeArray::Create](#create)|Crée un objet `CComSafeArray` .|
|[CComSafeArray::Destroy](#destroy)|Détruit un objet `CComSafeArray` .|
|[CComSafeArray::Detach](#detach)|Détache un `SAFEARRAY` objet. `CComSafeArray`|
|[CComSafeArray::GetAt](#getat)|Récupère un élément unique à partir d’un tableau unidimensionnel.|
|[CComSafeArray::GetCount](#getcount)|Retourne le nombre d'éléments du tableau.|
|[CComSafeArray::GetDimensions](#getdimensions)|Retourne le nombre de dimensions du tableau.|
|[CComSafeArray::GetLowerBound](#getlowerbound)|Retourne la limite inférieure d’une dimension donnée du tableau.|
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|Retourne l’adresse du membre de données `m_psa` .|
|[CComSafeArray::GetType](#gettype)|Retourne le type de données stocké dans le tableau.|
|[CComSafeArray::GetUpperBound](#getupperbound)|Retourne la limite supérieure d’une dimension du tableau.|
|[CComSafeArray::IsSizable](#issizable)|Teste si un objet `CComSafeArray` peut être redimensionné.|
|[CComSafeArray::MultiDimGetAt](#multidimgetat)|Récupère un élément unique à partir d’un tableau multidimensionnel.|
|[CComSafeArray::MultiDimSetAt](#multidimsetat)|Définit la valeur d’un élément d’un tableau multidimensionnel.|
|[CComSafeArray::Resize](#resize)|Redimensionne un objet `CComSafeArray` .|
|[CComSafeArray::SetAt](#setat)|Définit la valeur d’un élément d’un tableau unidimensionnel.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CComSafeArray::opérateur LPSAFEARRAY](#operator_lpsafearray)|Jetez une valeur `SAFEARRAY` à un pointeur.|
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|Récupère un élément du tableau.|
|[CComSafeArray::opérateur](#operator_eq)|Opérateur d'assignation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComSafeArray::m_psa](#m_psa)|Ce membre des données `SAFEARRAY` tient l’adresse de la structure.|

## <a name="remarks"></a>Notes

`CComSafeArray` fournit un wrapper pour la classe [SAFEARRAY Data Type](/windows/win32/api/oaidl/ns-oaidl-safearray) , ce qui simplifie la création et la gestion des tableaux unidimensionnels et multidimensionnels de pratiquement n’importe quel type prenant en charge VARIANT.

`CComSafeArray` simplifie le transmission de tableaux entre processus et offre en outre une sécurité renforcée en vérifiant les valeurs d’index de tableau par rapport aux limites inférieure et supérieure.

La limite inférieure d’un `CComSafeArray` peut commencer à n’importe quelle valeur définie par l’utilisateur ; cependant, les tableaux accessibles via C++ doivent utiliser une limite inférieure de 0. D’autres langages comme Visual Basic peuvent utiliser d’autres valeurs de délimitation (par exemple, de -10 à 10).

Utilisez [CComSafeArray::Create](#create) pour créer un objet `CComSafeArray` et [CComSafeArray::Destroy](#destroy) pour le supprimer.

Un `CComSafeArray` peut contenir le sous-ensemble de types de données VARIANT suivant :

|VARTYPE|Description|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglong|
|VT_R4|float|
|VT_R8|double|
|VT_DECIMAL|pointeur décimal|
|VT_VARIANT|pointeur de type Variant|
|VT_CY|Currency (type de données)|

## <a name="requirements"></a>Spécifications

**En-tête :** atlsafe.h

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]

## <a name="ccomsafearrayadd"></a><a name="add"></a>CComSafeArray::Ajouter

Ajoute un ou plusieurs `SAFEARRAY` éléments, ou `CComSafeArray`une structure, à un .

```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Paramètres

*psaSrc*<br/>
Pointeur vers un objet `SAFEARRAY`.

*ulCount ulCount*<br/>
Le nombre d’objets à ajouter au tableau.

*Pt*<br/>
Un pointeur à un ou plusieurs objets à ajouter au tableau.

*T*<br/>
Une référence à l’objet à ajouter au tableau.

*bCopy (en)*<br/>
Indique si une copie des données doit être créée. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Les nouveaux objets sont annexés à `SAFEARRAY` la fin de l’objet existant. L’ajout d’un `SAFEARRAY` objet à un objet multidimensionnel n’est pas pris en charge. Lors de l’ajout d’une gamme existante d’objets, les deux tableaux doivent contenir des éléments du même type.

Le drapeau *bCopy* est pris en compte lorsque des éléments de type BSTR ou VARIANT sont ajoutés à un tableau. La valeur par défaut de TRUE garantit qu’une nouvelle copie est faite des données lorsque l’élément est ajouté au tableau.

## <a name="ccomsafearrayattach"></a><a name="attach"></a>CComSafeArray::Attach

Attache une `SAFEARRAY` structure `CComSafeArray` à un objet.

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Paramètres

*psaSrc*<br/>
Un pointeur `SAFEARRAY` de la structure.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Attache une `SAFEARRAY` structure `CComSafeArray` à un objet, rendant disponibles les méthodes existantes. `CComSafeArray`

## <a name="ccomsafearrayccomsafearray"></a><a name="ccomsafearray"></a>CComSafeArray::CComSafeArray

Constructeur.

```
CComSafeArray();
CComSafeArray(const SAFEARRAYBOUND& bound);
CComSafeArray(ULONG  ulCount, LONG lLBound = 0);
CComSafeArray(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
CComSafeArray(const CComSafeArray& saSrc);
CComSafeArray(const SAFEARRAY& saSrc);
CComSafeArray(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Paramètres

*Lié*<br/>
Structure `SAFEARRAYBOUND`.

*ulCount ulCount*<br/>
Nombre d’éléments dans le tableau.

*lLBound (en anglais)*<br/>
La valeur limite inférieure; c’est-à-dire l’index du premier élément du tableau.

*pBound (en)*<br/>
Un pointeur `SAFEARRAYBOUND` vers une structure.

*uDims (en)*<br/>
Le nombre de dimensions dans le tableau.

*saSrc*<br/>
Une référence `SAFEARRAY` à `CComSafeArray` une structure ou à un objet. Dans les deux cas, le constructeur utilise cette référence pour faire une copie du tableau, de sorte que le tableau n’est pas référencé après la construction.

*psaSrc*<br/>
Un pointeur `SAFEARRAY` vers une structure. Le constructeur utilise cette adresse pour faire une copie du tableau, de sorte que le tableau n’est pas référencé après la construction.

### <a name="remarks"></a>Notes

Crée un objet `CComSafeArray` .

## <a name="ccomsafearrayccomsafearray"></a><a name="dtor"></a>CComSafeArray:

Destructeur.

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="ccomsafearraycopyfrom"></a><a name="copyfrom"></a>CComSafeArray::CopyDe

Copie le contenu `SAFEARRAY` d’une structure dans l’objet. `CComSafeArray`

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Paramètres

*ppArray*<br/>
Pointeur `SAFEARRAY` à la copie.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette méthode copie le `SAFEARRAY` contenu `CComSafeArray` d’un objet dans l’objet actuel. Le contenu existant du tableau est remplacé.

## <a name="ccomsafearraycopyto"></a><a name="copyto"></a>CComSafeArray::CopyTo

Crée une copie de l'objet `CComSafeArray`.

```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Paramètres

*ppArray*<br/>
Un pointeur à un endroit `SAFEARRAY`où créer le nouveau .

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette méthode copie le `CComSafeArray` contenu `SAFEARRAY` d’un objet dans une structure.

## <a name="ccomsafearraycreate"></a><a name="create"></a>CComSafeArray::Créer

Crée un `CComSafeArray`.

```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```

### <a name="parameters"></a>Paramètres

*pBound (en)*<br/>
Pointeur vers un objet `SAFEARRAYBOUND`.

*uDims (en)*<br/>
Nombre de dimensions dans le tableau.

*ulCount ulCount*<br/>
Nombre d’éléments dans le tableau.

*lLBound (en anglais)*<br/>
La valeur limite inférieure; c’est-à-dire l’index du premier élément du tableau.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Un `CComSafeArray` objet peut être `SAFEARRAYBOUND` créé à partir d’une structure existante et du nombre de dimensions, ou en spécifiant le nombre d’éléments dans le tableau et la limite inférieure. Si le tableau doit être accessible à partir de C, la limite inférieure doit être de 0. D’autres langues peuvent permettre d’autres valeurs pour la limite inférieure (par exemple, Visual Basic prend en charge les tableaux avec des éléments avec une gamme telle que -10 à 10).

## <a name="ccomsafearraydestroy"></a><a name="destroy"></a>CComSafeArray::Destroy

Détruit un objet `CComSafeArray` .

```
HRESULT Destroy();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Détruit un `CComSafeArray` objet existant et toutes les données qu’il contient.

## <a name="ccomsafearraydetach"></a><a name="detach"></a>CComSafeArray::Detach

Détache un `SAFEARRAY` objet. `CComSafeArray`

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur à un `SAFEARRAY` objet.

### <a name="remarks"></a>Notes

Cette méthode détache `SAFEARRAY` l’objet `CComSafeArray` de l’objet.

## <a name="ccomsafearraygetat"></a><a name="getat"></a>CComSafeArray::GetAt

Récupère un élément unique à partir d’un tableau unidimensionnel.

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>Paramètres

*Lindex*<br/>
Le numéro d’index de la valeur dans le tableau à retourner.

### <a name="return-value"></a>Valeur de retour

Renvoie une référence à l’élément de tableau requis.

## <a name="ccomsafearraygetcount"></a><a name="getcount"></a>CComSafeArray::GetCount

Retourne le nombre d'éléments du tableau.

```
ULONG GetCount(UINT uDim = 0) const;
```

### <a name="parameters"></a>Paramètres

*uDim (en)*<br/>
La dimension du tableau.

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d'éléments du tableau.

### <a name="remarks"></a>Notes

Lorsqu’elle est utilisée avec un tableau multidimensionnel, cette méthode ne renvoie que le nombre d’éléments dans une dimension spécifique.

## <a name="ccomsafearraygetdimensions"></a><a name="getdimensions"></a>CComSafeArray::GetDimensions

Retourne le nombre de dimensions du tableau.

```
UINT GetDimensions() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de dimensions du tableau.

## <a name="ccomsafearraygetlowerbound"></a><a name="getlowerbound"></a>CComSafeArray::GetLowerBound

Retourne la limite inférieure d’une dimension donnée du tableau.

```
LONG GetLowerBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Paramètres

*uDim (en)*<br/>
La dimension de tableau pour laquelle obtenir la limite inférieure. Si omis, la valeur par défaut est de 0.

### <a name="return-value"></a>Valeur de retour

Retourne la limite inférieure.

### <a name="remarks"></a>Notes

Si la limite inférieure est de 0, cela indique un tableau C-like dont le premier élément est l’élément numéro 0. En cas d’erreur, par exemple, un argument `AtlThrow` de dimension invalide, cette méthode appelle avec un HRESULT décrivant l’erreur.

## <a name="ccomsafearraygetsafearrayptr"></a><a name="getsafearrayptr"></a>CComSafeArray::GetSafeArrayPtr

Retourne l’adresse du membre de données `m_psa` .

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur au [CComSafeArray ::m_psa](#m_psa) membre des données.

## <a name="ccomsafearraygettype"></a><a name="gettype"></a>CComSafeArray::GetType

Retourne le type de données stocké dans le tableau.

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>Valeur de retour

Renvoie le type de données stockées dans le tableau, qui pourrait être l’un des types suivants :

|VARTYPE|Description|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglong|
|VT_R4|float|
|VT_R8|double|
|VT_DECIMAL|pointeur décimal|
|VT_VARIANT|pointeur de type Variant|
|VT_CY|Currency (type de données)|

## <a name="ccomsafearraygetupperbound"></a><a name="getupperbound"></a>CComSafeArray::GetUpperBound

Retourne la limite supérieure d’une dimension du tableau.

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Paramètres

*uDim (en)*<br/>
La dimension de tableau pour laquelle obtenir la limite supérieure. Si omis, la valeur par défaut est de 0.

### <a name="return-value"></a>Valeur de retour

Retourne la limite supérieure. Cette valeur est inclusive, l’indice maximum valide pour cette dimension.

### <a name="remarks"></a>Notes

En cas d’erreur, par exemple, un argument `AtlThrow` de dimension invalide, cette méthode appelle avec un HRESULT décrivant l’erreur.

## <a name="ccomsafearrayissizable"></a><a name="issizable"></a>CComSafeArray::IsSizable

Teste si un objet `CComSafeArray` peut être redimensionné.

```
bool IsSizable() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI `CComSafeArray` si le peut être resized, FALSE si elle ne peut pas.

## <a name="ccomsafearraym_psa"></a><a name="m_psa"></a>CComSafeArray::m_psa

Tient l’adresse `SAFEARRAY` de la structure accessible.

```
LPSAFEARRAY m_psa;
```

## <a name="ccomsafearraymultidimgetat"></a><a name="multidimgetat"></a>CComSafeArray::MultiDimGetAt

Récupère un élément unique à partir d’un tableau multidimensionnel.

```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```

### <a name="parameters"></a>Paramètres

*alIndex (en)*<br/>
Pointeur vers un vecteur d’index pour chaque dimension du tableau. La dimension la plus gauche `alIndex[0]`(la plus significative) est .

*T*<br/>
Une référence aux données retournées.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

## <a name="ccomsafearraymultidimsetat"></a><a name="multidimsetat"></a>CComSafeArray::MultiDimSetAt

Définit la valeur d’un élément d’un tableau multidimensionnel.

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>Paramètres

*alIndex (en)*<br/>
Pointeur vers un vecteur d’index pour chaque dimension du tableau. La dimension la plus juste `alIndex`(la moins significative) est [0].

*T*<br/>
Spécifie la valeur du nouvel élément.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Il s’agit d’une version multidimensionnelle de [CComSafeArray::SetAt](#setat).

## <a name="ccomsafearrayoperator-"></a><a name="operator_at"></a>CComSafeArray::opérateur\[\]

Récupère un élément du tableau.

```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```

### <a name="parameters"></a>Paramètres

*lIndex, nIndex*<br/>
Le numéro d’index de l’élément requis dans le tableau.

### <a name="return-value"></a>Valeur de retour

Retourne l’élément de tableau approprié.

### <a name="remarks"></a>Notes

Effectue une fonction similaire à [CComSafeArray::GetAt](#getat), mais cet opérateur ne fonctionne qu’avec des tableaux unidimensionnels.

## <a name="ccomsafearrayoperator-"></a><a name="operator_eq"></a>CComSafeArray::opérateur

Opérateur d'assignation.

```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Paramètres

*saSrc*<br/>
Référence à un objet `CComSafeArray`.

*psaSrc*<br/>
Pointeur vers un objet `SAFEARRAY`.

### <a name="return-value"></a>Valeur de retour

Retourne le type de données stocké dans le tableau.

## <a name="ccomsafearrayoperator-lpsafearray"></a><a name="operator_lpsafearray"></a>CComSafeArray::opérateur LPSAFEARRAY

Jetez une valeur `SAFEARRAY` à un pointeur.

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>Valeur de retour

Jetez une valeur `SAFEARRAY` à un pointeur.

## <a name="ccomsafearrayresize"></a><a name="resize"></a>CComSafeArray::Resize

Redimensionne un objet `CComSafeArray` .

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>Paramètres

*pBound (en)*<br/>
Pointeur d’une `SAFEARRAYBOUND` structure qui contient des informations sur le nombre d’éléments et la limite inférieure d’un tableau.

*ulCount ulCount*<br/>
Le nombre demandé d’objets dans le tableau ressétisé.

*lLBound (en anglais)*<br/>
Limite inférieure.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette méthode ne fait que resize la dimension la plus droite. Il ne sera pas resize tableaux qui reviennent `IsResizable` comme FALSE.

## <a name="ccomsafearraysetat"></a><a name="setat"></a>CComSafeArray::SetAt

Définit la valeur d’un élément d’un tableau unidimensionnel.

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Paramètres

*Lindex*<br/>
Le numéro d’index de l’élément de tableau à définir.

*T*<br/>
Nouvelle valeur de l'élément spécifié.

*bCopy (en)*<br/>
Indique si une copie des données doit être créée. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Le drapeau *bCopy* est pris en compte lorsque des éléments de type BSTR ou VARIANT sont ajoutés à un tableau. La valeur par défaut de TRUE garantit qu’une nouvelle copie est faite des données lorsque l’élément est ajouté au tableau.

## <a name="see-also"></a>Voir aussi

[SAFEARRAY Data Type](/windows/win32/api/oaidl/ns-oaidl-safearray)<br/>
[CComSafeArray::Create](#create)<br/>
[CComSafeArray::Destroy](#destroy)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
