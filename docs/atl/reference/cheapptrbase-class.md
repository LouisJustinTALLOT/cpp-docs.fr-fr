---
title: Classe CHeapPtrBase
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
helpviewer_keywords:
- CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
ms.openlocfilehash: 62cabf281473cdf21fe260fa23082bc55f339849
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326904"
---
# <a name="cheapptrbase-class"></a>Classe CHeapPtrBase

Cette classe constitue la base de plusieurs classes intelligentes de pointeur de tas.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class Allocator = CCRTAllocator>
class CHeapPtrBase
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type d’objet à stocker sur le tas.

*Allocator*<br/>
La classe d’allocation de mémoire à utiliser. Par défaut, les routines CRT sont utilisées pour allouer et libérer la mémoire.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHeapPtrBase::CHeapPtrBase](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHeapPtrBase::AllocateBytes](#allocatebytes)|Appelez cette méthode pour allouer la mémoire.|
|[CHeapPtrBase::Attach](#attach)|Appelez cette méthode pour prendre possession d’un pointeur existant.|
|[CHeapPtrBase::Detach](#detach)|Appelez cette méthode pour libérer la propriété d’un pointeur.|
|[CHeapPtrBase::Gratuit](#free)|Appelez cette méthode pour supprimer un `CHeapPtrBase`objet pointé par un .|
|[CHeapPtrBase::ReallocateBytes](#reallocatebytes)|Appelez cette méthode pour réaffecter la mémoire.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CHeapPtrBase::opérateur T](#operator_t_star)|L’opérateur de distribution.|
|[CHeapPtrBase::opérateur &](#operator_amp)|Opérateur &.|
|[CHeapPtrBase::opérateur ->](#operator_ptr)|L’opérateur pointeur-à-membre.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CHeapPtrBase::m_pData](#m_pdata)|La variable de membre des données de pointeur.|

## <a name="remarks"></a>Notes

Cette classe constitue la base de plusieurs classes intelligentes de pointeur de tas. Les classes dérivées, par exemple, [CHeapPtr](../../atl/reference/cheapptr-class.md) et [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), ajoutent leurs propres constructeurs et opérateurs. Consultez ces classes pour les exemples de mise en œuvre.

## <a name="requirements"></a>Spécifications

**En-tête:** atlcore.h

## <a name="cheapptrbaseallocatebytes"></a><a name="allocatebytes"></a>CHeapPtrBase::AllocateBytes

Appelez cette méthode pour allouer la mémoire.

```
bool AllocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes (en)*<br/>
Le nombre d’octets de mémoire à allouer.

### <a name="return-value"></a>Valeur de retour

Revient vrai si la mémoire est attribuée avec succès, faux autrement.

### <a name="remarks"></a>Notes

Dans les constructions de déboges, une défaillance d’affirmation se produira si la [base de CHeapPtr : : m_pData](#m_pdata) variable de membre indique actuellement une valeur existante ; c’est-à-dire qu’il n’est pas égal à NULL.

## <a name="cheapptrbaseattach"></a><a name="attach"></a>CHeapPtrBase::Attach

Appelez cette méthode pour prendre possession d’un pointeur existant.

```
void Attach(T* pData) throw();
```

### <a name="parameters"></a>Paramètres

*Pdata*<br/>
L’objet `CHeapPtrBase` s’appropriera ce pointeur.

### <a name="remarks"></a>Notes

Lorsqu’un `CHeapPtrBase` objet prend possession d’un pointeur, il supprime automatiquement le pointeur et les données allouées lorsqu’il n’est pas de portée.

Dans les constructions de déboges, une défaillance d’affirmation se produira si la [base de CHeapPtr : : m_pData](#m_pdata) variable de membre indique actuellement une valeur existante ; c’est-à-dire qu’il n’est pas égal à NULL.

## <a name="cheapptrbasecheapptrbase"></a><a name="dtor"></a>CHeapPtrBase::CHeapPtrBase

Destructeur.

```
~CHeapPtrBase() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="cheapptrbasedetach"></a><a name="detach"></a>CHeapPtrBase::Detach

Appelez cette méthode pour libérer la propriété d’un pointeur.

```
T* Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une copie du pointeur.

### <a name="remarks"></a>Notes

Libère la propriété d’un pointeur, définit la [base CHeapPtr : : m_pData](#m_pdata) variable de membre à NULL, et renvoie une copie du pointeur.

## <a name="cheapptrbasefree"></a><a name="free"></a>CHeapPtrBase::Gratuit

Appelez cette méthode pour supprimer un `CHeapPtrBase`objet pointé par un .

```
void Free() throw();
```

### <a name="remarks"></a>Notes

L’objet pointé `CHeapPtrBase` par le est libéré, et le [CHeapPtrBase::m_pData](#m_pdata) variable membre est réglé à NULL.

## <a name="cheapptrbasem_pdata"></a><a name="m_pdata"></a>CHeapPtrBase::m_pData

La variable de membre des données de pointeur.

```
T* m_pData;
```

### <a name="remarks"></a>Notes

Cette variable de membre contient l’information de pointeur.

## <a name="cheapptrbaseoperator-amp"></a><a name="operator_amp"></a>CHeapPtrBase::opérateur&amp;

Opérateur &.

```
T** operator&() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’adresse de l’objet pointée par l’objet. `CHeapPtrBase`

## <a name="cheapptrbaseoperator--gt"></a><a name="operator_ptr"></a>CHeapPtrBase::opérateur -&gt;

L’opérateur pointeur-à-membre.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la [CHeapPtrBase::m_pData](#m_pdata) variable membre.

### <a name="remarks"></a>Notes

Utilisez cet opérateur pour appeler une méthode `CHeapPtrBase` dans une classe pointée par l’objet. Dans les constructions de débog, `CHeapPtrBase` une défaillance d’affirmation se produira si les points à NULL.

## <a name="cheapptrbaseoperator-t"></a><a name="operator_t_star"></a>CHeapPtrBase::opérateur T

L’opérateur de distribution.

```
operator T*() const throw();
```

### <a name="remarks"></a>Notes

Retourne [CHeapPtrBase::m_pData](#m_pdata).

## <a name="cheapptrbasereallocatebytes"></a><a name="reallocatebytes"></a>CHeapPtrBase::ReallocateBytes

Appelez cette méthode pour réaffecter la mémoire.

```
bool ReallocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes (en)*<br/>
La nouvelle quantité de mémoire à allouer, dans les octets.

### <a name="return-value"></a>Valeur de retour

Revient vrai si la mémoire est attribuée avec succès, faux autrement.

## <a name="see-also"></a>Voir aussi

[Classe CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Classe CComHeapPtr](../../atl/reference/ccomheapptr-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
