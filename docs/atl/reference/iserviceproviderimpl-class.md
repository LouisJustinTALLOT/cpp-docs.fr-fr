---
title: IServiceProviderImpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
dev_langs:
- C++
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d14d00e57cbbb04c77f0b84c584ebb1c4f4260e5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703200"
---
# <a name="iserviceproviderimpl-class"></a>IServiceProviderImpl, classe

Cette classe fournit une implémentation par défaut de la `IServiceProvider` interface.

## <a name="syntax"></a>Syntaxe

```
template <class T>  
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```

#### <a name="parameters"></a>Paramètres

*T*  
Votre classe, dérivée de `IServiceProviderImpl`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Méthode IServiceProviderImpl::QueryService](#queryservice)|Crée ou accède au service spécifié et retourne un pointeur d’interface vers l’interface spécifiée pour le service.|

## <a name="remarks"></a>Notes

Le `IServiceProvider` interface recherche un service spécifié par son GUID et retourne le pointeur d’interface pour l’interface demandée sur le service. Classe `IServiceProviderImpl` fournit une implémentation par défaut de cette interface.

`IServiceProviderImpl` Spécifie une méthode : [QueryService](#queryservice), qui crée ou accède au service spécifié et retourne un pointeur d’interface vers l’interface spécifiée pour le service.

`IServiceProviderImpl` utilise une carte de service, en commençant par [BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) et se terminant par [END_SERVICE_MAP](service-map-macros.md#end_service_map).

La carte de service contient deux entrées : [SERVICE_ENTRY](service-map-macros.md#service_entry), ce qui indique un id de service spécifié (SID) pris en charge par l’objet, et [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain), qui appelle `QueryService` à chaîne vers un autre objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IServiceProvider`

`IServiceProviderImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="queryservice"></a>  Méthode IServiceProviderImpl::QueryService

Crée ou accède au service spécifié et retourne un pointeur d’interface vers l’interface spécifiée pour le service.

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*guidService*<br/>
[in] Pointeur vers un identificateur de service (SID).

*riid*<br/>
[in] Identificateur de l’interface à laquelle l’appelant doit accéder.

*ppvObj*<br/>
[out] Pointeur indirect vers l’interface demandée.

### <a name="return-value"></a>Valeur de retour

La valeur HRESULT retournée est une des opérations suivantes :

|Valeur de retour|Signification|
|------------------|-------------|
|S_OK|Le service a été correctement créé ou récupéré.|
|E_INVALIDARG|Un ou plusieurs arguments ne sont pas valides.|
|E_OUTOFMEMORY|Mémoire insuffisante créer le service.|
|E_UNEXPECTED|Une erreur inconnue s'est produite.|
|E_NOINTERFACE|L’interface demandée ne fait pas partie de ce service, ou le service est inconnu.|

### <a name="remarks"></a>Notes

`QueryService` Retourne un pointeur indirect vers l’interface demandée dans le service spécifié. L’appelant est chargé de le libérer ce pointeur lorsqu’il n’est plus nécessaire.

Lorsque vous appelez `QueryService`, vous passez à la fois un identificateur de service (*guidService*) et un identificateur d’interface (*riid*). Le *guidService* Spécifie le service auquel vous souhaitez accéder, et le *riid* identifie une interface qui fait partie du service. En retour, vous recevez un pointeur indirect vers l’interface.

L’objet qui implémente l’interface peut également implémenter des interfaces qui appartiennent à d’autres services. Considérez ce qui suit :

- Il se peut que certaines de ces interfaces peuvent être facultatifs. Pas toutes les interfaces définies dans la description de service sont nécessairement présents sur chaque implémentation du service ou sur chaque objet retourné.

- Contrairement aux appels à `QueryInterface`, en passant un identificateur de service différent ne signifie pas nécessairement qu’un autre composant COM (Object Model) est retourné.

- L’objet retourné peut avoir des interfaces supplémentaires qui ne font pas partie de la définition du service.

Deux services différents, tels que SID_SMyService et SID_SYourService, peuvent tous deux spécifier l’utilisation de la même interface, même si l’implémentation de l’interface n’aient rien en commun entre les deux services. Cela fonctionne, car un appel à `QueryService` (SID_SMyService, IID_IDispatch) peut retourner un objet autre que `QueryService` (SID_SYourService, IID_IDispatch). Identité de l’objet n’est pas supposé que lorsque vous spécifiez un identificateur de service différent.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
