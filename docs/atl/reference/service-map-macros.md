---
title: Macros de carte de service
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: eb2fe41c79135a7ac2ced9bc3242b070170716b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325939"
---
# <a name="service-map-macros"></a>Macros de carte de service

Ces macros définissent les cartes de service et les entrées.

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|Marque le début d’une carte de service ATL.|
|[END_SERVICE_MAP](#end_service_map)|Marque la fin d’une carte de service ATL.|
|[SERVICE_ENTRY](#service_entry)|Indique que l’objet prend en charge une pièce d’identité de service spécifique.|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Instructs [IServiceProviderImpl::QueryService](#queryservice) to chain to the specified object.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="begin_service_map"></a><a name="begin_service_map"></a>BEGIN_SERVICE_MAP

Marque le début de la carte de service.

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
[dans] Spécifie la classe contenant la carte de service.

### <a name="remarks"></a>Notes

Utilisez la carte de service pour implémenter les fonctionnalités du fournisseur de services sur votre objet COM. Tout d’abord, vous devez tirer votre classe de [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md). Il existe deux types d’entrées :

- [SERVICE_ENTRY](#service_entry)   Indique la prise en charge de l’ID de service spécifié (SID).

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)   Instructs [IServiceProviderImpl::QueryService](#queryservice) to chain to another, specified object.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

## <a name="end_service_map"></a><a name="end_service_map"></a>END_SERVICE_MAP

Marque la fin de la carte de service.

```
END_SERVICE_MAP()
```

### <a name="example"></a>Exemple

Voir l’exemple pour [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="service_entry"></a><a name="service_entry"></a>SERVICE_ENTRY

Indique que l’objet prend en charge l’id de service spécifié par *SID*.

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>Paramètres

*Sid*<br/>
L’ID de service.

### <a name="example"></a>Exemple

Voir l’exemple pour [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="service_entry_chain"></a><a name="service_entry_chain"></a>SERVICE_ENTRY_CHAIN

Instructs [IServiceProviderImpl::QueryService](#queryservice) to chain to the object specified by *punk*.

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
Un pointeur à l’interface **IUnknown** à laquelle enchaîner.

### <a name="example"></a>Exemple

Voir l’exemple pour [BEGIN_SERVICE_MAP](#begin_service_map).

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

[Macros](../../atl/reference/atl-macros.md)
