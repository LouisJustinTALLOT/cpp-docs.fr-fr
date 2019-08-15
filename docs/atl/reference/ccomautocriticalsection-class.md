---
title: CComAutoCriticalSection, classe
ms.date: 11/04/2016
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
ms.openlocfilehash: 116c550f45bf622e7620b3a6f552339b4bcc24a7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497929"
---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection, classe

`CComAutoCriticalSection`fournit des méthodes pour obtenir et libérer la propriété d’un objet de section critique.

## <a name="syntax"></a>Syntaxe

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|Constructeur.|
|[CComAutoCriticalSection::~CComAutoCriticalSection](#dtor)|Destructeur.|

## <a name="remarks"></a>Notes

`CComAutoCriticalSection`est semblable à la classe [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), `CComAutoCriticalSection` sauf qu’Initialise automatiquement l’objet de section critique dans le constructeur.

En général, vous `CComAutoCriticalSection` utilisez le `typedef` nom [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Ce nom fait `CComAutoCriticalSection` référence à lors de l’utilisation de [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) .

Les `Init` méthodes `Term` et de [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) ne sont pas disponibles lors de l’utilisation de cette classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>Configuration requise

**En-tête:** atlcore. h

##  <a name="ccomautocriticalsection"></a>  CComAutoCriticalSection::CComAutoCriticalSection

Constructeur.

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>Notes

Appelle la fonction Win32 [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), qui initialise l’objet de section critique.

##  <a name="dtor"></a>  CComAutoCriticalSection::~CComAutoCriticalSection

Destructeur.

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>Notes

Le destructeur appelle [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), qui libère toutes les ressources système utilisées par l’objet de section critique.

## <a name="see-also"></a>Voir aussi

[CComFakeCriticalSection, classe](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[CComCriticalSection, classe](../../atl/reference/ccomcriticalsection-class.md)
