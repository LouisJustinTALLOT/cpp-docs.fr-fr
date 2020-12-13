---
description: 'En savoir plus sur : classe CHeapPtr'
title: CHeapPtr, classe
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
ms.openlocfilehash: dc795c199562fa423a160b053c96983651d0812d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141646"
---
# <a name="cheapptr-class"></a>CHeapPtr, classe

Classe de pointeur intelligent pour la gestion des pointeurs de tas.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename T, class Allocator=CCRTAllocator>
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type d’objet à stocker sur le tas.

*Allocateur*<br/>
Classe d’allocation de mémoire à utiliser.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHeapPtr::CHeapPtr](#cheapptr)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHeapPtr :: Allocate](#allocate)|Appelez cette méthode pour allouer de la mémoire sur le tas pour stocker des objets.|
|[CHeapPtr :: Reallocation](#reallocate)|Appelez cette méthode pour réallouer la mémoire sur le tas.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CHeapPtr :: Operator =](#operator_eq)|Opérateur d’assignation.|

## <a name="remarks"></a>Notes

`CHeapPtr` est dérivée de [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) et utilise par défaut les routines CRT (dans [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)) pour allouer et libérer de la mémoire. La classe [CHeapPtrList](../../atl/reference/cheapptrlist-class.md) peut être utilisée pour construire une liste de pointeurs de tas. Voir aussi [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), qui utilise les routines d’allocation de mémoire com.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcore. h

## <a name="cheapptrallocate"></a><a name="allocate"></a> CHeapPtr :: Allocate

Appelez cette méthode pour allouer de la mémoire sur le tas pour stocker des objets.

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>Paramètres

*nElements*<br/>
Nombre d’éléments utilisés pour calculer la quantité de mémoire à allouer. La valeur par défaut est 1.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si la mémoire a été allouée avec succès, false en cas d’échec.

### <a name="remarks"></a>Notes

Les routines d’allocation sont utilisées pour réserver suffisamment de mémoire sur le tas pour stocker les objets *nElement* d’un type défini dans le constructeur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

## <a name="cheapptrcheapptr"></a><a name="cheapptr"></a> CHeapPtr::CHeapPtr

Constructeur.

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur de tas existant ou `CHeapPtr` .

### <a name="remarks"></a>Notes

Le pointeur de tas peut éventuellement être créé à l’aide d’un pointeur existant ou d’un `CHeapPtr` objet. Dans ce cas, le nouvel `CHeapPtr` objet assume la responsabilité de la gestion du nouveau pointeur et des ressources.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

## <a name="cheapptroperator-"></a><a name="operator_eq"></a> CHeapPtr :: Operator =

Opérateur d'assignation.

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Objet `CHeapPtr` existant.

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence au mis à jour `CHeapPtr` .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

## <a name="cheapptrreallocate"></a><a name="reallocate"></a> CHeapPtr :: Reallocation

Appelez cette méthode pour réallouer la mémoire sur le tas.

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>Paramètres

*nElements*<br/>
Nouveau nombre d’éléments utilisés pour calculer la quantité de mémoire à allouer.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si la mémoire a été allouée avec succès, false en cas d’échec.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>Voir aussi

[CHeapPtrBase, classe](../../atl/reference/cheapptrbase-class.md)<br/>
[CCRTAllocator, classe](../../atl/reference/ccrtallocator-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
