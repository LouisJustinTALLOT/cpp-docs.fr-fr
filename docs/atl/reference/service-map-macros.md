---
title: Macros Service Map
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: 1fa163098d89dd949c17ee7cd5e4ddc46cd2a091
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835205"
---
# <a name="service-map-macros"></a>Macros Service Map

Ces macros définissent les cartes de service et les entrées.

|Nom|Description|
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|Marque le début d’un mappage de service ATL.|
|[END_SERVICE_MAP](#end_service_map)|Marque la fin d’un mappage de service ATL.|
|[SERVICE_ENTRY](#service_entry)|Indique que l’objet prend en charge un ID de service spécifique.|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Ordonne à [IServiceProviderImpl :: QueryService](#queryservice) de se lier à l’objet spécifié.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom. h

## <a name="begin_service_map"></a><a name="begin_service_map"></a> BEGIN_SERVICE_MAP

Marque le début de la carte de service.

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
dans Spécifie la classe qui contient la carte de service.

### <a name="remarks"></a>Notes

Utilisez la carte de service pour implémenter les fonctionnalités du fournisseur de services sur votre objet COM. Tout d’abord, vous devez dériver votre classe de [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md). Il existe deux types d’entrées :

- [SERVICE_ENTRY](#service_entry)   Indique la prise en charge de l’ID de service (SID) spécifié.

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)   Ordonne à [IServiceProviderImpl :: QueryService](#queryservice) d’effectuer une chaîne sur un autre objet spécifié.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

## <a name="end_service_map"></a><a name="end_service_map"></a> END_SERVICE_MAP

Marque la fin de la carte de service.

```
END_SERVICE_MAP()
```

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="service_entry"></a><a name="service_entry"></a> SERVICE_ENTRY

Indique que l’objet prend en charge l’ID de service spécifié par *sid*.

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>Paramètres

*SID*<br/>
ID du service.

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="service_entry_chain"></a><a name="service_entry_chain"></a> SERVICE_ENTRY_CHAIN

Ordonne à [IServiceProviderImpl :: QueryService](#queryservice) de chaîner avec l’objet spécifié par *punk*.

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
Pointeur vers l’interface **IUnknown** dans laquelle effectuer la chaîne.

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_SERVICE_MAP](#begin_service_map).

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

|Valeur de retour|Signification|
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

[Macros](../../atl/reference/atl-macros.md)
