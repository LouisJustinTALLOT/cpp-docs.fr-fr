---
title: CComPtrBase, classe
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
ms.openlocfilehash: 740920225fc513a869b4a92344f87004831e4768
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298609"
---
# <a name="ccomptrbase-class"></a>CComPtrBase, classe

Cette classe fournit une base pour les classes de pointeurs intelligents utilisant des routines de mémoire basées sur COM.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>Parameters

*T*<br/>
Type d’objet à référencer par le pointeur intelligent.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CComPtrBase :: ~ CComPtrBase](#dtor)|Destructeur.|

### <a name="public-methods"></a>Méthodes publiques

|Name|Description|
|----------|-----------------|
|[CComPtrBase :: Advise](#advise)|Appelez cette méthode pour créer une connexion entre le point de connexion de l' `CComPtrBase`et le récepteur d’un client.|
|[CComPtrBase::Attach](#attach)|Appelez cette méthode pour prendre possession d’un pointeur existant.|
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|Appelez cette méthode pour créer un objet de la classe associée à un ID de classe ou un ID de programme spécifié.|
|[CComPtrBase::CopyTo](#copyto)|Appelez cette méthode pour copier le pointeur `CComPtrBase` vers une autre variable pointeur.|
|[CComPtrBase::Detach](#detach)|Appelez cette méthode pour libérer la propriété d’un pointeur.|
|[CComPtrBase::IsEqualObject](#isequalobject)|Appelez cette méthode pour vérifier si le `IUnknown` spécifié pointe vers le même objet associé à l’objet `CComPtrBase`.|
|[CComPtrBase::QueryInterface](#queryinterface)|Appelez cette méthode pour retourner un pointeur vers une interface spécifiée.|
|[CComPtrBase::Release](#release)|Appelez cette méthode pour libérer l’interface.|
|[CComPtrBase::SetSite](#setsite)|Appelez cette méthode pour définir le site de l’objet `CComPtrBase` sur le `IUnknown` de l’objet parent.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[CComPtrBase :: Operator T *](#operator_t_star)|Opérateur de cast.|
|[CComPtrBase :: Operator !](#operator_not)|Opérateur NOT.|
|[CComPtrBase :: operator &](#operator_amp)|Opérateur &.|
|[CComPtrBase :: Operator *](#operator_star)|opérateur \*,|
|[CComPtrBase :: Operator <](#ccomptrbase__operator lt)|Opérateur inférieur à.|
|[CComPtrBase::operator ==](#operator_eq_eq)|Opérateur d’égalité.|
|[CComPtrBase :: operator->](#operator_ptr)|Opérateur pointeur vers membre.|

### <a name="public-data-members"></a>Membres de données publiques

|Name|Description|
|----------|-----------------|
|[CComPtrBase ::p](#p)|Variable de membre de données de pointeur.|

## <a name="remarks"></a>Notes

Cette classe fournit la base pour d’autres pointeurs intelligents qui utilisent des routines de gestion de la mémoire COM, telles que [CComQIPtr](../../atl/reference/ccomqiptr-class.md) et [CComPtr](../../atl/reference/ccomptr-class.md). Les classes dérivées ajoutent leurs propres constructeurs et opérateurs, mais s’appuient sur les méthodes fournies par `CComPtrBase`.

## <a name="requirements"></a>Configuration requise pour

**En-tête :** atlcomcli. h

##  <a name="advise"></a>  CComPtrBase::Advise

Appelez cette méthode pour créer une connexion entre le point de connexion de l' `CComPtrBase`et le récepteur d’un client.

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>Parameters

*pUnk*<br/>
Pointeur vers le `IUnknown`du client.

*iid*<br/>
GUID du point de connexion. En règle générale, il s’agit de l’interface sortante gérée par le point de connexion.

*pdw*<br/>
Pointeur vers le cookie qui identifie de façon unique la connexion.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [AtlAdvise](connection-point-global-functions.md#atladvise) .

##  <a name="attach"></a>  CComPtrBase::Attach

Appelez cette méthode pour prendre possession d’un pointeur existant.

```
void Attach(T* p2) throw();
```

### <a name="parameters"></a>Parameters

*p2*<br/>
L’objet `CComPtrBase` prend la propriété de ce pointeur.

### <a name="remarks"></a>Notes

`Attach` appelle [CComPtrBase :: Release](#release) sur la variable de membre [CComPtrBase ::p](#p) existante, puis affecte *P2* à `CComPtrBase::p`. Lorsqu’un objet `CComPtrBase` prend possession d’un pointeur, il appelle automatiquement `Release` sur le pointeur qui supprime le pointeur et toutes les données allouées si le nombre de références sur l’objet est égal à 0.

##  <a name="dtor"></a>  CComPtrBase::~CComPtrBase

Destructeur.

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>Notes

Libère l’interface vers laquelle pointe `CComPtrBase`.

##  <a name="cocreateinstance"></a>  CComPtrBase::CoCreateInstance

Appelez cette méthode pour créer un objet de la classe associée à un ID de classe ou un ID de programme spécifié.

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

### <a name="parameters"></a>Parameters

*szProgID*<br/>
Pointeur vers un ProgID, utilisé pour récupérer le CLSID.

*pUnkOuter*<br/>
Si la valeur est NULL, cela indique que l’objet n’est pas créé dans le cadre d’un agrégat. Si la valeur est non NULL, est un pointeur vers l’interface `IUnknown` de l’objet d’agrégation (le `IUnknown`de contrôle).

*dwClsContext*<br/>
Contexte dans lequel le code qui gère l’objet nouvellement créé s’exécutera.

*rclsid*<br/>
CLSID associé aux données et au code qui seront utilisés pour créer l’objet.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING ou E_NOINTERFACE en cas d’échec. Pour obtenir une description de ces erreurs, consultez [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) et [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) .

### <a name="remarks"></a>Notes

Si la première forme de la méthode est appelée, [CLSIDFromProgID](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) est utilisé pour récupérer le CLSID. Les deux formes appellent ensuite [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

Dans les versions Debug, une erreur d’assertion se produit si [CComPtrBase ::p](#p) n’est pas égal à null.

##  <a name="copyto"></a>  CComPtrBase::CopyTo

Appelez cette méthode pour copier le pointeur `CComPtrBase` vers une autre variable pointeur.

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>Parameters

*ppT*<br/>
Adresse de la variable qui recevra le pointeur `CComPtrBase`.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, E_POINTER en cas d’échec.

### <a name="remarks"></a>Notes

Copie le pointeur de `CComPtrBase` vers *ppT*. Le décompte de références sur la variable de membre [CComPtrBase ::p](#p) est incrémenté.

Une erreur HRESULT est retournée si *ppT* est égal à null. Dans les versions Debug, une erreur d’assertion se produit si *ppT* est égal à null.

##  <a name="detach"></a>  CComPtrBase::Detach

Appelez cette méthode pour libérer la propriété d’un pointeur.

```
T* Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une copie du pointeur.

### <a name="remarks"></a>Notes

Libère la propriété d’un pointeur, définit la variable de membre de données [CComPtrBase ::p](#p) sur la valeur null et retourne une copie du pointeur.

##  <a name="isequalobject"></a>  CComPtrBase::IsEqualObject

Appelez cette méthode pour vérifier si le `IUnknown` spécifié pointe vers le même objet associé à l’objet `CComPtrBase`.

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>Parameters

*pOther*<br/>
`IUnknown *` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si les objets sont identiques ; sinon, false.

##  <a name="operator_not"></a>CComPtrBase :: Operator !

Opérateur NOT.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si le pointeur de `CComHeapPtr` est égal à NULL ; sinon, false.

##  <a name="operator_amp"></a>CComPtrBase :: Operator &amp;

Opérateur &.

```
T** operator&() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’adresse de l’objet vers lequel pointe l’objet `CComPtrBase`.

##  <a name="operator_star"></a>CComPtrBase :: Operator \*

opérateur \*,

```
T& operator*() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de [CComPtrBase ::p](#p); autrement dit, un pointeur vers l’objet référencé par l’objet `CComPtrBase`.

Si les versions Debug sont générées, une erreur d’assertion se produit si [CComPtrBase ::p](#p) n’est pas égal à null.

##  <a name="operator_eq_eq"></a>  CComPtrBase::operator ==

Opérateur d’égalité.

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>Parameters

*pT*<br/>
Pointeur vers un objet.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si `CComPtrBase` et *PT* pointent vers le même objet ; sinon, false.

##  <a name="operator_ptr"></a>CComPtrBase :: Operator-&gt;

Opérateur pointeur vers membre.

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la variable de membre de données [CComPtrBase ::p](#p) .

### <a name="remarks"></a>Notes

Utilisez cet opérateur pour appeler une méthode dans une classe vers laquelle pointe l’objet `CComPtrBase`. Dans les versions Debug, un échec d’assertion se produit si le membre de données `CComPtrBase` pointe vers la valeur NULL.

##  <a name="operator_lt"></a>CComPtrBase :: Operator &lt;

Opérateur inférieur à.

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>Parameters

*pT*<br/>
Pointeur vers un objet.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si le pointeur managé par l’objet actuel est inférieur au pointeur auquel il est comparé.

##  <a name="operator_t_star"></a>CComPtrBase :: Operator T\*

Opérateur de cast.

```
operator T*() const throw();
```

### <a name="remarks"></a>Notes

Retourne un pointeur vers le type de données objet défini dans le modèle de classe.

##  <a name="p"></a>  CComPtrBase::p

Variable de membre de données de pointeur.

```
T* p;
```

### <a name="remarks"></a>Notes

Cette variable membre contient les informations de pointeur.

##  <a name="queryinterface"></a>  CComPtrBase::QueryInterface

Appelez cette méthode pour retourner un pointeur vers une interface spécifiée.

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>Parameters

*Q*<br/>
Type d’objet dont le pointeur d’interface est requis.

*pp*<br/>
Adresse de la variable de sortie qui reçoit le pointeur d’interface demandé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou E_NOINTERFACE en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode appelle [IUnknown :: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)).

Dans les versions Debug, une erreur d’assertion se produit si *pp* n’est pas égal à null.

##  <a name="release"></a>  CComPtrBase::Release

Appelez cette méthode pour libérer l’interface.

```
void Release() throw();
```

### <a name="remarks"></a>Notes

L’interface est libérée et [CComPtrBase ::p](#p) a la valeur null.

##  <a name="setsite"></a>  CComPtrBase::SetSite

Appelez cette méthode pour définir le site de l’objet `CComPtrBase` sur le `IUnknown` de l’objet parent.

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>Parameters

*punkParent*<br/>
Pointeur vers l’interface `IUnknown` du parent.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode appelle [AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
