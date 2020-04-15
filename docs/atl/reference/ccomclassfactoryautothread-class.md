---
title: Classe CComClassFactoryAutoThread
ms.date: 11/04/2016
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
ms.openlocfilehash: e997d92adfa9df46c82dacbd297db495b037c6e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320904"
---
# <a name="ccomclassfactoryautothread-class"></a>Classe CComClassFactoryAutoThread

Cette classe implémente l’interface [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) et permet de créer des objets dans plusieurs appartements.

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
|[CComClassFactoryAutoThread::CréerInstance](#createinstance)|Crée un objet du CLSID spécifié.|
|[CComClassFactoryAutoThread::LockServer](#lockserver)|Verrouille l’usine de classe dans la mémoire.|

## <a name="remarks"></a>Notes

`CComClassFactoryAutoThread`est similaire à [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), mais permet de créer des objets dans plusieurs appartements. Pour profiter de ce support, dérivez votre module EXE de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Les objets ATL acquièrent normalement une usine de classe en dérivé de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), qui déclare [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme l’usine de classe par défaut. Pour `CComClassFactoryAutoThread`l’utiliser, spécifiez la [macro DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) dans la définition de classe de votre objet. Par exemple :

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomclassfactoryautothreadcreateinstance"></a><a name="createinstance"></a>CComClassFactoryAutoThread::CréerInstance

Crée un objet du CLSID spécifié et récupère un pointeur d’interface sur cet objet.

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
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

### <a name="remarks"></a>Notes

Si votre module dérive de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), `CreateInstance` sélectionne d’abord un thread pour créer l’objet dans l’appartement associé.

## <a name="ccomclassfactoryautothreadlockserver"></a><a name="lockserver"></a>CComClassFactoryAutoThread::LockServer

Incréments et décroissements le `_Module::Lock` module `_Module::Unlock`verrou compte en appelant et , respectivement.

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>Paramètres

*Troupeau*<br/>
[dans] Si VRAI, le nombre de serrures est incrémenté; autrement, le nombre de serrures est décrète.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Lors `CComClassFactoryAutoThread`de `_Module` l’utilisation , se réfère généralement à l’exemple global de [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

L’appel `LockServer` permet à un client de s’accrocher à une usine de classe afin que plusieurs objets puissent être rapidement créés.

## <a name="see-also"></a>Voir aussi

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[Classe CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)<br/>
[Classe CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[Classe CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
