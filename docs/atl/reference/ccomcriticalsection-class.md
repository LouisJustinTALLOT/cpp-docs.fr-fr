---
title: Classe CComCriticalSection
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
ms.openlocfilehash: f3991d217fbc201bd428ed2522a5c4c25e074928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327967"
---
# <a name="ccomcriticalsection-class"></a>Classe CComCriticalSection

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
|[CComCriticalSection::Init](#init)|Crée et initialise un objet de section critique.|
|[CComCriticalSection::Lock](#lock)|Obtient la propriété de l’objet de section critique.|
|[CComCriticalSection::Terme](#term)|Libère les ressources système utilisées par l’objet de section critique.|
|[CComCriticalSection::Unlock](#unlock)|Libère la propriété de l’objet de section critique.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComCriticalSection::m_sec](#m_sec)|Un objet CRITICAL_SECTION.|

## <a name="remarks"></a>Notes

`CComCriticalSection`est similaire à la classe [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), sauf que vous devez explicitement initialiser et libérer la section critique.

Typiquement, vous `CComCriticalSection` utilisez à travers le nom **de typedef** [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Ce nom `CComCriticalSection` fait référence lorsque [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) est utilisé.

Consultez [CComCritSecLock Class](../../atl/reference/ccomcritseclock-class.md) pour un moyen plus `Lock` `Unlock` sûr d’utiliser cette classe que d’appeler et directement.

## <a name="requirements"></a>Spécifications

**En-tête:** atlcore.h

## <a name="ccomcriticalsectionccomcriticalsection"></a><a name="ccomcriticalsection"></a>CComCriticalSection::CComCriticalSection

Constructeur.

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>Notes

Définit le [membre m_sec](#m_sec) de données à NULL.

## <a name="ccomcriticalsectioninit"></a><a name="init"></a>CComCriticalSection::Init

Appelle la fonction Win32 [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), qui initialise l’objet de section critique contenu dans le membre [m_sec](#m_sec) de données.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, E_OUTOFMEMORY ou E_FAIL sur l’échec.

## <a name="ccomcriticalsectionlock"></a><a name="lock"></a>CComCriticalSection::Lock

Appelle la fonction Win32 [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), qui attend que le thread puisse s’approprier l’objet de section critique contenu dans le membre [m_sec](#m_sec) de données.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, E_OUTOFMEMORY ou E_FAIL sur l’échec.

### <a name="remarks"></a>Notes

L’objet de section critique doit d’abord être paradé avec un appel à la méthode [Init.](#init) Lorsque le code protégé a terminé l’exécution, le thread doit appeler [Unlock](#unlock) pour libérer la propriété de la section critique.

## <a name="ccomcriticalsectionm_sec"></a><a name="m_sec"></a>CComCriticalSection::m_sec

Contient un objet de section `CComCriticalSection` critique qui est utilisé par toutes les méthodes.

```
CRITICAL_SECTION m_sec;
```

## <a name="ccomcriticalsectionterm"></a><a name="term"></a>CComCriticalSection::Terme

Appelle la fonction Win32 [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), qui libère toutes les ressources utilisées par l’objet de section critique contenu dans le membre des données [m_sec.](#m_sec)

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Une `Term` fois appelée, la section critique ne peut plus être utilisée pour la synchronisation.

## <a name="ccomcriticalsectionunlock"></a><a name="unlock"></a>CComCriticalSection::Unlock

Appelle la fonction Win32 [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), qui libère la propriété de l’objet de section critique contenu dans le membre [m_sec](#m_sec) de données.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

### <a name="remarks"></a>Notes

Pour obtenir d’abord la propriété, le thread doit appeler la méthode [De verrouillage.](#lock) Chaque appel `Lock` nécessite un `Unlock` appel correspondant pour libérer la propriété de la section critique.

## <a name="see-also"></a>Voir aussi

[Classe CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classe CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)
