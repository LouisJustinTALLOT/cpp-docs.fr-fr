---
title: Classe CComPtrBase
ms.date: 11/04/2016
f1_keywords:
- CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase::Advise
- ATLCOMCLI/ATL::CComPtrBase::Attach
- ATLCOMCLI/ATL::CComPtrBase::CoCreateInstance
- ATLCOMCLI/ATL::CComPtrBase::CopyTo
- ATLCOMCLI/ATL::CComPtrBase::Detach
- ATLCOMCLI/ATL::CComPtrBase::IsEqualObject
- ATLCOMCLI/ATL::CComPtrBase::QueryInterface
- ATLCOMCLI/ATL::CComPtrBase::Release
- ATLCOMCLI/ATL::CComPtrBase::SetSite
- ATLCOMCLI/ATL::CComPtrBase::p
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
ms.openlocfilehash: 9c62cc912b3fea3ea68390882bdda37cbfb25a7e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747758"
---
# <a name="ccomptrbase-class"></a>Classe CComPtrBase

Cette classe fournit une base pour les classes de pointeurs intelligents en utilisant des routines de mémoire basées sur com.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type d’objet à référencé par le pointeur intelligent.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComPtrBase: CComPtrBase](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComPtrBase::Conseiller](#advise)|Appelez cette méthode pour créer `CComPtrBase`une connexion entre le point de connexion de l’un et l’évier d’un client.|
|[CComPtrBase::Attach](#attach)|Appelez cette méthode pour prendre possession d’un pointeur existant.|
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|Appelez cette méthode pour créer un objet de la classe associé à une pièce d’identité de classe ou une pièce d’identité spécifiée.|
|[CComPtrBase::CopyTo](#copyto)|Appelez cette méthode `CComPtrBase` pour copier le pointeur à une autre variable de pointeur.|
|[CComPtrBase::Detach](#detach)|Appelez cette méthode pour libérer la propriété d’un pointeur.|
|[CComPtrBase::IsEqualObject](#isequalobject)|Appelez cette méthode pour `IUnknown` vérifier si les points `CComPtrBase` spécifiés vers le même objet associé à l’objet.|
|[CComPtrBase::QueryInterface](#queryinterface)|Appelez cette méthode pour retourner un pointeur à une interface spécifiée.|
|[CComPtrBase::Libération](#release)|Appelez cette méthode pour libérer l’interface.|
|[CComPtrBase::SetSite](#setsite)|Appelez cette méthode pour définir `CComPtrBase` le `IUnknown` site de l’objet à l’objet parent.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CComPtrBase::opérateur T](#operator_t_star)|L’opérateur de distribution.|
|[CComPtrBase::opérateur !](#operator_not)|L’opérateur NON.|
|[CComPtrBase::opérateur &](#operator_amp)|Opérateur &.|
|[CComPtrBase::opérateur](#operator_star)|opérateur \*,|
|[CComPtrBase::opérateur <](#ccomptrbase__operator lt)|Le moins-que l’opérateur.|
|[CComPtrBase::opérateur](#operator_eq_eq)|L’opérateur de l’égalité.|
|[CComPtrBase::opérateur ->](#operator_ptr)|L’opérateur pointeur-à-membres.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComPtrBase::p](#p)|La variable de membre des données de pointeur.|

## <a name="remarks"></a>Notes

Cette classe fournit la base pour d’autres pointeurs intelligents qui utilisent des routines de gestion de la mémoire COM, tels que [CComQIPtr](../../atl/reference/ccomqiptr-class.md) et [CComPtr](../../atl/reference/ccomptr-class.md). Les classes dérivées ajoutent leurs propres constructeurs et `CComPtrBase`opérateurs, mais s’appuient sur les méthodes fournies par .

## <a name="requirements"></a>Spécifications

**En-tête:** atlcomcli.h

## <a name="ccomptrbaseadvise"></a><a name="advise"></a>CComPtrBase::Conseiller

Appelez cette méthode pour créer `CComPtrBase`une connexion entre le point de connexion de l’un et l’évier d’un client.

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
Un pointeur pour `IUnknown`le client .

*Iid*<br/>
Le GUID du point de connexion. Typiquement, c’est la même chose que l’interface sortante gérée par le point de connexion.

*Pdw*<br/>
Un pointeur vers le cookie qui identifie uniquement la connexion.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Voir [AtlAdvise](connection-point-global-functions.md#atladvise) pour plus d’informations.

## <a name="ccomptrbaseattach"></a><a name="attach"></a>CComPtrBase::Attach

Appelez cette méthode pour prendre possession d’un pointeur existant.

```cpp
void Attach(T* p2) throw();
```

### <a name="parameters"></a>Paramètres

*p2*<br/>
L’objet `CComPtrBase` s’appropriera ce pointeur.

### <a name="remarks"></a>Notes

`Attach`appelle [CComPtrBase::Release](#release) on the existing [CComPtrBase::p](#p) member variable and `CComPtrBase::p`then assigns *p2* to . Lorsqu’un `CComPtrBase` objet prend possession d’un `Release` pointeur, il fait automatiquement appel au pointeur qui supprimera le pointeur et les données allouées si le nombre de références sur l’objet passe à 0.

## <a name="ccomptrbaseccomptrbase"></a><a name="dtor"></a>CComPtrBase: CComPtrBase

Destructeur.

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>Notes

Libère l’interface `CComPtrBase`pointée par .

## <a name="ccomptrbasecocreateinstance"></a><a name="cocreateinstance"></a>CComPtrBase::CoCreateInstance

Appelez cette méthode pour créer un objet de la classe associé à une pièce d’identité de classe ou une pièce d’identité spécifiée.

```
HRESULT CoCreateInstance(
    LPCOLESTR szProgID,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();

HRESULT CoCreateInstance(
    REFCLSID rclsid,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();
```

### <a name="parameters"></a>Paramètres

*szProgID*<br/>
Pointeur à un ProgID, utilisé pour récupérer le CLSID.

*pUnkOuter*<br/>
Si NULL, indique que l’objet n’est pas créé dans le cadre d’un agrégat. Si non- NULL, est un pointeur `IUnknown` à l’interface de l’objet agrégé (le contrôle `IUnknown`).

*dwClsContexte*<br/>
Contexte dans lequel le code qui gère l’objet nouvellement créé s’exécutera.

*rclsid*<br/>
CLSID associé aux données et au code qui seront utilisés pour créer l’objet.

### <a name="return-value"></a>Valeur de retour

Retours S_OK sur le succès, ou REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING ou E_NOINTERFACE sur l’échec. Voir [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) et [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) pour une description de ces erreurs.

### <a name="remarks"></a>Notes

Si la première forme de la méthode est appelée, [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) est utilisé pour récupérer le CLSID. Les deux formulaires appellent ensuite [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

Dans les constructions de débog, une erreur d’affirmation se produira si [CComPtrBase::p](#p) n’est pas égal à NULL.

## <a name="ccomptrbasecopyto"></a><a name="copyto"></a>CComPtrBase::CopyTo

Appelez cette méthode `CComPtrBase` pour copier le pointeur à une autre variable de pointeur.

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>Paramètres

*Ppt*<br/>
Adresse de la variable `CComPtrBase` qui recevra le pointeur.

### <a name="return-value"></a>Valeur de retour

Retours S_OK sur le succès, E_POINTER sur l’échec.

### <a name="remarks"></a>Notes

Copies `CComPtrBase` du pointeur à *ppT*. Le compte de référence sur la [CComPtrBase::p](#p) variable de membre est incrémenté.

Une erreur HRESULT sera retournée si *ppT* est égal à NULL. Dans les constructions de débog, une erreur d’affirmation se produira si *ppT* est égal à NULL.

## <a name="ccomptrbasedetach"></a><a name="detach"></a>CComPtrBase::Detach

Appelez cette méthode pour libérer la propriété d’un pointeur.

```
T* Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une copie du pointeur.

### <a name="remarks"></a>Notes

Libère la propriété d’un pointeur, définit la variable de membre de données [CComPtrBase::p](#p) à NULL, et renvoie une copie du pointeur.

## <a name="ccomptrbaseisequalobject"></a><a name="isequalobject"></a>CComPtrBase::IsEqualObject

Appelez cette méthode pour `IUnknown` vérifier si les points `CComPtrBase` spécifiés vers le même objet associé à l’objet.

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>Paramètres

*pOther*<br/>
`IUnknown *` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si les objets sont identiques, faux autrement.

## <a name="ccomptrbaseoperator-"></a><a name="operator_not"></a>CComPtrBase::opérateur !

L’opérateur NON.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne vrai `CComHeapPtr` si le pointeur est égal à NULL, faux autrement.

## <a name="ccomptrbaseoperator-amp"></a><a name="operator_amp"></a>CComPtrBase::opérateur&amp;

Opérateur &.

```
T** operator&() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’adresse de l’objet pointée par l’objet. `CComPtrBase`

## <a name="ccomptrbaseoperator-"></a><a name="operator_star"></a>CComPtrBase::opérateur\*

opérateur \*,

```
T& operator*() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de [CComPtrBase::p](#p); c’est-à-dire un pointeur `CComPtrBase` de l’objet référencé par l’objet.

Si le débogé se construit, une erreur d’affirmation se produira si [CComPtrBase::p](#p) n’est pas égal à NULL.

## <a name="ccomptrbaseoperator-"></a><a name="operator_eq_eq"></a>CComPtrBase::opérateur

L’opérateur de l’égalité.

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
Un pointeur à un objet.

### <a name="return-value"></a>Valeur de retour

Retourne vrai `CComPtrBase` si et *pT* point vers le même objet, faux autrement.

## <a name="ccomptrbaseoperator--gt"></a><a name="operator_ptr"></a>CComPtrBase::opérateur -&gt;

L’opérateur pointeur-à-membre.

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la variable de membre de données [CComPtrBase::p.](#p)

### <a name="remarks"></a>Notes

Utilisez cet opérateur pour appeler une méthode `CComPtrBase` dans une classe pointée par l’objet. Dans les constructions de débog, `CComPtrBase` une défaillance d’affirmation se produira si le membre de données indique NULL.

## <a name="ccomptrbaseoperator-lt"></a><a name="operator_lt"></a>CComPtrBase::opérateur&lt;

Le moins-que l’opérateur.

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
Un pointeur à un objet.

### <a name="return-value"></a>Valeur de retour

Rendements vrais si le pointeur géré par l’objet actuel est inférieur au pointeur auquel il est comparé.

## <a name="ccomptrbaseoperator-t"></a><a name="operator_t_star"></a>CComPtrBase::opérateur T\*

L’opérateur de distribution.

```
operator T*() const throw();
```

### <a name="remarks"></a>Notes

Renvoie un pointeur au type de données d’objet défini dans le modèle de classe.

## <a name="ccomptrbasep"></a><a name="p"></a>CComPtrBase::p

La variable de membre des données de pointeur.

```
T* p;
```

### <a name="remarks"></a>Notes

Cette variable de membre contient l’information de pointeur.

## <a name="ccomptrbasequeryinterface"></a><a name="queryinterface"></a>CComPtrBase::QueryInterface

Appelez cette méthode pour retourner un pointeur à une interface spécifiée.

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>Paramètres

*Q*<br/>
Le type d’objet dont le pointeur d’interface est nécessaire.

*Pp*<br/>
Adresse de la variable de sortie qui reçoit le pointeur d’interface demandé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou E_NOINTERFACE sur l’échec.

### <a name="remarks"></a>Notes

Cette méthode appelle [IUnknown:QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)).

Dans les constructions de débog, une erreur d’affirmation se produira si *pp* n’est pas égal à NULL.

## <a name="ccomptrbaserelease"></a><a name="release"></a>CComPtrBase::Libération

Appelez cette méthode pour libérer l’interface.

```cpp
void Release() throw();
```

### <a name="remarks"></a>Notes

L’interface est libérée, et [CComPtrBase::p](#p) est réglé sur NULL.

## <a name="ccomptrbasesetsite"></a><a name="setsite"></a>CComPtrBase::SetSite

Appelez cette méthode pour définir `CComPtrBase` le `IUnknown` site de l’objet à l’objet parent.

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>Paramètres

*punkParent (punkParent)*<br/>
Un pointeur `IUnknown` à l’interface du parent.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette méthode appelle [AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
