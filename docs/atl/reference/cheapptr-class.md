---
title: Classe CHeapPtr
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
ms.openlocfilehash: a512aa974cb57072915f887f0c2a20ed1263ffa3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326916"
---
# <a name="cheapptr-class"></a>Classe CHeapPtr

Une classe de pointeur intelligent pour gérer les pointeurs de tas.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename T, class Allocator=CCRTAllocator>
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type d’objet à stocker sur le tas.

*Allocator*<br/>
La classe d’allocation de mémoire à utiliser.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHeapPtr::CHeapPtr](#cheapptr)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHeapPtr::Allocate](#allocate)|Appelez cette méthode pour allouer la mémoire sur le tas pour stocker des objets.|
|[CHeapPtr::Réallocate](#reallocate)|Appelez cette méthode pour réaffecter la mémoire sur le tas.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CHeapPtr::opérateur](#operator_eq)|L’opérateur de l’affectation.|

## <a name="remarks"></a>Notes

`CHeapPtr`est dérivé de [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) et utilise par défaut les routines CRT (dans [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)) pour allouer et libérer la mémoire. La classe [CHeapPtrList](../../atl/reference/cheapptrlist-class.md) peut être utilisée pour construire une liste de pointeurs de tas. Voir aussi [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), qui utilise des routines d’allocation de mémoire COM.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CHeapPtrBase (en)](../../atl/reference/cheapptrbase-class.md)

`CHeapPtr`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcore.h

## <a name="cheapptrallocate"></a><a name="allocate"></a>CHeapPtr::Allocate

Appelez cette méthode pour allouer la mémoire sur le tas pour stocker des objets.

```
bool Allocate(size_t nElements = 1) throw();
```

### <a name="parameters"></a>Paramètres

*nElements*<br/>
Le nombre d’éléments utilisés pour calculer la quantité de mémoire à allouer. La valeur par défaut est 1.

### <a name="return-value"></a>Valeur de retour

Revient vrai si la mémoire a été attribuée avec succès, faux sur l’échec.

### <a name="remarks"></a>Notes

Les routines d’alloueur sont utilisées pour réserver suffisamment de mémoire sur le tas pour stocker les objets *nElement* d’un type défini dans le constructeur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]

## <a name="cheapptrcheapptr"></a><a name="cheapptr"></a>CHeapPtr::CHeapPtr

Constructeur.

```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Un pointeur de `CHeapPtr`tas existant ou .

### <a name="remarks"></a>Notes

Le pointeur de tas peut être créé en `CHeapPtr` option à l’aide d’un pointeur existant, ou d’un objet. Si c’est `CHeapPtr` le cas, le nouvel objet assume la responsabilité de la gestion du nouveau pointeur et des ressources.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]

## <a name="cheapptroperator-"></a><a name="operator_eq"></a>CHeapPtr::opérateur

Opérateur d'assignation.

```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Objet `CHeapPtr` existant.

### <a name="return-value"></a>Valeur de retour

Renvoie une référence `CHeapPtr`à la mise à jour .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]

## <a name="cheapptrreallocate"></a><a name="reallocate"></a>CHeapPtr::Réallocate

Appelez cette méthode pour réaffecter la mémoire sur le tas.

```
bool Reallocate(size_t nElements) throw();
```

### <a name="parameters"></a>Paramètres

*nElements*<br/>
Le nouveau nombre d’éléments utilisés pour calculer la quantité de mémoire à allouer.

### <a name="return-value"></a>Valeur de retour

Revient vrai si la mémoire a été attribuée avec succès, faux sur l’échec.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Classe CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)<br/>
[Classe CCRTAllocator](../../atl/reference/ccrtallocator-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
