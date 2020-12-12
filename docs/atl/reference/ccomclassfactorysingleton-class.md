---
description: 'En savoir plus sur : classe CComClassFactorySingleton'
title: CComClassFactorySingleton, classe
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: eaf09f823a6d8d62f102e6e36116b56270248f9e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146859"
---
# <a name="ccomclassfactorysingleton-class"></a>CComClassFactorySingleton, classe

Cette classe dérive de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un objet unique.

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

`CComClassFactorySingleton` dérive de [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) et utilise [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) pour construire un objet unique. Chaque appel à la `CreateInstance` méthode interroge simplement cet objet pour obtenir un pointeur d’interface.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComClassFactorySingleton :: CreateInstance](#createinstance)|Interroge `m_spObj` un pointeur d’interface.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComClassFactorySingleton :: m_spObj](#m_spobj)|Objet [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) construit par `CComClassFactorySingleton` .|

## <a name="remarks"></a>Notes

Les objets ATL acquièrent normalement une fabrique de classe en dérivant de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), qui déclare `CComClassFactory` comme fabrique de classe par défaut. Pour utiliser `CComClassFactorySingleton` , spécifiez la macro [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) dans la définition de classe de votre objet. Par exemple :

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="ccomclassfactorysingletoncreateinstance"></a><a name="createinstance"></a> CComClassFactorySingleton :: CreateInstance

Appelle `QueryInterface` via [m_spObj](#m_spobj) pour récupérer un pointeur d’interface.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Paramètres

*pUnkOuter*<br/>
dans Si l’objet est créé dans le cadre d’un agrégat, *pUnkOuter* doit être l’élément externe inconnu. Sinon, *pUnkOuter* doit avoir la valeur null.

*riid*<br/>
dans IID de l’interface demandée. Si *pUnkOuter* n’est pas null, *riid* doit avoir la valeur `IID_IUnknown` .

*ppvObj*<br/>
à Pointeur vers le pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppvObj* a la valeur null.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="ccomclassfactorysingletonm_spobj"></a><a name="m_spobj"></a> CComClassFactorySingleton :: m_spObj

Objet [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) construit par `CComClassFactorySingleton` .

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>Notes

Chaque appel à la méthode [CreateInstance](#createinstance) interroge simplement cet objet pour obtenir un pointeur d’interface.

Notez que la forme actuelle de `m_spObj` présente une modification avec rupture par rapport à la façon dont `CComClassFactorySingleton` fonctionnait les versions précédentes d’ATL. Dans les versions précédentes `CComClassFactorySingleton` , l’objet a été créé en même temps que la fabrique de classe, pendant l’initialisation du serveur. Dans Visual C++ .NET 2003 et versions ultérieures, l’objet est créé de manière différée, à la première demande. Cette modification peut provoquer des erreurs dans les programmes qui reposent sur une initialisation précoce.

## <a name="see-also"></a>Voir aussi

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2, classe](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactoryAutoThread, classe](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComObjectRootEx (classe)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
