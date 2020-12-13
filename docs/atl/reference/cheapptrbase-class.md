---
description: 'En savoir plus sur : classe CHeapPtrBase'
title: CHeapPtrBase, classe
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
ms.openlocfilehash: 6186f68066f4c159c16c458f9f00725478aa98a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141633"
---
# <a name="cheapptrbase-class"></a>CHeapPtrBase, classe

Cette classe constitue la base de plusieurs classes de pointeur Smart Heap.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class Allocator = CCRTAllocator>
class CHeapPtrBase
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type d’objet à stocker sur le tas.

*Allocateur*<br/>
Classe d’allocation de mémoire à utiliser. Par défaut, les routines CRT sont utilisées pour allouer et libérer de la mémoire.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHeapPtrBase :: ~ CHeapPtrBase](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHeapPtrBase::AllocateBytes](#allocatebytes)|Appelez cette méthode pour allouer de la mémoire.|
|[CHeapPtrBase :: Attach](#attach)|Appelez cette méthode pour prendre possession d’un pointeur existant.|
|[CHeapPtrBase ::D Etach](#detach)|Appelez cette méthode pour libérer la propriété d’un pointeur.|
|[CHeapPtrBase :: Free](#free)|Appelez cette méthode pour supprimer un objet désigné par un `CHeapPtrBase` .|
|[CHeapPtrBase::ReallocateBytes](#reallocatebytes)|Appelez cette méthode pour réallouer la mémoire.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CHeapPtrBase :: Operator T *](#operator_t_star)|Opérateur de cast.|
|[CHeapPtrBase :: Operator &](#operator_amp)|Opérateur &.|
|[CHeapPtrBase :: Operator->](#operator_ptr)|Opérateur pointeur vers membre.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CHeapPtrBase :: m_pData](#m_pdata)|Variable de membre de données de pointeur.|

## <a name="remarks"></a>Notes

Cette classe constitue la base de plusieurs classes de pointeur Smart Heap. Les classes dérivées, par exemple, [CHeapPtr](../../atl/reference/cheapptr-class.md) et [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), ajoutent leurs propres constructeurs et opérateurs. Consultez ces classes pour obtenir des exemples d’implémentation.

## <a name="requirements"></a>Spécifications

**En-tête :** atlcore. h

## <a name="cheapptrbaseallocatebytes"></a><a name="allocatebytes"></a> CHeapPtrBase::AllocateBytes

Appelez cette méthode pour allouer de la mémoire.

```
bool AllocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes*<br/>
Nombre d’octets de mémoire à allouer.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si la mémoire est allouée avec succès ; sinon, false.

### <a name="remarks"></a>Notes

Dans les versions Debug, un échec d’assertion se produit si la variable membre [CHeapPtrBase :: m_pData](#m_pdata) pointe actuellement vers une valeur existante ; autrement dit, il n’est pas égal à la valeur NULL.

## <a name="cheapptrbaseattach"></a><a name="attach"></a> CHeapPtrBase :: Attach

Appelez cette méthode pour prendre possession d’un pointeur existant.

```cpp
void Attach(T* pData) throw();
```

### <a name="parameters"></a>Paramètres

*pData*<br/>
L' `CHeapPtrBase` objet prend la propriété de ce pointeur.

### <a name="remarks"></a>Notes

Lorsqu’un `CHeapPtrBase` objet prend possession d’un pointeur, il supprime automatiquement le pointeur et toutes les données allouées lorsqu’il est hors de portée.

Dans les versions Debug, un échec d’assertion se produit si la variable membre [CHeapPtrBase :: m_pData](#m_pdata) pointe actuellement vers une valeur existante ; autrement dit, il n’est pas égal à la valeur NULL.

## <a name="cheapptrbasecheapptrbase"></a><a name="dtor"></a> CHeapPtrBase :: ~ CHeapPtrBase

Destructeur.

```
~CHeapPtrBase() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="cheapptrbasedetach"></a><a name="detach"></a> CHeapPtrBase ::D Etach

Appelez cette méthode pour libérer la propriété d’un pointeur.

```
T* Detach() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne une copie du pointeur.

### <a name="remarks"></a>Notes

Libère la propriété d’un pointeur, définit la variable de membre [CHeapPtrBase :: m_pData](#m_pdata) sur la valeur null et retourne une copie du pointeur.

## <a name="cheapptrbasefree"></a><a name="free"></a> CHeapPtrBase :: Free

Appelez cette méthode pour supprimer un objet désigné par un `CHeapPtrBase` .

```cpp
void Free() throw();
```

### <a name="remarks"></a>Notes

L’objet pointé par `CHeapPtrBase` est libéré et la variable membre [CHeapPtrBase :: m_pData](#m_pdata) a la valeur null.

## <a name="cheapptrbasem_pdata"></a><a name="m_pdata"></a> CHeapPtrBase :: m_pData

Variable de membre de données de pointeur.

```
T* m_pData;
```

### <a name="remarks"></a>Notes

Cette variable membre contient les informations de pointeur.

## <a name="cheapptrbaseoperator-amp"></a><a name="operator_amp"></a> CHeapPtrBase ::, opérateur &amp;

Opérateur &.

```
T** operator&() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne l’adresse de l’objet vers lequel pointe l' `CHeapPtrBase` objet.

## <a name="cheapptrbaseoperator--gt"></a><a name="operator_ptr"></a> CHeapPtrBase :: Operator-&gt;

Opérateur pointeur vers membre.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur de la variable membre [CHeapPtrBase :: m_pData](#m_pdata) .

### <a name="remarks"></a>Notes

Utilisez cet opérateur pour appeler une méthode dans une classe vers laquelle pointe l' `CHeapPtrBase` objet. Dans les versions Debug, un échec d’assertion se produit si le `CHeapPtrBase` pointe vers la valeur null.

## <a name="cheapptrbaseoperator-t"></a><a name="operator_t_star"></a> CHeapPtrBase :: Operator T *

Opérateur de cast.

```
operator T*() const throw();
```

### <a name="remarks"></a>Notes

Retourne [CHeapPtrBase :: m_pData](#m_pdata).

## <a name="cheapptrbasereallocatebytes"></a><a name="reallocatebytes"></a> CHeapPtrBase::ReallocateBytes

Appelez cette méthode pour réallouer la mémoire.

```
bool ReallocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*nBytes*<br/>
Nouvelle quantité de mémoire à allouer, en octets.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si la mémoire est allouée avec succès ; sinon, false.

## <a name="see-also"></a>Voir aussi

[CHeapPtr, classe](../../atl/reference/cheapptr-class.md)<br/>
[CComHeapPtr, classe](../../atl/reference/ccomheapptr-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
