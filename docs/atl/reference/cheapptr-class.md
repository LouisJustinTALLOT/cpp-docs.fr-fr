---
title: Cheapptr, classe
ms.date: 11/04/2016
f1_keywords:
- CHeapPtr
- ATLCORE/ATL::CHeapPtr
- ATLCORE/ATL::CHeapPtr::CHeapPtr
- ATLCORE/ATL::CHeapPtr::Allocate
- ATLCORE/ATL::CHeapPtr::Reallocate
helpviewer_keywords:
- CHeapPtr class
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
ms.openlocfilehash: 8373d7ee0fc32b89891281e0fbd4b685ce40f0e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632373"
---
# <a name="cheapptr-class"></a>Cheapptr, classe

Une classe de pointeur intelligent pour la gestion des pointeurs de tas.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename T, class Allocator=CCRTAllocator>
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type d’objet à stocker sur le tas.

*Allocateur*<br/>
La classe d’allocation de mémoire à utiliser.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHeapPtr::CHeapPtr](#cheapptr)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHeapPtr::Allocate](#allocate)|Appelez cette méthode pour allouer de la mémoire sur le tas pour stocker des objets.|
|[CHeapPtr::Reallocate](#reallocate)|Appelez cette méthode pour réallouer la mémoire sur le tas.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CHeapPtr::operator =](#operator_eq)|L’opérateur d’assignation.|

## <a name="remarks"></a>Notes

`CHeapPtr` est dérivé de [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) et par défaut utilise les routines CRT (dans [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)) à allouer et libérer la mémoire. La classe [CHeapPtrList](../../atl/reference/cheapptrlist-class.md) peuvent être utilisés pour construire une liste de pointeurs de tas. Voir aussi [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), qui utilise les routines d’allocation de mémoire COM.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcore.h

##  <a name="allocate"></a>  CHeapPtr::Allocate

Appelez cette méthode pour allouer de la mémoire sur le tas pour stocker des objets.

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>Paramètres

*nElements*<br/>
Le nombre d’éléments utilisée pour calculer la quantité de mémoire à allouer. La valeur par défaut est 1.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si la mémoire a été allouée, false en cas d’échec.

### <a name="remarks"></a>Notes

Les routines d’allocateur servent à réserver suffisamment de mémoire sur le tas pour stocker *nElement* objets d’un type défini dans le constructeur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

##  <a name="cheapptr"></a>  CHeapPtr::CHeapPtr

Constructeur.

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Un pointeur de tas existant ou `CHeapPtr`.

### <a name="remarks"></a>Notes

Le pointeur de segment de mémoire peut éventuellement être créé à l’aide d’un pointeur existant, ou un `CHeapPtr` objet. Dans ce cas, la nouvelle `CHeapPtr` objet assume la responsabilité de gérer le nouveau pointeur et les ressources.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

##  <a name="operator_eq"></a>  CHeapPtr::operator =

Opérateur d'assignation.

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Objet `CHeapPtr` existant.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la mise à jour `CHeapPtr`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

##  <a name="reallocate"></a>  CHeapPtr::Reallocate

Appelez cette méthode pour réallouer la mémoire sur le tas.

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>Paramètres

*nElements*<br/>
Le nouveau nombre d’éléments utilisée pour calculer la quantité de mémoire à allouer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si la mémoire a été allouée, false en cas d’échec.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>Voir aussi

[CHeapPtrBase, classe](../../atl/reference/cheapptrbase-class.md)<br/>
[CCRTAllocator, classe](../../atl/reference/ccrtallocator-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
