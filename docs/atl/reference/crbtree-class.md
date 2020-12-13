---
description: 'En savoir plus sur : classe CRBTree'
title: CRBTree, classe
ms.date: 11/04/2016
f1_keywords:
- CRBTree
- ATLCOLL/ATL::CRBTree
- ATLCOLL/ATL::CRBTree::KINARGTYPE
- ATLCOLL/ATL::CRBTree::KOUTARGTYPE
- ATLCOLL/ATL::CRBTree::VINARGTYPE
- ATLCOLL/ATL::CRBTree::VOUTARGTYPE
- ATLCOLL/ATL::CRBTree::FindFirstKeyAfter
- ATLCOLL/ATL::CRBTree::GetAt
- ATLCOLL/ATL::CRBTree::GetCount
- ATLCOLL/ATL::CRBTree::GetHeadPosition
- ATLCOLL/ATL::CRBTree::GetKeyAt
- ATLCOLL/ATL::CRBTree::GetNext
- ATLCOLL/ATL::CRBTree::GetNextAssoc
- ATLCOLL/ATL::CRBTree::GetNextKey
- ATLCOLL/ATL::CRBTree::GetNextValue
- ATLCOLL/ATL::CRBTree::GetPrev
- ATLCOLL/ATL::CRBTree::GetTailPosition
- ATLCOLL/ATL::CRBTree::GetValueAt
- ATLCOLL/ATL::CRBTree::IsEmpty
- ATLCOLL/ATL::CRBTree::RemoveAll
- ATLCOLL/ATL::CRBTree::RemoveAt
- ATLCOLL/ATL::CRBTree::SetValueAt
helpviewer_keywords:
- CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
ms.openlocfilehash: 3c45c8b05429ba75905912d76f87605a07ff49e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140970"
---
# <a name="crbtree-class"></a>CRBTree, classe

Cette classe fournit des méthodes pour créer et utiliser une arborescence Red-Black.

