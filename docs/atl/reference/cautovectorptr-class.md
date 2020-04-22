---
title: Classe CAutoVectorPtr
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
ms.openlocfilehash: fc4bd4ba7a2f41a25679f1da718671f525519708
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748216"
---
# <a name="cautovectorptr-class"></a>Classe CAutoVectorPtr

Cette classe représente un objet pointeur intelligent à l’aide de nouveaux opérateurs vecteurs et supprimer.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CAutoVectorPtr
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de pointeur.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|Constructeur.|
|[CAutoVectorPtr: CAutoVectorPtr](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAutoVectorPtr::Allocate](#allocate)|Appelez cette méthode pour allouer la mémoire requise `CAutoVectorPtr`par la gamme d’objets pointés par .|
|[CAutoVectorPtr::Attach](#attach)|Appelez cette méthode pour prendre possession d’un pointeur existant.|
|[CAutoVectorPtr::Detach](#detach)|Appelez cette méthode pour libérer la propriété d’un pointeur.|
|[CAutoVectorPtr::Gratuit](#free)|Appelez cette méthode pour supprimer un `CAutoVectorPtr`objet pointé par un .|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAutoVectorPtr::opérateur T](#operator_t__star)|L’opérateur de distribution.|
|[CAutoVectorPtr::opérateur](#operator_eq)|L’opérateur de l’affectation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAutoVectorPtr::m_p](#m_p)|La variable de membre des données de pointeur.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes pour créer et gérer un pointeur intelligent, ce qui aidera à se protéger contre les fuites de mémoire en libérant automatiquement des ressources lorsqu’elle tombe hors de portée. `CAutoVectorPtr`est similaire `CAutoPtr`à , la `CAutoVectorPtr` seule différence étant que les [utilisations vecteurs de nouvelles&#91;&#93;](../../standard-library/new-operators.md#op_new_arr) et [vecteur supprimer&#91;&#93;](../../standard-library/new-operators.md#op_delete_arr) d’allouer et de mémoire libre au lieu de la C **'nouveaux** opérateurs et **supprimer.** Voir [CAutoVectorPtrElrElraits](../../atl/reference/cautovectorptrelementtraits-class.md) si `CAutoVectorPtr` des classes de collecte sont nécessaires.

Voir [CAutoPtr](../../atl/reference/cautoptr-class.md) pour un exemple d’utilisation d’une classe de pointeur intelligent.

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="cautovectorptrallocate"></a><a name="allocate"></a>CAutoVectorPtr::Allocate

Appelez cette méthode pour allouer la mémoire requise `CAutoVectorPtr`par la gamme d’objets pointés par .

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>Paramètres

*nElements*<br/>
Nombre d’éléments dans le tableau.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si la mémoire est attribuée avec succès, fausse sur l’échec.

### <a name="remarks"></a>Notes

Dans les constructions de déboguer, une défaillance d’affirmation se produira si le [CAutoVectorPtr : : m_p](#m_p) variable de membre indique actuellement une valeur existante ; c’est-à-dire qu’il n’est pas égal à NULL.

## <a name="cautovectorptrattach"></a><a name="attach"></a>CAutoVectorPtr::Attach

Appelez cette méthode pour prendre possession d’un pointeur existant.

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
L’objet `CAutoVectorPtr` s’appropriera ce pointeur.

### <a name="remarks"></a>Notes

Lorsqu’un `CAutoVectorPtr` objet prend possession d’un pointeur, il supprime automatiquement le pointeur et les données allouées lorsqu’il n’est pas de portée. Si [CAutoVectorPtr::Detach](#detach) est appelé, le programmeur est de nouveau chargé de libérer les ressources allouées.

Dans les constructions de déboguer, une défaillance d’affirmation se produira si le [CAutoVectorPtr : : m_p](#m_p) variable de membre indique actuellement une valeur existante ; c’est-à-dire qu’il n’est pas égal à NULL.

## <a name="cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr

Constructeur.

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Un pointeur existant.

### <a name="remarks"></a>Notes

L’objet `CAutoVectorPtr` peut être créé à l’aide d’un pointeur existant, auquel cas il transfère la propriété du pointeur.

## <a name="cautovectorptrcautovectorptr"></a><a name="dtor"></a>CAutoVectorPtr: CAutoVectorPtr

Destructeur.

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées. Appels [CAutoVectorPtr::Gratuit](#free).

## <a name="cautovectorptrdetach"></a><a name="detach"></a>CAutoVectorPtr::Detach

Appelez cette méthode pour libérer la propriété d’un pointeur.

```
T* Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une copie du pointeur.

### <a name="remarks"></a>Notes

Libère la propriété d’un pointeur, définit le [CAutoVectorPtr : : m_p](#m_p) variable de membre à NULL, et renvoie une copie du pointeur. Après `Detach`avoir appelé, il appartient au programmeur de libérer `CAutoVectorPtr` toutes les ressources allouées sur lesquelles l’objet peut avoir précédemment assumé la responsabilité.

## <a name="cautovectorptrfree"></a><a name="free"></a>CAutoVectorPtr::Gratuit

Appelez cette méthode pour supprimer un `CAutoVectorPtr`objet pointé par un .

```cpp
void Free() throw();
```

### <a name="remarks"></a>Notes

L’objet pointé `CAutoVectorPtr` par le est libéré, et le [CAutoVectorPtr::m_p](#m_p) variable membre est réglé à NULL.

## <a name="cautovectorptrm_p"></a><a name="m_p"></a>CAutoVectorPtr::m_p

La variable de membre des données de pointeur.

```
T* m_p;
```

### <a name="remarks"></a>Notes

Cette variable de membre contient l’information de pointeur.

## <a name="cautovectorptroperator-"></a><a name="operator_eq"></a>CAutoVectorPtr::opérateur

L’opérateur de l’affectation.

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Un pointeur.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à un **CAutoVectorPtr\< T >**.

### <a name="remarks"></a>Notes

L’opérateur d’affectation `CAutoVectorPtr` détache l’objet de n’importe quel pointeur actuel et attache le nouveau pointeur, *p*, à sa place.

## <a name="cautovectorptroperator-t-"></a><a name="operator_t__star"></a>CAutoVectorPtr::opérateur T

L’opérateur de distribution.

```
operator T*() const throw();
```

### <a name="remarks"></a>Notes

Renvoie un pointeur au type de données d’objet défini dans le modèle de classe.

## <a name="see-also"></a>Voir aussi

[Classe CAutoPtr](../../atl/reference/cautoptr-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
