---
title: Ccomautocriticalsection, classe
ms.date: 11/04/2016
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
ms.openlocfilehash: 1da9aeb0ff285893ed4f81277f379ad8bffcc65b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590903"
---
# <a name="ccomautocriticalsection-class"></a>Ccomautocriticalsection, classe

`CComAutoCriticalSection` Fournit des méthodes pour obtenir et de libérer de la propriété d’un objet de section critique.

## <a name="syntax"></a>Syntaxe

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|Constructeur.|
|[CComAutoCriticalSection :: ~ CComAutoCriticalSection](#dtor)|Destructeur.|

## <a name="remarks"></a>Notes

`CComAutoCriticalSection` est semblable à la classe [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), à l’exception `CComAutoCriticalSection` initialise automatiquement l’objet de section critique dans le constructeur.

En général, vous utilisez `CComAutoCriticalSection` via la `typedef` nom [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Ce nom fait référence à `CComAutoCriticalSection` lorsque [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) est utilisé.

Le `Init` et `Term` méthodes à partir de [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) ne sont pas disponibles lors de l’utilisation de cette classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcore.h

##  <a name="ccomautocriticalsection"></a>  CComAutoCriticalSection::CComAutoCriticalSection

Constructeur.

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>Notes

Appelle la fonction Win32 [InitializeCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsection), ce qui initialise l’objet de section critique.

##  <a name="dtor"></a>  CComAutoCriticalSection :: ~ CComAutoCriticalSection

Destructeur.

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>Notes

Le destructeur appelle [DeleteCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-deletecriticalsection), ce qui libère toutes les ressources système utilisées par l’objet de section critique.

## <a name="see-also"></a>Voir aussi

[CComFakeCriticalSection, classe](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[CComCriticalSection, classe](../../atl/reference/ccomcriticalsection-class.md)
