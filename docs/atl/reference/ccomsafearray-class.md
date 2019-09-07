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
ms.openlocfilehash: 79b1dc844f53f739dc48eb6177e57810ff0c8412
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739590"
---
# <a name="ccomsafearray-class"></a>CComSafeArray, classe

Cette classe est un wrapper pour la `SAFEARRAY` structure.

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
|[CComSafeArray::~CComSafeArray](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComSafeArray::Add](#add)|Ajoute un ou plusieurs éléments, ou une `SAFEARRAY` structure, à un `CComSafeArray`.|
|[CComSafeArray::Attach](#attach)|Attache une `SAFEARRAY` structure à un `CComSafeArray` objet.|
|[CComSafeArray::CopyFrom](#copyfrom)|Copie le contenu d’une `SAFEARRAY` structure dans l' `CComSafeArray` objet.|
|[CComSafeArray::CopyTo](#copyto)|Crée une copie de l’objet `CComSafeArray`.|
|[CComSafeArray::Create](#create)|Crée un objet `CComSafeArray`.|
|[CComSafeArray::Destroy](#destroy)|Détruit un objet `CComSafeArray`.|
|[CComSafeArray::Detach](#detach)|Détache un `SAFEARRAY` d’un `CComSafeArray` objet.|
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
|[CComSafeArray :: Operator LPSAFEARRAY](#operator_lpsafearray)|Convertit une valeur en `SAFEARRAY` pointeur.|
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|Récupère un élément du tableau.|
|[CComSafeArray::operator =](#operator_eq)|Opérateur d'assignation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComSafeArray::m_psa](#m_psa)|Ce membre de données contient l’adresse de `SAFEARRAY` la structure.|

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
|VT_R8|Double|
|VT_DECIMAL|pointeur décimal|
|VT_VARIANT|pointeur de type Variant|
|VT_CY|Currency (type de données)|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsafe.h

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]

##  <a name="add"></a>  CComSafeArray::Add

Ajoute un ou plusieurs éléments, ou une `SAFEARRAY` structure, à un `CComSafeArray`.

```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Paramètres

*psaSrc*<br/>
Pointeur vers un objet `SAFEARRAY` .

*ulCount*<br/>
Nombre d’objets à ajouter au tableau.

*pT*<br/>
Pointeur vers un ou plusieurs objets à ajouter au tableau.

*t*<br/>
Référence à l’objet à ajouter au tableau.

*bCopy*<br/>
Indique si une copie des données doit être créée. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Les nouveaux objets sont ajoutés à la fin de l’objet existant `SAFEARRAY` . L’ajout d’un objet à un `SAFEARRAY` objet multidimensionnel n’est pas pris en charge. Lorsque vous ajoutez un tableau d’objets existant, les deux tableaux doivent contenir des éléments du même type.

L’indicateur *bCopy* est pris en compte lorsque des éléments de type BSTR ou variant sont ajoutés à un tableau. La valeur par défaut TRUE garantit qu’une nouvelle copie des données est créée lorsque l’élément est ajouté au tableau.

##  <a name="attach"></a>  CComSafeArray::Attach

Attache une `SAFEARRAY` structure à un `CComSafeArray` objet.

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Paramètres

*psaSrc*<br/>
Pointeur vers la `SAFEARRAY` structure.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Attache une `SAFEARRAY` structure à un `CComSafeArray` objet, ce qui rend les `CComSafeArray` méthodes existantes disponibles.

##  <a name="ccomsafearray"></a>  CComSafeArray::CComSafeArray

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

*bound*<br/>
Structure `SAFEARRAYBOUND`.

*ulCount*<br/>
Nombre d’éléments dans le tableau.

*lLBound*<br/>
Valeur limite inférieure ; autrement dit, l’index du premier élément dans le tableau.

*pBound*<br/>
Pointeur vers une `SAFEARRAYBOUND` structure.

*uDims*<br/>
Nombre de dimensions dans le tableau.

*saSrc*<br/>
Référence à une structure `SAFEARRAY` ou `CComSafeArray` un objet. Dans les deux cas, le constructeur utilise cette référence pour effectuer une copie du tableau, de sorte que le tableau n’est pas référencé après la construction.

*psaSrc*<br/>
Pointeur vers une `SAFEARRAY` structure. Le constructeur utilise cette adresse pour effectuer une copie du tableau, de sorte que le tableau n’est pas référencé après la construction.

### <a name="remarks"></a>Notes

Crée un objet `CComSafeArray`.

##  <a name="dtor"></a>  CComSafeArray::~CComSafeArray

Destructeur.

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

##  <a name="copyfrom"></a>  CComSafeArray::CopyFrom

Copie le contenu d’une `SAFEARRAY` structure dans l' `CComSafeArray` objet.

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Paramètres

*ppArray*<br/>
Pointeur vers le `SAFEARRAY` à copier.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode copie le contenu d’un `SAFEARRAY` dans l’objet `CComSafeArray` actuel. Le contenu existant du tableau est remplacé.

##  <a name="copyto"></a>  CComSafeArray::CopyTo

Crée une copie de l’objet `CComSafeArray`.

```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Paramètres

*ppArray*<br/>
Pointeur vers un emplacement dans lequel créer le nouveau `SAFEARRAY`.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode copie le contenu d’un `CComSafeArray` objet dans une `SAFEARRAY` structure.

##  <a name="create"></a>  CComSafeArray::Create

Crée un `CComSafeArray`.

```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```

### <a name="parameters"></a>Paramètres

*pBound*<br/>
Pointeur vers un objet `SAFEARRAYBOUND` .

*uDims*<br/>
Nombre de dimensions dans le tableau.

*ulCount*<br/>
Nombre d’éléments dans le tableau.

*lLBound*<br/>
Valeur limite inférieure ; autrement dit, l’index du premier élément dans le tableau.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Un `CComSafeArray` objet peut être créé à partir d' `SAFEARRAYBOUND` une structure existante et du nombre de dimensions, ou en spécifiant le nombre d’éléments dans le tableau et la limite inférieure. Si le tableau doit être accessible à partir C++de, la limite inférieure doit être 0. D’autres langages peuvent autoriser d’autres valeurs pour la limite inférieure (par exemple, Visual Basic prend en charge les tableaux avec des éléments avec une plage telle que-10 à 10).

##  <a name="destroy"></a>  CComSafeArray::Destroy

Détruit un objet `CComSafeArray`.

```
HRESULT Destroy();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Détruit un objet existant `CComSafeArray` et toutes les données qu’il contient.

##  <a name="detach"></a>  CComSafeArray::Detach

Détache un `SAFEARRAY` d’un `CComSafeArray` objet.

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers un `SAFEARRAY` objet.

### <a name="remarks"></a>Notes

Cette méthode détache l' `SAFEARRAY` objet de l' `CComSafeArray` objet.

##  <a name="getat"></a>  CComSafeArray::GetAt

Récupère un élément unique à partir d’un tableau unidimensionnel.

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>Paramètres

*lIndex*<br/>
Numéro d’index de la valeur dans le tableau à retourner.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à l’élément de tableau requis.

##  <a name="getcount"></a>  CComSafeArray::GetCount

Retourne le nombre d'éléments du tableau.

```
ULONG GetCount(UINT uDim = 0) const;
```

### <a name="parameters"></a>Paramètres

*uDim*<br/>
Dimension du tableau.

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d'éléments du tableau.

### <a name="remarks"></a>Notes

Lorsqu’elle est utilisée avec un tableau multidimensionnel, cette méthode retourne le nombre d’éléments dans une dimension spécifique uniquement.

##  <a name="getdimensions"></a>  CComSafeArray::GetDimensions

Retourne le nombre de dimensions du tableau.

```
UINT GetDimensions() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de dimensions du tableau.

##  <a name="getlowerbound"></a>  CComSafeArray::GetLowerBound

Retourne la limite inférieure d’une dimension donnée du tableau.

```
LONG GetLowerBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Paramètres

*uDim*<br/>
Dimension du tableau pour laquelle obtenir la limite inférieure. En cas d’omission, la valeur par défaut est 0.

### <a name="return-value"></a>Valeur de retour

Retourne la limite inférieure.

### <a name="remarks"></a>Notes

Si la limite inférieure est 0, cela indique un tableau de type C dont le premier élément est le numéro d’élément 0. En cas d’erreur, par exemple, un argument de dimension non valide, cette méthode appelle `AtlThrow` avec un HRESULT décrivant l’erreur.

##  <a name="getsafearrayptr"></a>  CComSafeArray::GetSafeArrayPtr

Retourne l’adresse du membre de données `m_psa` .

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le membre de données [CComSafeArray :: m_psa](#m_psa) .

##  <a name="gettype"></a>  CComSafeArray::GetType

Retourne le type de données stocké dans le tableau.

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le type de données stockées dans le tableau, qui peut être l’un des types suivants :

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
|VT_R8|Double|
|VT_DECIMAL|pointeur décimal|
|VT_VARIANT|pointeur de type Variant|
|VT_CY|Currency (type de données)|

##  <a name="getupperbound"></a>  CComSafeArray::GetUpperBound

Retourne la limite supérieure d’une dimension du tableau.

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Paramètres

*uDim*<br/>
Dimension du tableau pour laquelle obtenir la limite supérieure. En cas d’omission, la valeur par défaut est 0.

### <a name="return-value"></a>Valeur de retour

Retourne la limite supérieure. Cette valeur est comprise, l’index valide maximal pour cette dimension.

### <a name="remarks"></a>Notes

En cas d’erreur, par exemple, un argument de dimension non valide, cette méthode appelle `AtlThrow` avec un HRESULT décrivant l’erreur.

##  <a name="issizable"></a>  CComSafeArray::IsSizable

Teste si un objet `CComSafeArray` peut être redimensionné.

```
bool IsSizable() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true `CComSafeArray` si le peut être redimensionné, false dans le cas où il ne peut pas.

##  <a name="m_psa"></a>  CComSafeArray::m_psa

Contient l’adresse de la `SAFEARRAY` structure accédée.

```
LPSAFEARRAY m_psa;
```

##  <a name="multidimgetat"></a>  CComSafeArray::MultiDimGetAt

Récupère un élément unique à partir d’un tableau multidimensionnel.

```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```

### <a name="parameters"></a>Paramètres

*alIndex*<br/>
Pointeur vers un vecteur d’index pour chaque dimension du tableau. La dimension la plus à gauche (la `alIndex[0]`plus significative) est.

*t*<br/>
Référence aux données retournées.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="multidimsetat"></a>  CComSafeArray::MultiDimSetAt

Définit la valeur d’un élément d’un tableau multidimensionnel.

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>Paramètres

*alIndex*<br/>
Pointeur vers un vecteur d’index pour chaque dimension du tableau. La dimension la plus à droite (la `alIndex`moins significative) est [0].

*T*<br/>
Spécifie la valeur du nouvel élément.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Il s’agit d’une version multidimensionnelle de [CComSafeArray :: setat](#setat).

##  <a name="operator_at"></a>  CComSafeArray::operator \[\]

Récupère un élément du tableau.

```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```

### <a name="parameters"></a>Paramètres

*lIndex, nIndex*<br/>
Numéro d’index de l’élément requis dans le tableau.

### <a name="return-value"></a>Valeur de retour

Retourne l’élément de tableau approprié.

### <a name="remarks"></a>Notes

Exécute une fonction similaire à [CComSafeArray :: GetAt](#getat), mais cet opérateur fonctionne uniquement avec les tableaux unidimensionnels.

##  <a name="operator_eq"></a>  CComSafeArray::operator =

Opérateur d'assignation.

```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Paramètres

*saSrc*<br/>
Référence à un objet `CComSafeArray`.

*psaSrc*<br/>
Pointeur vers un objet `SAFEARRAY` .

### <a name="return-value"></a>Valeur de retour

Retourne le type de données stocké dans le tableau.

##  <a name="operator_lpsafearray"></a>CComSafeArray :: Operator LPSAFEARRAY

Convertit une valeur en `SAFEARRAY` pointeur.

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>Valeur de retour

Convertit une valeur en `SAFEARRAY` pointeur.

##  <a name="resize"></a>  CComSafeArray::Resize

Redimensionne un objet `CComSafeArray` .

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>Paramètres

*pBound*<br/>
Pointeur vers une `SAFEARRAYBOUND` structure qui contient des informations sur le nombre d’éléments et la limite inférieure d’un tableau.

*ulCount*<br/>
Nombre d’objets demandé dans le tableau redimensionné.

*lLBound*<br/>
Limite inférieure.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode redimensionne uniquement la dimension la plus à droite. Elle ne redimensionne pas les tableaux qui `IsResizable` renvoient la valeur false.

##  <a name="setat"></a>  CComSafeArray::SetAt

Définit la valeur d’un élément d’un tableau unidimensionnel.

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Paramètres

*lIndex*<br/>
Numéro d’index de l’élément de tableau à définir.

*t*<br/>
Nouvelle valeur de l’élément spécifié.

*bCopy*<br/>
Indique si une copie des données doit être créée. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

L’indicateur *bCopy* est pris en compte lorsque des éléments de type BSTR ou variant sont ajoutés à un tableau. La valeur par défaut TRUE garantit qu’une nouvelle copie des données est créée lorsque l’élément est ajouté au tableau.

## <a name="see-also"></a>Voir aussi

[SAFEARRAY (type de données)](/windows/win32/api/oaidl/ns-oaidl-safearray)<br/>
[CComSafeArray::Create](#create)<br/>
[CComSafeArray::Destroy](#destroy)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
