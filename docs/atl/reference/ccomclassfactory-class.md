---
title: CComClassFactory, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f01b333edd9dd671ce4d03176a75979e57a06bd7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062169"
---
# <a name="ccomclassfactory-class"></a>CComClassFactory, classe

Cette classe implémente le [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interface.

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
|[CComClassFactory::CreateInstance](#createinstance)|Crée un objet du CLSID spécifié.|
|[CComClassFactory::LockServer](#lockserver)|Verrouille la fabrique de classe en mémoire.|

## <a name="remarks"></a>Notes

`CComClassFactory` implémente le [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interface, qui contient des méthodes pour la création d’un objet d’un CLSID particulier, ainsi que le verrouillage de la fabrique de classe dans la mémoire pour permettre aux nouveaux objets à créer plus rapidement. `IClassFactory` doit être implémentée pour chaque classe que vous inscrivez dans le Registre système et à laquelle vous affectez un CLSID.

Objets ATL acquièrent normalement une fabrique de classe en dérivant de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe inclut la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), qui déclare `CComClassFactory` en tant que la fabrique de classe par défaut. Pour remplacer cette valeur par défaut, spécifiez l’une de la `DECLARE_CLASSFACTORY` *XXX* macros dans votre définition de classe. Par exemple, le [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) macro utilise la classe spécifiée de la fabrique de classe :

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

La définition de classe ci-dessus spécifie que `CMyClassFactory` sera utilisé comme fabrique de classe par défaut de l’objet. `CMyClassFactory` doit dériver de `CComClassFactory` et remplacer `CreateInstance`.

ATL fournit trois autres macros qui déclarent une fabrique de classe :

- [Macro DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) utilise [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), qui contrôle la création via une licence.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) utilise [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), ce qui crée des objets dans des cloisonnements plusieurs.

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) utilise [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), qui construit un seul [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="createinstance"></a>  CComClassFactory::CreateInstance

Crée un objet du CLSID spécifié et récupère un pointeur d’interface vers cet objet.

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

##  <a name="lockserver"></a>  CComClassFactory::LockServer

Incrémente et décrémente le module nombre de verrous en appelant `_Module::Lock` et `_Module::Unlock`, respectivement.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Paramètres

*Troupeau*<br/>
[in] Si la valeur est TRUE, le nombre de verrous est incrémenté ; Sinon, le nombre de verrous est décrémenté.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

`_Module` fait référence à l’instance globale de [CComModule](../../atl/reference/ccommodule-class.md) ou une classe dérivée à partir de celui-ci.

Appel `LockServer` permet à un client à maintenir une fabrique de classe afin que plusieurs objets peuvent être créés rapidement.

## <a name="see-also"></a>Voir aussi

[CComObjectRootEx, classe](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
