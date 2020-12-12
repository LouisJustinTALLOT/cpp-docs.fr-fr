---
description: 'En savoir plus sur : classe CComClassFactoryAutoThread'
title: CComClassFactoryAutoThread, classe
ms.date: 11/04/2016
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
ms.openlocfilehash: 9d25303d4d40f695c68fdf09aae7d56e6f1e5fb1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152280"
---
# <a name="ccomclassfactoryautothread-class"></a>CComClassFactoryAutoThread, classe

Cette classe implémente l’interface [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) et permet la création d’objets dans plusieurs cloisonnements.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComClassFactoryAutoThread
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComClassFactoryAutoThread :: CreateInstance](#createinstance)|Crée un objet du CLSID spécifié.|
|[CComClassFactoryAutoThread :: LockServer,](#lockserver)|Verrouille la fabrique de classe en mémoire.|

## <a name="remarks"></a>Notes

`CComClassFactoryAutoThread` est semblable à [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), mais permet la création d’objets dans plusieurs cloisonnements. Pour tirer parti de cette prise en charge, dérivez votre module EXE de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Les objets ATL acquièrent normalement une fabrique de classe en dérivant de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), qui déclare [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme fabrique de classe par défaut. Pour utiliser `CComClassFactoryAutoThread` , spécifiez la macro [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) dans la définition de classe de votre objet. Par exemple :

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="ccomclassfactoryautothreadcreateinstance"></a><a name="createinstance"></a> CComClassFactoryAutoThread :: CreateInstance

Crée un objet du CLSID spécifié et récupère un pointeur d’interface vers cet objet.

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
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

### <a name="remarks"></a>Notes

Si votre module dérive de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), `CreateInstance` sélectionne d’abord un thread pour créer l’objet dans le cloisonnement associé.

## <a name="ccomclassfactoryautothreadlockserver"></a><a name="lockserver"></a> CComClassFactoryAutoThread :: LockServer,

Incrémente et décrémente le nombre de verrous de module en appelant `_Module::Lock` et `_Module::Unlock` , respectivement.

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>Paramètres

*Troupeau*<br/>
dans Si la valeur est TRUE, le nombre de verrous est incrémenté ; dans le cas contraire, le nombre de verrous est décrémenté.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Lors de l’utilisation `CComClassFactoryAutoThread` `_Module` de, fait généralement référence à l’instance globale de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

L’appel de `LockServer` permet à un client de conserver une fabrique de classes pour que plusieurs objets puissent être créés rapidement.

## <a name="see-also"></a>Voir aussi

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2, classe](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactorySingleton, classe](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx (classe)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
