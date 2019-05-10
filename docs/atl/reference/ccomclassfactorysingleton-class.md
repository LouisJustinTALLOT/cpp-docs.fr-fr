---
title: Ccomclassfactorysingleton, classe
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: c415da15341f7800a706379d991cb753f5991170
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221175"
---
# <a name="ccomclassfactorysingleton-class"></a>Ccomclassfactorysingleton, classe

Cette classe est dérivée de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un objet unique.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe.

`CComClassFactorySingleton` dérive de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un objet unique. Chaque appel à la `CreateInstance` méthode interroge simplement cet objet pour un pointeur d’interface.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComClassFactorySingleton::CreateInstance](#createinstance)|Requêtes `m_spObj` pour un pointeur d’interface.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComClassFactorySingleton::m_spObj](#m_spobj)|Le [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objet construit par `CComClassFactorySingleton`.|

## <a name="remarks"></a>Notes

Objets ATL acquièrent normalement une fabrique de classe en dérivant de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe inclut la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), qui déclare `CComClassFactory` en tant que la fabrique de classe par défaut. Pour utiliser `CComClassFactorySingleton`, spécifiez la [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) macro dans la définition de classe de votre objet. Exemple :

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="createinstance"></a>  CComClassFactorySingleton::CreateInstance

Appels `QueryInterface` via [m_spObj](#m_spobj) pour récupérer un pointeur d’interface.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Paramètres

*pUnkOuter*<br/>
[in] Si l’objet est créé dans le cadre d’un agrégat, puis *pUnkOuter* doit être inconnu externe. Sinon, *pUnkOuter* doit être NULL.

*riid*<br/>
[in] IID de l’interface demandée. Si *pUnkOuter* n’est pas NULL, *riid* doit être `IID_IUnknown`.

*ppvObj*<br/>
[out] Un pointeur vers le pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppvObj* est définie sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="m_spobj"></a>  CComClassFactorySingleton::m_spObj

Le [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objet construit par `CComClassFactorySingleton`.

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>Notes

Chaque appel à la [CreateInstance](#createinstance) méthode interroge simplement cet objet pour un pointeur d’interface.

Notez que le formulaire actuel de `m_spObj` présente une modification avec rupture à partir de la façon qui `CComClassFactorySingleton` travaillé dans les versions précédentes de l’ATL. Dans les versions précédentes du `CComClassFactorySingleton` objet a été créé en même temps que la fabrique de classe, lors de l’initialisation du serveur. Dans Visual C++.NET 2003 et versions ultérieures, l’objet est créé de manière différée, à la première demande. Cette modification peut provoquer des erreurs dans les programmes qui s’appuient sur l’initialisation anticipée.

## <a name="see-also"></a>Voir aussi

[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2, classe](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactoryAutoThread, classe](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComObjectRootEx, classe](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