## <a name="syntax"></a>Syntaxe

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBTree
```

#### <a name="parameters"></a>Paramètres

*DK*<br/>
Type d’élément clé.

*V*<br/>
Type d’élément de valeur.

*KTraits*<br/>
Code utilisé pour copier ou déplacer les éléments clés. Pour plus d’informations, consultez la [classe CElementTraits](../../atl/reference/celementtraits-class.md) .

*VTraits*<br/>
Code utilisé pour copier ou déplacer des éléments de valeur.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CRBTree::KINARGTYPE](#kinargtype)|Type utilisé quand une clé est passée comme argument d’entrée.|
|[CRBTree::KOUTARGTYPE](#koutargtype)|Type utilisé quand une clé est retournée en tant qu’argument de sortie.|
|[CRBTree::VINARGTYPE](#vinargtype)|Type utilisé quand une valeur est passée comme argument d’entrée.|
|[CRBTree::VOUTARGTYPE](#voutargtype)|Type utilisé quand une valeur est passée comme argument de sortie.|

### <a name="public-classes"></a>Classes publiques

|Nom|Description|
|----------|-----------------|
|[CRBTree :: CPair, classe](#cpair_class)|Classe contenant les éléments de clé et de valeur.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRBTree :: ~ CRBTree](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)|Appelez cette méthode pour rechercher la position de l’élément qui utilise la clé disponible suivante.|
|[CRBTree :: GetAt](#getat)|Appelez cette méthode pour obtenir l’élément à une position donnée dans l’arborescence.|
|[CRBTree :: GetCount](#getcount)|Appelez cette méthode pour récupérer le nombre d’éléments dans l’arborescence.|
|[CRBTree::GetHeadPosition](#getheadposition)|Appelez cette méthode pour obtenir la valeur de position de l’élément au début de l’arborescence.|
|[CRBTree::GetKeyAt](#getkeyat)|Appelez cette méthode pour obtenir la clé à partir d’une position donnée dans l’arborescence.|
|[CRBTree :: GetNext](#getnext)|Appelez cette méthode pour obtenir un pointeur vers un élément stocké dans l' `CRBTree` objet et avancer la position vers l’élément suivant.|
|[CRBTree::GetNextAssoc](#getnextassoc)|Appelez cette méthode pour récupérer la clé et la valeur d’un élément stocké dans la classe Map et avancer la position vers l’élément suivant.|
|[CRBTree::GetNextKey](#getnextkey)|Appelez cette méthode pour récupérer la clé d’un élément stocké dans l’arborescence et avancer la position vers l’élément suivant.|
|[CRBTree::GetNextValue](#getnextvalue)|Appelez cette méthode pour récupérer la valeur d’un élément stocké dans l’arborescence et avancer la position vers l’élément suivant.|
|[CRBTree::GetPrev](#getprev)|Appelez cette méthode pour obtenir un pointeur vers un élément stocké dans l' `CRBTree` objet, puis mettez à jour la position vers l’élément précédent.|
|[CRBTree::GetTailPosition](#gettailposition)|Appelez cette méthode pour obtenir la valeur de position de l’élément à la fin de l’arborescence.|
|[CRBTree::GetValueAt](#getvalueat)|Appelez cette méthode pour récupérer la valeur stockée à une position donnée dans l' `CRBTree` objet.|
|[CRBTree :: IsEmpty](#isempty)|Appelez cette méthode pour tester un objet d’arborescence vide.|
|[CRBTree :: RemoveAll](#removeall)|Appelez cette méthode pour supprimer tous les éléments de l' `CRBTree` objet.|
|[CRBTree :: RemoveAt](#removeat)|Appelez cette méthode pour supprimer l’élément à la position donnée dans l' `CRBTree` objet.|
|[CRBTree::SetValueAt](#setvalueat)|Appelez cette méthode pour modifier la valeur stockée à une position donnée dans l' `CRBTree` objet.|

## <a name="remarks"></a>Notes

Une arborescence de Red-Black est un arbre de recherche binaire qui utilise un supplément d’informations par nœud pour s’assurer qu’il reste « équilibré », c’est-à-dire que la hauteur de l’arborescence n’augmente pas de manière disproportionnée et affecte les performances.

Cette classe de modèle est conçue pour être utilisée par [CRBMap](../../atl/reference/crbmap-class.md) et [CRBMultiMap](../../atl/reference/crbmultimap-class.md). La plupart des méthodes qui composent ces classes dérivées sont fournies par `CRBTree` .

Pour une description plus complète des différentes classes de collection et de leurs fonctionnalités et caractéristiques de performances, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="crbtreecpair-class"></a><a name="cpair_class"></a> CRBTree :: CPair, classe

Classe contenant les éléments de clé et de valeur.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Notes

Cette classe est utilisée par les méthodes [CRBTree :: GetAt](#getat), [CRBTree :: GetNext](#getnext)et [CRBTree :: GetPrev](#getprev) pour accéder aux éléments de clé et de valeur stockés dans l’arborescence.

Les membres sont les suivants :

|Membre de données|Description|
|-|-|
|`m_key`|Membre de données qui stocke l’élément clé.|
|`m_value`|Membre de données qui stocke l’élément de valeur.|

## <a name="crbtreecrbtree"></a><a name="dtor"></a> CRBTree :: ~ CRBTree

Destructeur.

```
~CRBTree() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées. Appelle [CRBTree :: RemoveAll](#removeall) pour supprimer tous les éléments.

## <a name="crbtreefindfirstkeyafter"></a><a name="findfirstkeyafter"></a> CRBTree::FindFirstKeyAfter

Appelez cette méthode pour rechercher la position de l’élément qui utilise la clé disponible suivante.

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur de position de l’élément qui utilise la clé disponible suivante. S’il n’y a plus d’éléments, la valeur NULL est retournée.

### <a name="remarks"></a>Notes

Cette méthode facilite le parcours de l’arborescence sans avoir à calculer les valeurs de position au préalable.

## <a name="crbtreegetat"></a><a name="getat"></a> CRBTree :: GetAt

Appelez cette méthode pour obtenir l’élément à une position donnée dans l’arborescence.

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Valeur de la position.

*key*<br/>
Variable qui reçoit la clé.

*value*<br/>
Variable qui reçoit la valeur.

### <a name="return-value"></a>Valeur renvoyée

Les deux premières formes retournent un pointeur vers un [CPair](#cpair_class). La troisième forme obtient une clé et une valeur pour la position donnée.

### <a name="remarks"></a>Notes

La valeur de position peut être déterminée précédemment à l’aide d’un appel à une méthode telle que [CRBTree :: GetHeadPosition](#getheadposition) ou [CRBTree :: GetTailPosition](#gettailposition).

Dans les versions Debug, un échec d’assertion se produit si *pos* est égal à null.

## <a name="crbtreegetcount"></a><a name="getcount"></a> CRBTree :: GetCount

Appelez cette méthode pour récupérer le nombre d’éléments dans l’arborescence.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre d’éléments (chaque paire clé/valeur est un élément) stockée dans l’arborescence.

## <a name="crbtreegetheadposition"></a><a name="getheadposition"></a> CRBTree::GetHeadPosition

Appelez cette méthode pour obtenir la valeur de position de l’élément au début de l’arborescence.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur de position de l’élément au début de l’arborescence.

### <a name="remarks"></a>Notes

La valeur retournée par `GetHeadPosition` peut être utilisée avec des méthodes telles que [CRBTree :: GetKeyAt](#getkeyat) ou [CRBTree :: GetNext](#getnext) pour traverser l’arborescence et récupérer des valeurs.

## <a name="crbtreegetkeyat"></a><a name="getkeyat"></a> CRBTree::GetKeyAt

Appelez cette méthode pour obtenir la clé à partir d’une position donnée dans l’arborescence.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Valeur de la position.

### <a name="return-value"></a>Valeur renvoyée

Retourne la clé stockée à la position *pos* dans l’arborescence.

### <a name="remarks"></a>Notes

Si *pos* n’est pas une valeur de position valide, les résultats sont imprévisibles. Dans les versions Debug, un échec d’assertion se produit si *pos* est égal à null.

## <a name="crbtreegetnext"></a><a name="getnext"></a> CRBTree :: GetNext

Appelez cette méthode pour obtenir un pointeur vers un élément stocké dans l' `CRBTree` objet et avancer la position vers l’élément suivant.

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree :: GetHeadPosition](#getheadposition) ou [CRBTree :: FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers la valeur [CPair](#cpair_class) suivante dans l’arborescence.

### <a name="remarks"></a>Notes

Le compteur de position *pos* est mis à jour après chaque appel. Si l’élément récupéré est le dernier de l’arborescence, *pos* a la valeur null.

## <a name="crbtreegetnextassoc"></a><a name="getnextassoc"></a> CRBTree::GetNextAssoc

Appelez cette méthode pour récupérer la clé et la valeur d’un élément stocké dans la classe Map et avancer la position vers l’élément suivant.

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree :: GetHeadPosition](#getheadposition) ou [CRBTree :: FindFirstKeyAfter](#findfirstkeyafter).

*key*<br/>
Paramètre de modèle qui spécifie le type de la clé de l’arborescence.

*value*<br/>
Paramètre de modèle qui spécifie le type de la valeur de l’arborescence.

### <a name="remarks"></a>Notes

Le compteur de position *pos* est mis à jour après chaque appel. Si l’élément récupéré est le dernier de l’arborescence, *pos* a la valeur null.

## <a name="crbtreegetnextkey"></a><a name="getnextkey"></a> CRBTree::GetNextKey

Appelez cette méthode pour récupérer la clé d’un élément stocké dans l’arborescence et avancer la position vers l’élément suivant.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree :: GetHeadPosition](#getheadposition) ou [CRBTree :: FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à la clé suivante dans l’arborescence.

### <a name="remarks"></a>Notes

Met à jour le compteur de position actuelle, *pos*. S’il n’y a plus d’entrées dans l’arborescence, le compteur de position est défini sur NULL.

## <a name="crbtreegetnextvalue"></a><a name="getnextvalue"></a> CRBTree::GetNextValue

Appelez cette méthode pour récupérer la valeur d’un élément stocké dans l’arborescence et avancer la position vers l’élément suivant.

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree :: GetHeadPosition](#getheadposition) ou [CRBTree :: FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à la valeur suivante dans l’arborescence.

### <a name="remarks"></a>Notes

Met à jour le compteur de position actuelle, *pos*. S’il n’y a plus d’entrées dans l’arborescence, le compteur de position est défini sur NULL.

## <a name="crbtreegetprev"></a><a name="getprev"></a> CRBTree::GetPrev

Appelez cette méthode pour obtenir un pointeur vers un élément stocké dans l' `CRBTree` objet, puis mettez à jour la position vers l’élément précédent.

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree :: GetHeadPosition](#getheadposition) ou [CRBTree :: FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers la valeur [CPair](#cpair_class) précédente stockée dans l’arborescence.

### <a name="remarks"></a>Notes

Met à jour le compteur de position actuelle, *pos*. S’il n’y a plus d’entrées dans l’arborescence, le compteur de position est défini sur NULL.

## <a name="crbtreegettailposition"></a><a name="gettailposition"></a> CRBTree::GetTailPosition

Appelez cette méthode pour obtenir la valeur de position de l’élément à la fin de l’arborescence.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur de position de l’élément à la fin de l’arborescence.

### <a name="remarks"></a>Notes

La valeur retournée par `GetTailPosition` peut être utilisée avec des méthodes telles que [CRBTree :: GetKeyAt](#getkeyat) ou [CRBTree :: GetPrev](#getprev) pour parcourir l’arborescence et récupérer des valeurs.

## <a name="crbtreegetvalueat"></a><a name="getvalueat"></a> CRBTree::GetValueAt

Appelez cette méthode pour récupérer la valeur stockée à une position donnée dans l' `CRBTree` objet.

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree :: GetHeadPosition](#getheadposition) ou [CRBTree :: FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à la valeur stockée à la position donnée dans l' `CRBTree` objet.

## <a name="crbtreeisempty"></a><a name="isempty"></a> CRBTree :: IsEmpty

Appelez cette méthode pour tester un objet d’arborescence vide.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si l’arborescence est vide ; sinon, FALSe.

## <a name="crbtreekinargtype"></a><a name="kinargtype"></a> CRBTree::KINARGTYPE

Type utilisé quand une clé est passée comme argument d’entrée.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="crbtreekoutargtype"></a><a name="koutargtype"></a> CRBTree::KOUTARGTYPE

Type utilisé quand une clé est retournée en tant qu’argument de sortie.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="crbtreeremoveall"></a><a name="removeall"></a> CRBTree :: RemoveAll

Appelez cette méthode pour supprimer tous les éléments de l' `CRBTree` objet.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Notes

Efface l' `CRBTree` objet et libère la mémoire utilisée pour stocker les éléments.

## <a name="crbtreeremoveat"></a><a name="removeat"></a> CRBTree :: RemoveAt

Appelez cette méthode pour supprimer l’élément à la position donnée dans l' `CRBTree` objet.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree :: GetHeadPosition](#getheadposition) ou [CRBTree :: FindFirstKeyAfter](#findfirstkeyafter).

### <a name="remarks"></a>Notes

Supprime la paire clé/valeur stockée à la position spécifiée. La mémoire utilisée pour stocker l’élément est libérée. La POSITION référencée par *pos* devient non valide et, tandis que la position de tous les autres éléments de l’arborescence reste valide, elle ne conserve pas nécessairement le même ordre.

## <a name="crbtreesetvalueat"></a><a name="setvalueat"></a> CRBTree::SetValueAt

Appelez cette méthode pour modifier la valeur stockée à une position donnée dans l' `CRBTree` objet.

```cpp
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree :: GetHeadPosition](#getheadposition) ou [CRBTree :: FindFirstKeyAfter](#findfirstkeyafter).

*value*<br/>
Valeur à ajouter à l' `CRBTree` objet.

### <a name="remarks"></a>Notes

Modifie l’élément de valeur stocké à la position donnée dans l' `CRBTree` objet.

## <a name="crbtreevinargtype"></a><a name="vinargtype"></a> CRBTree::VINARGTYPE

Type utilisé quand une valeur est passée comme argument d’entrée.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="crbtreevoutargtype"></a><a name="voutargtype"></a> CRBTree::VOUTARGTYPE

Type utilisé quand une valeur est passée comme argument de sortie.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
