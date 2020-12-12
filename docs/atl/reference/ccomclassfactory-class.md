---
description: 'En savoir plus sur : classe CComClassFactory'
title: CComClassFactory, classe
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
ms.openlocfilehash: 36233abf13c6ff6963d02bc5431286ca6c783235
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152293"
---
# <a name="ccomclassfactory-class"></a>CComClassFactory, classe

Cette classe implémente l’interface [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) .

## <a name="syntax"></a>Syntaxe

```
class CComClassFactory
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComClassFactory :: CreateInstance](#createinstance)|Crée un objet du CLSID spécifié.|
|[CComClassFactory :: LockServer,](#lockserver)|Verrouille la fabrique de classe en mémoire.|

## <a name="remarks"></a>Notes

`CComClassFactory` implémente l’interface [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) , qui contient des méthodes pour créer un objet d’un CLSID particulier, ainsi que le verrouillage de la fabrique de classe en mémoire pour permettre la création plus rapide de nouveaux objets. `IClassFactory` doit être implémentée pour chaque classe que vous inscrivez dans le registre système et pour laquelle vous affectez un CLSID.

Les objets ATL acquièrent normalement une fabrique de classe en dérivant de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), qui déclare `CComClassFactory` comme fabrique de classe par défaut. Pour remplacer cette valeur par défaut, spécifiez l’une des `DECLARE_CLASSFACTORY` macros *xxx* dans votre définition de classe. Par exemple, la macro [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) utilise la classe spécifiée pour la fabrique de classe :

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

La définition de classe ci-dessus spécifie que `CMyClassFactory` sera utilisé comme fabrique de classe par défaut de l’objet. `CMyClassFactory` doit dériver de `CComClassFactory` et substituer `CreateInstance` .

ATL fournit trois autres macros qui déclarent une fabrique de classes :

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) Utilise [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), qui contrôle la création via une licence.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) Utilise [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), qui crée des objets dans plusieurs cloisonnements.

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) Utilise [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), qui construit un objet [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) unique.

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="ccomclassfactorycreateinstance"></a><a name="createinstance"></a> CComClassFactory :: CreateInstance

Crée un objet du CLSID spécifié et récupère un pointeur d’interface vers cet objet.

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

## <a name="ccomclassfactorylockserver"></a><a name="lockserver"></a> CComClassFactory :: LockServer,

Incrémente et décrémente le nombre de verrous de module en appelant `_Module::Lock` et `_Module::Unlock` , respectivement.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Paramètres

*Troupeau*<br/>
dans Si la valeur est TRUE, le nombre de verrous est incrémenté ; dans le cas contraire, le nombre de verrous est décrémenté.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

`_Module` fait référence à l’instance globale de [CComModule](../../atl/reference/ccommodule-class.md) ou à une classe dérivée de celle-ci.

L’appel de `LockServer` permet à un client de conserver une fabrique de classes pour que plusieurs objets puissent être créés rapidement.

## <a name="see-also"></a>Voir aussi

[CComObjectRootEx (classe)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
