---
description: 'En savoir plus sur : classe CComAutoCriticalSection'
title: CComAutoCriticalSection, classe
ms.date: 11/04/2016
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
ms.openlocfilehash: 2441c714b95a3bbefed4a699055d14c6915cffda
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146963"
---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection, classe

`CComAutoCriticalSection` fournit des méthodes pour obtenir et libérer la propriété d’un objet de section critique.

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

`CComAutoCriticalSection` est semblable à la classe [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), sauf qu' `CComAutoCriticalSection` Initialise automatiquement l’objet de section critique dans le constructeur.

En général, vous utilisez `CComAutoCriticalSection` le **`typedef`** nom [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Ce nom fait référence à lors de l' `CComAutoCriticalSection` utilisation de [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) .

Les `Init` `Term` méthodes et de [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) ne sont pas disponibles lors de l’utilisation de cette classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcore. h

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="ccomautocriticalsection"></a> CComAutoCriticalSection::CComAutoCriticalSection

Constructeur.

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>Notes

Appelle la fonction Win32 [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), qui initialise l’objet de section critique.

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="dtor"></a> CComAutoCriticalSection :: ~ CComAutoCriticalSection

Destructeur.

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>Notes

Le destructeur appelle [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), qui libère toutes les ressources système utilisées par l’objet de section critique.

## <a name="see-also"></a>Voir aussi

[CComFakeCriticalSection, classe](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[CComCriticalSection, classe](../../atl/reference/ccomcriticalsection-class.md)
