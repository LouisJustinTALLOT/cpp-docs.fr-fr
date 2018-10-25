---
title: Macros de mappage de service | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
dev_langs:
- C++
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 30715cffb42c1dbf92512fa7314bf70f46f300a3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079933"
---
# <a name="service-map-macros"></a>Macros de mappage de service

Ces macros définissent des cartes de services et les entrées.

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|Marque le début d’une carte de service ATL.|
|[END_SERVICE_MAP](#end_service_map)|Marque la fin d’une carte de service ATL.|
|[SERVICE_ENTRY](#service_entry)|Indique que l’objet prend en charge un ID de service spécifique.|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Indique à [méthode IServiceProviderImpl::QueryService](#queryservice) à chaîne à l’objet spécifié.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="begin_service_map"></a>  BEGIN_SERVICE_MAP

Marque le début de la carte de service.

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
[in] Spécifie la classe contenant la carte de service.

### <a name="remarks"></a>Notes

Utilisez la carte de service pour implémenter des fonctionnalités de fournisseur de service sur votre objet COM. Tout d’abord, vous devez dériver votre classe de [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md). Il existe deux types d’entrées :

- [SERVICE_ENTRY](#service_entry) indique la prise en charge pour l’ID (SID) de service spécifié.

- [SERVICE_ENTRY_CHAIN](#service_entry_chain) demande à [méthode IServiceProviderImpl::QueryService](#queryservice) attacher à un autre objet spécifié.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

##  <a name="end_service_map"></a>  END_SERVICE_MAP

Marque la fin de la carte de service.

```
END_SERVICE_MAP()
```

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="service_entry"></a>  SERVICE_ENTRY

Indique que l’objet prend en charge l’id de service spécifié par *SID*.

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>Paramètres

*SID*<br/>
L’ID de service.

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="service_entry_chain"></a>  SERVICE_ENTRY_CHAIN

Indique à [méthode IServiceProviderImpl::QueryService](#queryservice) attacher à l’objet spécifié par *punk*.

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>Paramètres

*pUnk*<br/>
Un pointeur vers le **IUnknown** interface à laquelle à chaîne.

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_SERVICE_MAP](#begin_service_map).

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

[Macros](../../atl/reference/atl-macros.md)
