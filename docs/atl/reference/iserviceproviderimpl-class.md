---
description: 'En savoir plus sur : classe IServiceProviderImpl'
title: IServiceProviderImpl, classe
ms.date: 11/04/2016
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
ms.openlocfilehash: 0cd9fab784fe8bffe420123129aa51c80c187890
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139150"
---
# <a name="iserviceproviderimpl-class"></a>IServiceProviderImpl, classe

Cette classe fournit une implémentation par défaut de l' `IServiceProvider` interface.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IServiceProviderImpl` .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IServiceProviderImpl :: QueryService](#queryservice)|Crée ou accède au service spécifié et retourne un pointeur d’interface vers l’interface spécifiée pour le service.|

## <a name="remarks"></a>Notes

L' `IServiceProvider` interface localise un service spécifié par son GUID et retourne le pointeur d’interface pour l’interface demandée sur le service. La classe `IServiceProviderImpl` fournit une implémentation par défaut de cette interface.

`IServiceProviderImpl` spécifie une méthode : [QueryService](#queryservice), qui crée le service spécifié ou y accède, et retourne un pointeur d’interface vers l’interface spécifiée pour le service.

`IServiceProviderImpl` utilise une carte de service, en commençant par [BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) et en terminant par [END_SERVICE_MAP](service-map-macros.md#end_service_map).

La carte de service contient deux entrées : [SERVICE_ENTRY](service-map-macros.md#service_entry), qui indique un ID de service (SID) spécifié pris en charge par l’objet, et [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain), qui appelle `QueryService` pour effectuer une chaîne à un autre objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IServiceProvider`

`IServiceProviderImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="iserviceproviderimplqueryservice"></a><a name="queryservice"></a> IServiceProviderImpl :: QueryService

Crée ou accède au service spécifié et retourne un pointeur d’interface vers l’interface spécifiée pour le service.

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*guidService*<br/>
dans Pointeur vers un identificateur de service (SID).

*riid*<br/>
dans Identificateur de l’interface à laquelle l’appelant doit accéder.

*ppvObj*<br/>
à Pointeur indirect vers l’interface demandée.

### <a name="return-value"></a>Valeur renvoyée

La valeur HRESULT retournée est l’un des éléments suivants :

|Valeur retournée|Signification|
|------------------|-------------|
|S_OK|Le service a été correctement créé ou récupéré.|
|E_INVALIDARG|Un ou plusieurs arguments ne sont pas valides.|
|E_OUTOFMEMORY|La mémoire est insuffisante pour créer le service.|
|E_UNEXPECTED|Une erreur inconnue s'est produite.|
|E_NOINTERFACE|L’interface demandée ne fait pas partie de ce service, ou le service est inconnu.|

### <a name="remarks"></a>Notes

`QueryService` retourne un pointeur indirect vers l’interface demandée dans le service spécifié. L’appelant est chargé de libérer ce pointeur lorsqu’il n’est plus nécessaire.

Lorsque vous appelez `QueryService` , vous transmettez à la fois un identificateur de service (*guidService*) et un identificateur d’interface (*riid*). Le *guidService* spécifie le service auquel vous souhaitez accéder, et le *riid* identifie une interface qui fait partie du service. En retour, vous recevez un pointeur indirect vers l’interface.

L’objet qui implémente l’interface peut également implémenter des interfaces qui font partie d’autres services. Tenez compte des éléments suivants :

- Certaines de ces interfaces peuvent être facultatives. Toutes les interfaces définies dans la description de service ne sont pas nécessairement présentes sur chaque implémentation du service ou sur chaque objet retourné.

- Contrairement aux appels à `QueryInterface` , passer un identificateur de service différent ne signifie pas nécessairement qu’un objet COM (Component Object Model) différent est retourné.

- L’objet retourné peut avoir des interfaces supplémentaires qui ne font pas partie de la définition du service.

Deux services différents, tels que SID_SMyService et SID_SYourService, peuvent tous deux spécifier l’utilisation de la même interface, même si l’implémentation de l’interface peut n’avoir aucun élément commun entre les deux services. Cela fonctionne, car un appel à `QueryService` (SID_SMyService, IID_IDispatch) peut retourner un objet différent de `QueryService` (SID_SYourService, IID_IDispatch). L’identité de l’objet n’est pas utilisée lorsque vous spécifiez un identificateur de service différent.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
