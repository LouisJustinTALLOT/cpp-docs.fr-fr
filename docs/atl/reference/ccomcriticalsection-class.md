---
description: 'En savoir plus sur : classe CComCriticalSection'
title: CComCriticalSection, classe
ms.date: 11/04/2016
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
ms.openlocfilehash: 7a6a3efef68a14cbda513ee60ed3980293514ad6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146729"
---
# <a name="ccomcriticalsection-class"></a>CComCriticalSection, classe

Cette classe fournit des méthodes pour obtenir et libérer la propriété d’un objet de section critique.

## <a name="syntax"></a>Syntaxe

```
class CComCriticalSection
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComCriticalSection :: init](#init)|Crée et initialise un objet de section critique.|
|[CComCriticalSection :: Lock](#lock)|Obtient la propriété de l’objet de section critique.|
|[CComCriticalSection :: term](#term)|Libère les ressources système utilisées par l’objet de section critique.|
|[CComCriticalSection :: Unlock](#unlock)|Libère la propriété de l’objet de section critique.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComCriticalSection :: m_sec](#m_sec)|Objet CRITICAL_SECTION.|

## <a name="remarks"></a>Notes

`CComCriticalSection` est semblable à la classe [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), à ceci près que vous devez initialiser explicitement et libérer la section critique.

En général, vous utilisez `CComCriticalSection` le **`typedef`** nom [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Ce nom fait référence à lors de l' `CComCriticalSection` utilisation de [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) .

Consultez la [classe CComCritSecLock](../../atl/reference/ccomcritseclock-class.md) pour un moyen plus sûr d’utiliser cette classe que d’appeler `Lock` et `Unlock` directement.

## <a name="requirements"></a>Spécifications

**En-tête :** atlcore. h

## <a name="ccomcriticalsectionccomcriticalsection"></a><a name="ccomcriticalsection"></a> CComCriticalSection::CComCriticalSection

Constructeur.

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>Notes

Affecte la valeur NULL au membre de données [m_sec](#m_sec) .

## <a name="ccomcriticalsectioninit"></a><a name="init"></a> CComCriticalSection :: init

Appelle la fonction Win32 [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), qui initialise l’objet de section critique contenu dans le membre de données [m_sec](#m_sec) .

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, E_OUTOFMEMORY ou E_FAIL en cas d’échec.

## <a name="ccomcriticalsectionlock"></a><a name="lock"></a> CComCriticalSection :: Lock

Appelle la fonction Win32 [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), qui attend que le thread puisse prendre possession de l’objet de section critique contenu dans le membre de données [m_sec](#m_sec) .

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite, E_OUTOFMEMORY ou E_FAIL en cas d’échec.

### <a name="remarks"></a>Notes

L’objet de section critique doit d’abord être initialisé avec un appel à la méthode [init](#init) . Lorsque l’exécution du code protégé est terminée, le thread doit appeler [Unlock](#unlock) pour libérer la propriété de la section critique.

## <a name="ccomcriticalsectionm_sec"></a><a name="m_sec"></a> CComCriticalSection :: m_sec

Contient un objet de section critique qui est utilisé par toutes les `CComCriticalSection` méthodes.

```
CRITICAL_SECTION m_sec;
```

## <a name="ccomcriticalsectionterm"></a><a name="term"></a> CComCriticalSection :: term

Appelle la fonction Win32 [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), qui libère toutes les ressources utilisées par l’objet de section critique contenu dans le membre de données [m_sec](#m_sec) .

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

### <a name="remarks"></a>Notes

Une fois que `Term` a été appelé, la section critique ne peut plus être utilisée pour la synchronisation.

## <a name="ccomcriticalsectionunlock"></a><a name="unlock"></a> CComCriticalSection :: Unlock

Appelle la fonction Win32 [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), qui libère la propriété de l’objet de section critique contenu dans le membre de données [m_sec](#m_sec) .

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour obtenir d’abord la propriété, le thread doit appeler la méthode [Lock](#lock) . Chaque appel à `Lock` requiert un appel correspondant à `Unlock` pour libérer la propriété de la section critique.

## <a name="see-also"></a>Voir aussi

[CComFakeCriticalSection, classe](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[CComCritSecLock, classe](../../atl/reference/ccomcritseclock-class.md)
