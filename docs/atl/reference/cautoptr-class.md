---
title: Classe CAutoPtr
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
ms.openlocfilehash: cb8e3d6b71db6ab60b3b246bd8c5bf4f2c9aaa34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321255"
---
# <a name="cautoptr-class"></a>Classe CAutoPtr

Cette classe représente un objet pointeur intelligent.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CAutoPtr
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de pointeur.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAutoPtr::CAutoPtr](#cautoptr)|Constructeur.|
|[CAutoPtr: :CAutoPtr](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAutoPtr::Attach](#attach)|Appelez cette méthode pour prendre possession d’un pointeur existant.|
|[CAutoPtr::Detach](#detach)|Appelez cette méthode pour libérer la propriété d’un pointeur.|
|[CAutoPtr::Gratuit](#free)|Appelez cette méthode pour supprimer un `CAutoPtr`objet pointé par un .|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAutoPtr::opérateur T](#operator_t_star)|L’opérateur de distribution.|
|[CAutoPtr::opérateur](#operator_eq)|L’opérateur de l’affectation.|
|[CAutoPtr::opérateur ->](#operator_ptr)|L’opérateur pointeur-à-membre.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAutoPtr::m_p](#m_p)|La variable de membre des données de pointeur.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes pour créer et gérer un pointeur intelligent, ce qui aidera à se protéger contre les fuites de mémoire en libérant automatiquement des ressources lorsqu’elle tombe hors de portée.

De `CAutoPtr`plus, le constructeur de copie et l’opérateur d’affectation de l’opérateur de l’affectation de la propriété du pointeur, copiant le pointeur source au pointeur de destination et fixant le pointeur source à NULL. Il est donc impossible `CAutoPtr` d’avoir deux objets chacun stockant le même pointeur, ce qui réduit la possibilité de supprimer le même pointeur deux fois.

`CAutoPtr`simplifie également la création de collections de pointeurs. Au lieu de dérier une classe de collection et de dépasser le destructeur, il est plus simple de faire une collection d’objets. `CAutoPtr` Lorsque la collection est `CAutoPtr` supprimée, les objets sortent de leur portée et se suppriment automatiquement.

[CHeapPtr](../../atl/reference/cheapptr-class.md) et les variantes fonctionnent `CAutoPtr`de la même manière que , sauf qu’ils allouent et la mémoire libre en utilisant différentes fonctions de tas au lieu de la C **'nouveaux** opérateurs et **supprimer.** [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) est `CAutoPtr`similaire à , la seule différence étant qu’il utilise **vecteur nouveau []** et **vecteur supprimer []** pour allouer et la mémoire libre.

Voir aussi [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) et [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) lorsque des tableaux ou des listes de pointeurs intelligents sont nécessaires.

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

## <a name="cautoptrattach"></a><a name="attach"></a>CAutoPtr::Attach

Appelez cette méthode pour prendre possession d’un pointeur existant.

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
L’objet `CAutoPtr` s’appropriera ce pointeur.

### <a name="remarks"></a>Notes

Lorsqu’un `CAutoPtr` objet prend possession d’un pointeur, il supprime automatiquement le pointeur et les données allouées lorsqu’il n’est pas de portée. Si [CAutoPtr: :Detach](#detach) est appelé, le programmeur est de nouveau chargé de libérer les ressources allouées.

Dans les constructions de débog, une défaillance d’affirmation se produira si le [CAutoPtr : : m_p](#m_p) membre des données indique actuellement une valeur existante ; c’est-à-dire qu’il n’est pas égal à NULL.

### <a name="example"></a>Exemple

Voir l’exemple dans le [CAutoPtr Overview](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="cautoptr"></a>CAutoPtr::CAutoPtr

Constructeur.

```
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Un pointeur existant.

*TSrc (TSrc)*<br/>
Le type étant `CAutoPtr`géré par un autre , utilisé pour initialiser l’objet actuel.

### <a name="remarks"></a>Notes

L’objet `CAutoPtr` peut être créé à l’aide d’un pointeur existant, auquel cas il transfère la propriété du pointeur.

### <a name="example"></a>Exemple

Voir l’exemple dans le [CAutoPtr Overview](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="dtor"></a>CAutoPtr: :CAutoPtr

Destructeur.

```
~CAutoPtr() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées. Appels [CAutoPtr::Gratuit](#free).

## <a name="cautoptrdetach"></a><a name="detach"></a>CAutoPtr::Detach

Appelez cette méthode pour libérer la propriété d’un pointeur.

```
T* Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une copie du pointeur.

### <a name="remarks"></a>Notes

Libère la propriété d’un pointeur, définit le [CAutoPtr : : m_p](#m_p) variable de membre de données à NULL, et renvoie une copie du pointeur. Après `Detach`l’appel, il appartient au programmeur de libérer `CAutoPtr` toutes les ressources allouées sur lesquelles l’objet peut avoir déjà assumé la reponsabilité.

### <a name="example"></a>Exemple

Voir l’exemple dans le [CAutoPtr Overview](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrfree"></a><a name="free"></a>CAutoPtr::Gratuit

Appelez cette méthode pour supprimer un `CAutoPtr`objet pointé par un .

```
void Free() throw();
```

### <a name="remarks"></a>Notes

L’objet pointé `CAutoPtr` par le est libéré, et le [CAutoPtr::m_p](#m_p) variable de membre de données est réglé à NULL.

## <a name="cautoptrm_p"></a><a name="m_p"></a>CAutoPtr::m_p

La variable de membre des données de pointeur.

```
T* m_p;
```

### <a name="remarks"></a>Notes

Cette variable de membre contient l’information de pointeur.

## <a name="cautoptroperator-"></a><a name="operator_eq"></a>CAutoPtr::opérateur

L’opérateur de l’affectation.

```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>Paramètres

*P*<br/>
Un pointeur.

*TSrc (TSrc)*<br/>
Un type de classe.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à un **CAutoPtr\< T >**.

### <a name="remarks"></a>Notes

L’opérateur d’affectation `CAutoPtr` détache l’objet de n’importe quel pointeur actuel et attache le nouveau pointeur, *p*, à sa place.

### <a name="example"></a>Exemple

Voir l’exemple dans le [CAutoPtr Overview](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator--gt"></a><a name="operator_ptr"></a>CAutoPtr::opérateur -&gt;

L’opérateur pointeur-à-membre.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la variable de membre [CAutoPtr: :m_p](#m_p) de données.

### <a name="remarks"></a>Notes

Utilisez cet opérateur pour appeler une méthode `CAutoPtr` dans une classe pointée par l’objet. Dans les constructions de débog, `CAutoPtr` une défaillance d’affirmation se produira si les points à NULL.

### <a name="example"></a>Exemple

Voir l’exemple dans le [CAutoPtr Overview](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator-t"></a><a name="operator_t_star"></a>CAutoPtr::opérateur T

L’opérateur de distribution.

```
operator T* () const throw();
```

### <a name="return-value"></a>Valeur de retour

Renvoie un pointeur au type de données d’objet défini dans le modèle de classe.

### <a name="example"></a>Exemple

Voir l’exemple dans le [CAutoPtr Overview](../../atl/reference/cautoptr-class.md).

## <a name="see-also"></a>Voir aussi

[Classe CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Classe CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
