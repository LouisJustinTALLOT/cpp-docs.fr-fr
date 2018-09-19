---
title: CComSafeArray, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComSafeArray class
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 411b8f58b38d2b35c1353d1ff446407026977d66
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030142"
---
# <a name="ccomsafearray-class"></a>CComSafeArray, classe

Cette classe est un wrapper pour le `SAFEARRAY` structure.

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
|[CComSafeArray :: ~ CComSafeArray](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComSafeArray::Add](#add)|Ajoute un ou plusieurs éléments, ou un `SAFEARRAY` structure, à un `CComSafeArray`.|
|[CComSafeArray::Attach](#attach)|Attache un `SAFEARRAY` structure un `CComSafeArray` objet.|
|[CComSafeArray::CopyFrom](#copyfrom)|Copie le contenu d’un `SAFEARRAY` structure dans le `CComSafeArray` objet.|
|[CComSafeArray::CopyTo](#copyto)|Crée une copie de l’objet `CComSafeArray`.|
|[CComSafeArray::Create](#create)|Crée un objet `CComSafeArray`.|
|[CComSafeArray::Destroy](#destroy)|Détruit un objet `CComSafeArray`.|
|[CComSafeArray::Detach](#detach)|Détache un `SAFEARRAY` à partir d’un `CComSafeArray` objet.|
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
|[CComSafeArray::operator LPSAFEARRAY](#operator_lpsafearray)|Convertit une valeur dans un `SAFEARRAY` pointeur.|
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|Récupère un élément du tableau.|
|[CComSafeArray::operator =](#operator_eq)|Opérateur d'assignation.|  

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComSafeArray::m_psa](#m_psa)|Ce membre de données conserve l’adresse de la `SAFEARRAY` structure.|

## <a name="remarks"></a>Notes

`CComSafeArray` fournit un wrapper pour le [SAFEARRAY Data Type](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagsafearray) (classe), rendant très simple de créer et gérer des tableaux unidimensionnels et multidimensionnels de pratiquement n’importe quel les types prenant en charge VARIANT.

`CComSafeArray` simplifie le transmission de tableaux entre processus et offre en outre une sécurité renforcée en vérifiant les valeurs d’index de tableau par rapport aux limites inférieure et supérieure.

La limite inférieure d’un `CComSafeArray` peut commencer à n’importe quelle valeur définie par l’utilisateur ; cependant, les tableaux accessibles via C++ doivent utiliser une limite inférieure de 0. D’autres langages comme Visual Basic peuvent utiliser d’autres valeurs de délimitation (par exemple, de -10 à 10).

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

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsafe.h

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]

##  <a name="add"></a>  CComSafeArray::Add

Ajoute un ou plusieurs éléments, ou un `SAFEARRAY` structure, à un `CComSafeArray`.

```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Paramètres

*psaSrc*<br/>
Un pointeur vers un `SAFEARRAY` objet.

*ulCount*<br/>
Le nombre d’objets à ajouter au tableau.

*pT*<br/>
Pointeur vers un ou plusieurs objets à ajouter au tableau.

*t*<br/>
Une référence à l’objet à ajouter au tableau.

*bCopy*<br/>
Indique si une copie des données doit être créée. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Les nouveaux objets sont ajoutés à la fin de l’existante `SAFEARRAY` objet. Ajout d’un objet à un multidimensionnelles `SAFEARRAY` objet n’est pas pris en charge. Lorsque vous ajoutez un tableau d’objets existant, les deux tableaux doit contenir des éléments du même type.

Le *bCopy* indicateur est pris en compte lorsque des éléments de type BSTR ou type VARIANT sont ajoutés à un tableau. La valeur par défaut true garantit qu’une nouvelle copie est effectuée des données lors de l’élément est ajouté au tableau.

##  <a name="attach"></a>  CComSafeArray::Attach

Attache un `SAFEARRAY` structure un `CComSafeArray` objet.

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Paramètres

*psaSrc*<br/>
Un pointeur vers le `SAFEARRAY` structure.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Attache un `SAFEARRAY` structure un `CComSafeArray` objet, en rendant existant `CComSafeArray` méthodes disponibles.

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

*lié*<br/>
Structure `SAFEARRAYBOUND`.

*ulCount*<br/>
Nombre d’éléments dans le tableau.

*lLBound*<br/>
La valeur de la limite inférieure ; Autrement dit, l’index du premier élément du tableau.

*pBound*<br/>
Un pointeur vers un `SAFEARRAYBOUND` structure.

*uDims*<br/>
Le nombre de dimensions dans le tableau.

*saSrc*<br/>
Une référence à un `SAFEARRAY` structure ou `CComSafeArray` objet. Dans les deux cas, le constructeur utilise cette référence pour effectuer une copie du tableau, donc le tableau n’est pas référencé après la construction.

*psaSrc*<br/>
Un pointeur vers un `SAFEARRAY` structure. Le constructeur utilise cette adresse pour effectuer une copie du tableau, donc le tableau n’est pas référencé après la construction.

### <a name="remarks"></a>Notes

Crée un objet `CComSafeArray`.

##  <a name="dtor"></a>  CComSafeArray :: ~ CComSafeArray

Destructeur.

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

##  <a name="copyfrom"></a>  CComSafeArray::CopyFrom

Copie le contenu d’un `SAFEARRAY` structure dans le `CComSafeArray` objet.

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Paramètres

*ppArray*<br/>
Pointeur vers le `SAFEARRAY` à copier.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode copie le contenu d’un `SAFEARRAY` dans la zone actuelle `CComSafeArray` objet. Le contenu existant du tableau est remplacé.

##  <a name="copyto"></a>  CComSafeArray::CopyTo

Crée une copie de l’objet `CComSafeArray`.

```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Paramètres

*ppArray*<br/>
Un pointeur vers un emplacement dans lequel créer le nouveau `SAFEARRAY`.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode copie le contenu d’un `CComSafeArray` de l’objet dans un `SAFEARRAY` structure.

##  <a name="create"></a>  CComSafeArray::Create

Crée un `CComSafeArray`.

```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```

### <a name="parameters"></a>Paramètres

*pBound*<br/>
Un pointeur vers un `SAFEARRAYBOUND` objet.

*uDims*<br/>
Le nombre de dimensions dans le tableau.

*ulCount*<br/>
Nombre d’éléments dans le tableau.

*lLBound*<br/>
La valeur de la limite inférieure ; Autrement dit, l’index du premier élément du tableau.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Un `CComSafeArray` objet peut être créé à partir d’un existant `SAFEARRAYBOUND` structure et le nombre de dimensions ou en spécifiant le nombre d’éléments du tableau et la limite inférieure. Si le tableau est accessible à partir de Visual C++, la limite inférieure doit être 0. Autres langages peuvent autoriser d’autres valeurs de la limite inférieure (par exemple, les tableaux Visual prend en charge de base avec des éléments avec une plage comme -10 à 10).

##  <a name="destroy"></a>  CComSafeArray::Destroy

Détruit un objet `CComSafeArray`.

```
HRESULT Destroy();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Détruit un existant `CComSafeArray` objet et toutes les données qu’il contient.

##  <a name="detach"></a>  CComSafeArray::Detach

Détache un `SAFEARRAY` à partir d’un `CComSafeArray` objet.

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers un `SAFEARRAY` objet.

### <a name="remarks"></a>Notes

Cette méthode détache le `SAFEARRAY` de l’objet à partir de la `CComSafeArray` objet.

##  <a name="getat"></a>  CComSafeArray::GetAt

Récupère un élément unique à partir d’un tableau unidimensionnel.

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>Paramètres

*lIndex Valeur de type*<br/>
Le numéro d’index de la valeur dans le tableau à retourner.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à l’élément de tableau requis.

##  <a name="getcount"></a>  CComSafeArray::GetCount

Retourne le nombre d'éléments du tableau.

```
ULONG GetCount(UINT uDim = 0) const;
```

### <a name="parameters"></a>Paramètres

*uDim*<br/>
La dimension du tableau.

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d'éléments du tableau.

### <a name="remarks"></a>Notes

Lorsqu’il est utilisé avec un tableau multidimensionnel, cette méthode retourne le nombre d’éléments dans une dimension spécifique uniquement.

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
La dimension de tableau pour lequel obtenir la limite inférieure. Si omis, la valeur par défaut est 0.

### <a name="return-value"></a>Valeur de retour

Retourne la limite inférieure.

### <a name="remarks"></a>Notes

Si la limite inférieure est 0, cela indique un tableau de type C dont le premier élément est l’élément numéro 0. En cas d’erreur, par exemple, un argument de dimension non valide, cette méthode appelle `AtlThrow` avec un HRESULT qui décrit l’erreur.

##  <a name="getsafearrayptr"></a>  CComSafeArray::GetSafeArrayPtr

Retourne l’adresse du membre de données `m_psa` .

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le [CComSafeArray::m_psa](#m_psa) membre de données.

##  <a name="gettype"></a>  CComSafeArray::GetType

Retourne le type de données stocké dans le tableau.

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le type de données stockées dans le tableau, ce qui peut être un des types suivants :

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

##  <a name="getupperbound"></a>  CComSafeArray::GetUpperBound

Retourne la limite supérieure d’une dimension du tableau.

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Paramètres

*uDim*<br/>
La dimension de tableau pour lequel obtenir la limite supérieure. Si omis, la valeur par défaut est 0.

### <a name="return-value"></a>Valeur de retour

Retourne la limite supérieure. Cette valeur est inclusive, l’index valide maximale pour cette dimension.

### <a name="remarks"></a>Notes

En cas d’erreur, par exemple, un argument de dimension non valide, cette méthode appelle `AtlThrow` avec un HRESULT qui décrit l’erreur.

##  <a name="issizable"></a>  CComSafeArray::IsSizable

Teste si un objet `CComSafeArray` peut être redimensionné.

```
bool IsSizable() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le `CComSafeArray` peut être redimensionné, FALSE s’il ne peut pas.

##  <a name="m_psa"></a>  CComSafeArray::m_psa

Contient l’adresse de la `SAFEARRAY` structure accédé.

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
Pointeur vers un vecteur d’index pour chaque dimension du tableau. La dimension (le plus significative) à l’extrême gauche est `alIndex[0]`.

*t*<br/>
Une référence aux données retournées.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

##  <a name="multidimsetat"></a>  CComSafeArray::MultiDimSetAt

Définit la valeur d’un élément d’un tableau multidimensionnel.

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>Paramètres

*alIndex*<br/>
Pointeur vers un vecteur d’index pour chaque dimension du tableau. La dimension (moins significatif) plus à droite est `alIndex`[0].

*T*<br/>
Spécifie la valeur du nouvel élément.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Il s’agit d’une version multidimensionnelle de [CComSafeArray::SetAt](#setat).

##  <a name="operator_at"></a>  CComSafeArray::operator \[\]

Récupère un élément du tableau.

```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```

### <a name="parameters"></a>Paramètres

*lIndex Valeur de type, nIndex*<br/>
Numéro d’index de l’élément requis dans le tableau.

### <a name="return-value"></a>Valeur de retour

Retourne l’élément de tableau approprié.

### <a name="remarks"></a>Notes

Exécute une fonction similaire à [CComSafeArray::GetAt](#getat), mais cet opérateur fonctionne uniquement avec les tableaux unidimensionnels.

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
Un pointeur vers un `SAFEARRAY` objet.

### <a name="return-value"></a>Valeur de retour

Retourne le type de données stocké dans le tableau.

##  <a name="operator_lpsafearray"></a>  CComSafeArray::operator LPSAFEARRAY

Convertit une valeur dans un `SAFEARRAY` pointeur.

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>Valeur de retour

Convertit une valeur dans un `SAFEARRAY` pointeur.

##  <a name="resize"></a>  CComSafeArray::Resize

Redimensionne un objet `CComSafeArray` .

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>Paramètres

*pBound*<br/>
Un pointeur vers un `SAFEARRAYBOUND` structure qui contient des informations sur le nombre d’éléments et la limite inférieure du tableau.

*ulCount*<br/>
Le nombre demandé d’objets dans le tableau redimensionné.

*lLBound*<br/>
La limite inférieure.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode redimensionne uniquement la dimension la plus à droite. Celui-ci se redimensionne pas les tableaux qui retournent `IsResizable` comme FALSE.

##  <a name="setat"></a>  CComSafeArray::SetAt

Définit la valeur d’un élément d’un tableau unidimensionnel.

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Paramètres

*lIndex Valeur de type*<br/>
Numéro d’index de l’élément de tableau à définir.

*t*<br/>
La nouvelle valeur de l’élément spécifié.

*bCopy*<br/>
Indique si une copie des données doit être créée. La valeur par défaut est TRUE.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Le *bCopy* indicateur est pris en compte lorsque des éléments de type BSTR ou type VARIANT sont ajoutés à un tableau. La valeur par défaut true garantit qu’une nouvelle copie est effectuée des données lors de l’élément est ajouté au tableau.

## <a name="see-also"></a>Voir aussi

[Type de données SAFEARRAY](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagsafearray)<br/>
[CComSafeArray::Create](#create)<br/>
[CComSafeArray::Destroy](#destroy)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
