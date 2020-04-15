---
title: Classe CComClassFactory
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
ms.openlocfilehash: 041575339906b83488697f1db5a7f8b08b53070e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321024"
---
# <a name="ccomclassfactory-class"></a>Classe CComClassFactory

Cette classe implémente l’interface [IClassFactory.](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)

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
|[CComClassFactory::CréerInstance](#createinstance)|Crée un objet du CLSID spécifié.|
|[CComClassFactory::LockServer](#lockserver)|Verrouille l’usine de classe dans la mémoire.|

## <a name="remarks"></a>Notes

`CComClassFactory`implémente l’interface [IClassFactory,](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) qui contient des méthodes pour créer un objet d’un CLSID particulier, ainsi que le verrouillage de l’usine de classe dans la mémoire pour permettre de nouveaux objets à créer plus rapidement. `IClassFactory`doit être mis en œuvre pour chaque classe que vous vous inscrivez dans le registre du système et à laquelle vous attribuez un CLSID.

Les objets ATL acquièrent normalement une usine de classe en dérivé de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) `CComClassFactory` , qui déclare que l’usine de classe par défaut. Pour remplacer cette valeur par `DECLARE_CLASSFACTORY`défaut, spécifiez l’une des macros *XXX* dans votre définition de classe. Par exemple, la [macro DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) utilise la classe spécifiée pour l’usine de classe :

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

La définition de classe `CMyClassFactory` ci-dessus spécifie qui sera utilisée comme usine de classe par défaut de l’objet. `CMyClassFactory`doit dériver `CComClassFactory` et `CreateInstance`passer outre .

ATL fournit trois autres macros qui déclarent une usine de classe:

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) Utilise [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), qui contrôle la création par le biais d’une licence.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) Utilise [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), qui crée des objets dans plusieurs appartements.

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) Utilise [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), qui construit un seul objet [CComObjectGlobal.](../../atl/reference/ccomobjectglobal-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomclassfactorycreateinstance"></a><a name="createinstance"></a>CComClassFactory::CréerInstance

Crée un objet du CLSID spécifié et récupère un pointeur d’interface sur cet objet.

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

## <a name="ccomclassfactorylockserver"></a><a name="lockserver"></a>CComClassFactory::LockServer

Incréments et décroissements le `_Module::Lock` module `_Module::Unlock`verrou compte en appelant et , respectivement.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Paramètres

*Troupeau*<br/>
[dans] Si VRAI, le nombre de serrures est incrémenté; autrement, le nombre de serrures est décrète.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

`_Module`se réfère à l’exemple global de [CComModule](../../atl/reference/ccommodule-class.md) ou d’une classe qui en découle.

L’appel `LockServer` permet à un client de s’accrocher à une usine de classe afin que plusieurs objets puissent être créés rapidement.

## <a name="see-also"></a>Voir aussi

[Classe CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
