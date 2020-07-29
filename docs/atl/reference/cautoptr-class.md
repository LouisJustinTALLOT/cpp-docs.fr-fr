---
title: CAutoPtr, classe
ms.date: 11/04/2016
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
ms.openlocfilehash: 699e62362bc74009e3faed3b4fd66b579c9c4cd3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226657"
---
# <a name="cautoptr-class"></a>CAutoPtr, classe

Cette classe représente un objet pointeur intelligent.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class CAutoPtr
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de pointeur.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAutoPtr::CAutoPtr](#cautoptr)|Constructeur.|
|[CAutoPtr :: ~ CAutoPtr](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAutoPtr :: Attach](#attach)|Appelez cette méthode pour prendre possession d’un pointeur existant.|
|[CAutoPtr ::D Etach](#detach)|Appelez cette méthode pour libérer la propriété d’un pointeur.|
|[CAutoPtr :: Free](#free)|Appelez cette méthode pour supprimer un objet désigné par un `CAutoPtr` .|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAutoPtr :: Operator T *](#operator_t_star)|Opérateur de cast.|
|[CAutoPtr :: Operator =](#operator_eq)|Opérateur d’assignation.|
|[CAutoPtr :: Operator->](#operator_ptr)|Opérateur pointeur vers membre.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAutoPtr :: m_p](#m_p)|Variable de membre de données de pointeur.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes pour créer et gérer un pointeur intelligent, ce qui vous permet de vous protéger contre les fuites de mémoire en libérant automatiquement les ressources lorsqu’elles sont hors de portée.

En outre, le `CAutoPtr` constructeur de copie et l’opérateur d’assignation transfère la propriété du pointeur, en copiant le pointeur source vers le pointeur de destination et en définissant le pointeur source sur la valeur null. Il est donc impossible d’avoir deux `CAutoPtr` objets qui stockent chacun le même pointeur, ce qui réduit la possibilité de supprimer deux fois le même pointeur.

`CAutoPtr`simplifie également la création de collections de pointeurs. Au lieu de dériver une classe de collection et de substituer le destructeur, il est plus simple de créer une collection d' `CAutoPtr` objets. Lorsque la collection est supprimée, les `CAutoPtr` objets sont hors de portée et se suppriment automatiquement.

Les [CHeapPtr](../../atl/reference/cheapptr-class.md) et les variantes fonctionnent de la même façon que `CAutoPtr` , sauf qu’ils allouent et libèrent de la mémoire à l’aide de différentes fonctions de tas au lieu des **`new`** opérateurs C++ et **`delete`** . [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) est similaire à `CAutoPtr` , la seule différence étant qu’il utilise **Vector New []** et **Vector delete []** pour allouer et libérer de la mémoire.

Voir aussi [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) et [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) lorsque des tableaux ou des listes de pointeurs intelligents sont requis.

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

## <a name="cautoptrattach"></a><a name="attach"></a>CAutoPtr :: Attach

Appelez cette méthode pour prendre possession d’un pointeur existant.

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
L' `CAutoPtr` objet prend la propriété de ce pointeur.

### <a name="remarks"></a>Notes

Lorsqu’un `CAutoPtr` objet prend possession d’un pointeur, il supprime automatiquement le pointeur et toutes les données allouées lorsqu’il est hors de portée. Si [CAutoPtr ::D Etach](#detach) est appelé, le programmeur est à nouveau chargé de libérer toutes les ressources allouées.

Dans les versions Debug, un échec d’assertion se produit si le membre de données [CAutoPtr :: m_p](#m_p) pointe actuellement vers une valeur existante ; autrement dit, il n’est pas égal à la valeur NULL.

### <a name="example"></a>Exemple

Consultez l’exemple dans la [vue d’ensemble de CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="cautoptr"></a>CAutoPtr::CAutoPtr

Constructeur.

```cpp
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur existant.

*TSrc*<br/>
Type géré par un autre `CAutoPtr` , utilisé pour initialiser l’objet actuel.

### <a name="remarks"></a>Notes

L' `CAutoPtr` objet peut être créé à l’aide d’un pointeur existant, auquel cas il transfère la propriété du pointeur.

### <a name="example"></a>Exemple

Consultez l’exemple dans la [vue d’ensemble de CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="dtor"></a>CAutoPtr :: ~ CAutoPtr

Destructeur.

```cpp
~CAutoPtr() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées. Appelle [CAutoPtr :: Free](#free).

## <a name="cautoptrdetach"></a><a name="detach"></a>CAutoPtr ::D Etach

Appelez cette méthode pour libérer la propriété d’un pointeur.

```cpp
T* Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une copie du pointeur.

### <a name="remarks"></a>Notes

Libère la propriété d’un pointeur, définit la variable de membre de données [CAutoPtr :: m_p](#m_p) sur la valeur null et retourne une copie du pointeur. Après l’appel de `Detach` , il incombe au programmeur de libérer toutes les ressources allouées sur lesquelles l' `CAutoPtr` objet a pu supposer Reponsibility précédemment.

### <a name="example"></a>Exemple

Consultez l’exemple dans la [vue d’ensemble de CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrfree"></a><a name="free"></a>CAutoPtr :: Free

Appelez cette méthode pour supprimer un objet désigné par un `CAutoPtr` .

```cpp
void Free() throw();
```

### <a name="remarks"></a>Notes

L’objet pointé par `CAutoPtr` est libéré, et la variable de membre de données [CAutoPtr :: m_p](#m_p) est définie sur null.

## <a name="cautoptrm_p"></a><a name="m_p"></a>CAutoPtr :: m_p

Variable de membre de données de pointeur.

```cpp
T* m_p;
```

### <a name="remarks"></a>Notes

Cette variable membre contient les informations de pointeur.

## <a name="cautoptroperator-"></a><a name="operator_eq"></a>CAutoPtr :: Operator =

Opérateur d’assignation.

```cpp
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>Paramètres

*p*<br/>
Pointeur.

*TSrc*<br/>
Type de classe.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à un **CAutoPtr \< T > **.

### <a name="remarks"></a>Notes

L’opérateur d’assignation détache l' `CAutoPtr` objet à partir de n’importe quel pointeur actuel et attache le nouveau pointeur, *p*, à la place.

### <a name="example"></a>Exemple

Consultez l’exemple dans la [vue d’ensemble de CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator--gt"></a><a name="operator_ptr"></a>CAutoPtr :: Operator-&gt;

Opérateur pointeur vers membre.

```cpp
T* operator->() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la variable de membre de données [CAutoPtr :: m_p](#m_p) .

### <a name="remarks"></a>Notes

Utilisez cet opérateur pour appeler une méthode dans une classe vers laquelle pointe l' `CAutoPtr` objet. Dans les versions Debug, un échec d’assertion se produit si le `CAutoPtr` pointe vers la valeur null.

### <a name="example"></a>Exemple

Consultez l’exemple dans la [vue d’ensemble de CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator-t"></a><a name="operator_t_star"></a>CAutoPtr :: Operator T *

Opérateur de cast.

```cpp
operator T* () const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers le type de données objet défini dans le modèle de classe.

### <a name="example"></a>Exemple

Consultez l’exemple dans la [vue d’ensemble de CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="see-also"></a>Voir aussi

[CHeapPtr, classe](../../atl/reference/cheapptr-class.md)<br/>
[CAutoVectorPtr, classe](../../atl/reference/cautovectorptr-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
