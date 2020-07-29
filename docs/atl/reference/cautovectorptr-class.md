---
title: CAutoVectorPtr, classe
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
ms.openlocfilehash: 65d37396b02d2c11c758915b201eef09cf1935b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226644"
---
# <a name="cautovectorptr-class"></a>CAutoVectorPtr, classe

Cette classe représente un objet pointeur intelligent à l’aide d’opérateurs Vector New et DELETE.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CAutoVectorPtr
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de pointeur.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|Constructeur.|
|[CAutoVectorPtr :: ~ CAutoVectorPtr](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAutoVectorPtr :: Allocate](#allocate)|Appelez cette méthode pour allouer la mémoire requise par le tableau d’objets vers lequel pointe `CAutoVectorPtr` .|
|[CAutoVectorPtr :: Attach](#attach)|Appelez cette méthode pour prendre possession d’un pointeur existant.|
|[CAutoVectorPtr ::D Etach](#detach)|Appelez cette méthode pour libérer la propriété d’un pointeur.|
|[CAutoVectorPtr :: Free](#free)|Appelez cette méthode pour supprimer un objet désigné par un `CAutoVectorPtr` .|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAutoVectorPtr :: Operator T *](#operator_t__star)|Opérateur de cast.|
|[CAutoVectorPtr :: Operator =](#operator_eq)|Opérateur d’assignation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAutoVectorPtr :: m_p](#m_p)|Variable de membre de données de pointeur.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes pour créer et gérer un pointeur intelligent, ce qui vous permet de vous protéger contre les fuites de mémoire en libérant automatiquement les ressources lorsqu’elles sont hors de portée. `CAutoVectorPtr`est semblable à `CAutoPtr` , la seule différence étant que `CAutoVectorPtr` utilise [Vector New&#91;&#93;](../../standard-library/new-operators.md#op_new_arr) et [Vector Delete&#91;&#93;](../../standard-library/new-operators.md#op_delete_arr) pour allouer et libérer de la mémoire au lieu des **`new`** opérateurs C++ et **`delete`** . Consultez [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) si les classes de collection de `CAutoVectorPtr` sont requises.

Pour obtenir un exemple d’utilisation d’une classe de pointeur intelligent, consultez [CAutoPtr](../../atl/reference/cautoptr-class.md) .

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="cautovectorptrallocate"></a><a name="allocate"></a>CAutoVectorPtr :: Allocate

Appelez cette méthode pour allouer la mémoire requise par le tableau d’objets vers lequel pointe `CAutoVectorPtr` .

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>Paramètres

*nElements*<br/>
Nombre d’éléments dans le tableau.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si la mémoire a été allouée avec succès, false en cas d’échec.

### <a name="remarks"></a>Notes

Dans les versions Debug, un échec d’assertion se produit si la variable membre [CAutoVectorPtr :: m_p](#m_p) pointe actuellement vers une valeur existante ; autrement dit, il n’est pas égal à la valeur NULL.

## <a name="cautovectorptrattach"></a><a name="attach"></a>CAutoVectorPtr :: Attach

Appelez cette méthode pour prendre possession d’un pointeur existant.

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
L' `CAutoVectorPtr` objet prend la propriété de ce pointeur.

### <a name="remarks"></a>Notes

Lorsqu’un `CAutoVectorPtr` objet prend possession d’un pointeur, il supprime automatiquement le pointeur et toutes les données allouées lorsqu’il est hors de portée. Si [CAutoVectorPtr ::D Etach](#detach) est appelé, le programmeur est à nouveau chargé de libérer toutes les ressources allouées.

Dans les versions Debug, un échec d’assertion se produit si la variable membre [CAutoVectorPtr :: m_p](#m_p) pointe actuellement vers une valeur existante ; autrement dit, il n’est pas égal à la valeur NULL.

## <a name="cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr

Constructeur.

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur existant.

### <a name="remarks"></a>Notes

L' `CAutoVectorPtr` objet peut être créé à l’aide d’un pointeur existant, auquel cas il transfère la propriété du pointeur.

## <a name="cautovectorptrcautovectorptr"></a><a name="dtor"></a>CAutoVectorPtr :: ~ CAutoVectorPtr

Destructeur.

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées. Appelle [CAutoVectorPtr :: Free](#free).

## <a name="cautovectorptrdetach"></a><a name="detach"></a>CAutoVectorPtr ::D Etach

Appelez cette méthode pour libérer la propriété d’un pointeur.

```
T* Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une copie du pointeur.

### <a name="remarks"></a>Notes

Libère la propriété d’un pointeur, définit la variable de membre [CAutoVectorPtr :: m_p](#m_p) sur la valeur null et retourne une copie du pointeur. Après l’appel de `Detach` , il incombe au programmeur de libérer toutes les ressources allouées sur lesquelles l' `CAutoVectorPtr` objet peut avoir déjà pris part à la responsabilité.

## <a name="cautovectorptrfree"></a><a name="free"></a>CAutoVectorPtr :: Free

Appelez cette méthode pour supprimer un objet désigné par un `CAutoVectorPtr` .

```cpp
void Free() throw();
```

### <a name="remarks"></a>Notes

L’objet pointé par `CAutoVectorPtr` est libéré et la variable membre [CAutoVectorPtr :: m_p](#m_p) a la valeur null.

## <a name="cautovectorptrm_p"></a><a name="m_p"></a>CAutoVectorPtr :: m_p

Variable de membre de données de pointeur.

```
T* m_p;
```

### <a name="remarks"></a>Notes

Cette variable membre contient les informations de pointeur.

## <a name="cautovectorptroperator-"></a><a name="operator_eq"></a>CAutoVectorPtr :: Operator =

Opérateur d’assignation.

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à un **CAutoVectorPtr \< T > **.

### <a name="remarks"></a>Notes

L’opérateur d’assignation détache l' `CAutoVectorPtr` objet à partir de n’importe quel pointeur actuel et attache le nouveau pointeur, *p*, à la place.

## <a name="cautovectorptroperator-t-"></a><a name="operator_t__star"></a>CAutoVectorPtr :: Operator T *

Opérateur de cast.

```
operator T*() const throw();
```

### <a name="remarks"></a>Notes

Retourne un pointeur vers le type de données objet défini dans le modèle de classe.

## <a name="see-also"></a>Voir aussi

[CAutoPtr, classe](../../atl/reference/cautoptr-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
