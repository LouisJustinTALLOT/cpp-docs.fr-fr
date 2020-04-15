---
title: Classe CComClassFactorySingleton
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: ec860f7ef59b7d3289bf2e18fea0f0e064a7c8f9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320828"
---
# <a name="ccomclassfactorysingleton-class"></a>Classe CComClassFactorySingleton

Cette classe dérive de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un seul objet.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe.

`CComClassFactorySingleton`dérive de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un seul objet. Chaque appel `CreateInstance` à la méthode interroge simplement cet objet pour un pointeur d’interface.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComClassFactorySingleton::CréerInstance](#createinstance)|Requête `m_spObj` pour un pointeur d’interface.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComClassFactorySingleton::m_spObj](#m_spobj)|[L’objet CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) construit par `CComClassFactorySingleton`.|

## <a name="remarks"></a>Notes

Les objets ATL acquièrent normalement une usine de classe en dérivé de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) `CComClassFactory` , qui déclare que l’usine de classe par défaut. Pour `CComClassFactorySingleton`l’utiliser, spécifiez la [macro DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) dans la définition de classe de votre objet. Par exemple :

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomclassfactorysingletoncreateinstance"></a><a name="createinstance"></a>CComClassFactorySingleton::CréerInstance

Appels `QueryInterface` à travers [m_spObj](#m_spobj) pour récupérer un pointeur d’interface.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Paramètres

*pUnkOuter*<br/>
[dans] Si l’objet est créé dans le cadre d’un agrégat, puis *pUnkOuter* doit être l’inconnu extérieur. Sinon, *pUnkOuter* doit être NULL.

*riid*<br/>
[dans] L’IID de l’interface demandée. Si *pUnkOuter* n’est pas- `IID_IUnknown`NULL, *riid* doit être .

*ppvObj*<br/>
[out] Un pointeur au pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppvObj* est réglé sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="ccomclassfactorysingletonm_spobj"></a><a name="m_spobj"></a>CComClassFactorySingleton::m_spObj

[L’objet CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) construit par `CComClassFactorySingleton`.

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>Notes

Chaque appel à la méthode [CreateInstance](#createinstance) interroge simplement cet objet pour un pointeur d’interface.

Notez que la `m_spObj` forme actuelle de présente `CComClassFactorySingleton` un changement de rupture de la façon dont cela a fonctionné dans les versions précédentes de ATL. Dans les versions précédentes, l’objet `CComClassFactorySingleton` a été créé en même temps que l’usine de classe, lors de l’initialisation du serveur. Dans Visual C.NET 2003 et plus tard, l’objet est créé paresseusement, à la première demande. Ce changement pourrait causer des erreurs dans les programmes qui reposent sur l’initialisation précoce.

## <a name="see-also"></a>Voir aussi

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[Classe CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)<br/>
[Classe CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[Classe CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
