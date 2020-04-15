---
title: Classe IServiceProviderImpl
ms.date: 11/04/2016
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
ms.openlocfilehash: ef0ee4f77441cb8d19ea2d6dcada1fed9faf2782
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329428"
---
# <a name="iserviceproviderimpl-class"></a>Classe IServiceProviderImpl

Cette classe fournit une `IServiceProvider` implémentation par défaut de l’interface.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IServiceProviderImpl`dérivée de .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IServiceProviderImpl::QueryService](#queryservice)|Crée ou accède au service spécifié et renvoie un pointeur d’interface à l’interface spécifiée pour le service.|

## <a name="remarks"></a>Notes

L’interface `IServiceProvider` localise un service spécifié par son GUID et renvoie le pointeur d’interface pour l’interface demandée sur le service. La `IServiceProviderImpl` classe fournit une implémentation par défaut de cette interface.

`IServiceProviderImpl`spécifie une méthode : [QueryService](#queryservice), qui crée ou accède au service spécifié et renvoie un pointeur d’interface à l’interface spécifiée pour le service.

`IServiceProviderImpl`utilise une carte de service, en commençant par [BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) et se terminant par [END_SERVICE_MAP](service-map-macros.md#end_service_map).

La carte de service contient deux entrées: [SERVICE_ENTRY](service-map-macros.md#service_entry), qui indique un id de service spécifié `QueryService` (SID) pris en charge par l’objet, et [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain), qui appelle à la chaîne à un autre objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IServiceProvider`

`IServiceProviderImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="iserviceproviderimplqueryservice"></a><a name="queryservice"></a>IServiceProviderImpl::QueryService

Crée ou accède au service spécifié et renvoie un pointeur d’interface à l’interface spécifiée pour le service.

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*guidService*<br/>
[dans] Pointeur vers un identifiant de service (SID).

*riid*<br/>
[dans] Identifiant l’interface à laquelle l’appelant doit accéder.

*ppvObj*<br/>
[out] Pointeur indirect à l’interface demandée.

### <a name="return-value"></a>Valeur de retour

La valeur HRESULT retournée est l’une des suivantes :

|Valeur retournée|Signification|
|------------------|-------------|
|S_OK|Le service a été créé ou récupéré avec succès.|
|E_INVALIDARG|Un ou plusieurs arguments ne sont pas valides.|
|E_OUTOFMEMORY|La mémoire est insuffisante pour créer le service.|
|E_UNEXPECTED|Une erreur inconnue s'est produite.|
|E_NOINTERFACE|L’interface demandée ne fait pas partie de ce service, ou le service est inconnu.|

### <a name="remarks"></a>Notes

`QueryService`renvoie un pointeur indirect à l’interface demandée dans le service spécifié. L’appelant est responsable de la publication de ce pointeur lorsqu’il n’est plus nécessaire.

Lorsque vous `QueryService`appelez, vous passez à la fois un identifiant de service (*guidService*) et un identifiant d’interface *(riid*). Le *guidService* spécifie le service auquel vous souhaitez accéder, et le *riid* identifie une interface qui fait partie du service. En retour, vous recevez un pointeur indirect sur l’interface.

L’objet qui implémente l’interface peut également implémenter des interfaces qui font partie d’autres services. Tenez compte des éléments suivants :

- Certaines de ces interfaces peuvent être facultatives. Toutes les interfaces définies dans la description de service ne sont pas nécessairement présentes sur chaque implémentation du service ou sur chaque objet retourné.

- Contrairement aux `QueryInterface`appels vers , passer un identifiant de service différent ne signifie pas nécessairement qu’un autre modèle d’objet composant (COM) objet est retourné.

- L’objet retourné peut avoir des interfaces supplémentaires qui ne font pas partie de la définition du service.

Deux services différents, tels que SID_SMyService et SID_SYourService, peuvent tous deux spécifier l’utilisation de la même interface, même si la mise en œuvre de l’interface pourrait n’avoir rien en commun entre les deux services. Cela fonctionne, car `QueryService` un appel à (SID_SMyService, IID_IDispatch) peut retourner `QueryService` un objet différent de (SID_SYourService, IID_IDispatch). L’identité de l’objet n’est pas assumée lorsque vous spécifiez un identifiant de service différent.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
