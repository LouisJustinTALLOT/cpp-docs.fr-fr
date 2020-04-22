---
title: Classe CRBTree
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
ms.openlocfilehash: 58c001ccef35d4265ef5b7fe200654781f130872
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746579"
---
# <a name="crbtree-class"></a>Classe CRBTree

Cette classe fournit des méthodes pour créer et utiliser un arbre rouge-noir.

## <a name="syntax"></a>Syntaxe

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBTree
```

#### <a name="parameters"></a>Paramètres

*K*<br/>
Le type d’élément clé.

*C*<br/>
Le type d’élément de valeur.

*Les KTraits*<br/>
Le code utilisé pour copier ou déplacer des éléments clés. Voir [CElementTraits Class](../../atl/reference/celementtraits-class.md) pour plus de détails.

*VTraits*<br/>
Le code utilisé pour copier ou déplacer des éléments de valeur.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CRBTree::KINARGTYPE](#kinargtype)|Type utilisé lorsqu’une clé est passée comme argument d’entrée.|
|[CRBTree::KOUTARGTYPE](#koutargtype)|Type utilisé lorsqu’une clé est retournée comme argument de sortie.|
|[CRBTree::VINARGTYPE](#vinargtype)|Type utilisé lorsqu’une valeur est adoptée comme argument d’entrée.|
|[CRBTree::VOUTARGTYPE](#voutargtype)|Type utilisé lorsqu’une valeur est adoptée comme argument de sortie.|

### <a name="public-classes"></a>Classes publiques

|Nom|Description|
|----------|-----------------|
|[CRBTree::Classe CPair](#cpair_class)|Une classe contenant la clé et les éléments de valeur.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRBTree: :CRBTree](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRBTree::FindFirstKeyAprès](#findfirstkeyafter)|Appelez cette méthode pour trouver la position de l’élément qui utilise la prochaine clé disponible.|
|[CRBTree::GetAt](#getat)|Appelez cette méthode pour obtenir l’élément à une position donnée dans l’arbre.|
|[CRBTree::GetCount](#getcount)|Appelez cette méthode pour obtenir le nombre d’éléments dans l’arbre.|
|[CRBTree::GetHeadPosition](#getheadposition)|Appelez cette méthode pour obtenir la valeur de position pour l’élément à la tête de l’arbre.|
|[CRBTree::GetKeyAt](#getkeyat)|Appelez cette méthode pour obtenir la clé à partir d’une position donnée dans l’arbre.|
|[CRBTree::GetNext](#getnext)|Appelez cette méthode pour obtenir un pointeur sur un élément stocké dans l’objet, `CRBTree` et avancer la position à l’élément suivant.|
|[CRBTree::GetNextAssoc](#getnextassoc)|Appelez cette méthode pour obtenir la clé et la valeur d’un élément stocké dans la carte et faire avancer la position à l’élément suivant.|
|[CRBTree::GetNextKey](#getnextkey)|Appelez cette méthode pour obtenir la clé d’un élément stocké dans l’arbre et avancer la position à l’élément suivant.|
|[CRBTree::GetNextValue](#getnextvalue)|Appelez cette méthode pour obtenir la valeur d’un élément stocké dans l’arbre et faire avancer la position à l’élément suivant.|
|[CRBTree::GetPrev](#getprev)|Appelez cette méthode pour obtenir un pointeur sur un élément stocké dans l’objet, `CRBTree` puis mettre à jour la position à l’élément précédent.|
|[CRBTree::GetTailPosition](#gettailposition)|Appelez cette méthode pour obtenir la valeur de position pour l’élément à la queue de l’arbre.|
|[CRBTree::GetValueAt](#getvalueat)|Appelez cette méthode pour récupérer la valeur `CRBTree` stockée à une position donnée dans l’objet.|
|[CRBTree::IsEmpty](#isempty)|Appelez cette méthode pour tester un objet d’arbre vide.|
|[CRBTree::RemoveAll](#removeall)|Appelez cette méthode pour supprimer `CRBTree` tous les éléments de l’objet.|
|[CRBTree::RemoveAt](#removeat)|Appelez cette méthode pour supprimer l’élément `CRBTree` à la position donnée dans l’objet.|
|[CRBTree::SetValueAt](#setvalueat)|Appelez cette méthode pour modifier la valeur `CRBTree` stockée à une position donnée dans l’objet.|

## <a name="remarks"></a>Notes

Un arbre rouge-noir est un arbre de recherche binaire qui utilise un bit supplémentaire d’information par nœud pour s’assurer qu’il reste «équilibré», c’est-à-dire, la hauteur de l’arbre ne pousse pas de façon disproportionnée grande et affecter les performances.

Cette classe de modèle est conçue pour être utilisée par [CRBMap](../../atl/reference/crbmap-class.md) et [CRBMultiMap](../../atl/reference/crbmultimap-class.md). La majeure partie des méthodes qui composent `CRBTree`ces classes dérivées sont fournies par .

Pour une discussion plus complète des différentes classes de collection et de leurs caractéristiques et caractéristiques de performance, voir [atL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlcoll.h

## <a name="crbtreecpair-class"></a><a name="cpair_class"></a>CRBTree::Classe CPair

Une classe contenant la clé et les éléments de valeur.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Notes

Cette classe est utilisée par les méthodes [CRBTree::GetAt](#getat), [CRBTree::GetNext](#getnext), et [CRBTree::GetPrev](#getprev) pour accéder à la clé et les éléments de valeur stockés dans la structure de l’arbre.

Les membres sont les suivants :

|||
|-|-|
|`m_key`|Le membre des données stockant l’élément clé.|
|`m_value`|Le membre des données stockant l’élément de valeur.|

## <a name="crbtreecrbtree"></a><a name="dtor"></a>CRBTree: :CRBTree

Destructeur.

```
~CRBTree() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées. Appels [CRBTree::RemoveAll](#removeall) pour supprimer tous les éléments.

## <a name="crbtreefindfirstkeyafter"></a><a name="findfirstkeyafter"></a>CRBTree::FindFirstKeyAprès

Appelez cette méthode pour trouver la position de l’élément qui utilise la prochaine clé disponible.

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de position de l’élément qui utilise la prochaine clé disponible. S’il n’y a plus d’éléments, NULL est retourné.

### <a name="remarks"></a>Notes

Cette méthode facilite la traversée de l’arbre sans avoir à calculer les valeurs de position à l’avance.

## <a name="crbtreegetat"></a><a name="getat"></a>CRBTree::GetAt

Appelez cette méthode pour obtenir l’élément à une position donnée dans l’arbre.

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Valeur de la position.

*key*<br/>
La variable qui reçoit la clé.

*value*<br/>
La variable qui reçoit la valeur.

### <a name="return-value"></a>Valeur de retour

Les deux premiers formulaires renvoient un pointeur à un [CPair](#cpair_class). Le troisième formulaire obtient une clé et une valeur pour le poste donné.

### <a name="remarks"></a>Notes

La valeur de position peut être précédemment déterminée avec un appel à une méthode telle que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::GetTailPosition](#gettailposition).

Dans les constructions de débog, une défaillance d’affirmation se produira si *pos* est égal à NULL.

## <a name="crbtreegetcount"></a><a name="getcount"></a>CRBTree::GetCount

Appelez cette méthode pour obtenir le nombre d’éléments dans l’arbre.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments (chaque paire de clé/valeur est un élément) stocké dans l’arbre.

## <a name="crbtreegetheadposition"></a><a name="getheadposition"></a>CRBTree::GetHeadPosition

Appelez cette méthode pour obtenir la valeur de position pour l’élément à la tête de l’arbre.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de position de l’élément à la tête de l’arbre.

### <a name="remarks"></a>Notes

La valeur `GetHeadPosition` retournée par peut être utilisée avec des méthodes telles que [CRBTree::GetKeyAt](#getkeyat) ou [CRBTree::GetNext](#getnext) pour traverser l’arbre et récupérer les valeurs.

## <a name="crbtreegetkeyat"></a><a name="getkeyat"></a>CRBTree::GetKeyAt

Appelez cette méthode pour obtenir la clé à partir d’une position donnée dans l’arbre.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Valeur de la position.

### <a name="return-value"></a>Valeur de retour

Retourne la clé stockée à la position *pos* dans l’arbre.

### <a name="remarks"></a>Notes

Si *pos* n’est pas une valeur de position valide, les résultats sont imprévisibles. Dans les constructions de débog, une défaillance d’affirmation se produira si *pos* est égal à NULL.

## <a name="crbtreegetnext"></a><a name="getnext"></a>CRBTree::GetNext

Appelez cette méthode pour obtenir un pointeur sur un élément stocké dans l’objet, `CRBTree` et avancer la position à l’élément suivant.

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur à la prochaine valeur [CPair](#cpair_class) dans l’arbre.

### <a name="remarks"></a>Notes

Le compteur de position *pos* est mis à jour après chaque appel. Si l’élément récupéré est le dernier de l’arbre, *le pos* est réglé sur NULL.

## <a name="crbtreegetnextassoc"></a><a name="getnextassoc"></a>CRBTree::GetNextAssoc

Appelez cette méthode pour obtenir la clé et la valeur d’un élément stocké dans la carte et faire avancer la position à l’élément suivant.

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

*key*<br/>
Paramètre de modèle spécifiant le type de clé de l’arbre.

*value*<br/>
Paramètre de modèle spécifiant le type de valeur de l’arbre.

### <a name="remarks"></a>Notes

Le compteur de position *pos* est mis à jour après chaque appel. Si l’élément récupéré est le dernier de l’arbre, *le pos* est réglé sur NULL.

## <a name="crbtreegetnextkey"></a><a name="getnextkey"></a>CRBTree::GetNextKey

Appelez cette méthode pour obtenir la clé d’un élément stocké dans l’arbre et avancer la position à l’élément suivant.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la prochaine clé de l’arbre.

### <a name="remarks"></a>Notes

Mises à jour du compteur de position actuel, *pos*. S’il n’y a plus d’entrées dans l’arbre, le compteur de position est réglé sur NULL.

## <a name="crbtreegetnextvalue"></a><a name="getnextvalue"></a>CRBTree::GetNextValue

Appelez cette méthode pour obtenir la valeur d’un élément stocké dans l’arbre et faire avancer la position à l’élément suivant.

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la valeur suivante dans l’arbre.

### <a name="remarks"></a>Notes

Mises à jour du compteur de position actuel, *pos*. S’il n’y a plus d’entrées dans l’arbre, le compteur de position est réglé sur NULL.

## <a name="crbtreegetprev"></a><a name="getprev"></a>CRBTree::GetPrev

Appelez cette méthode pour obtenir un pointeur sur un élément stocké dans l’objet, `CRBTree` puis mettre à jour la position à l’élément précédent.

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur sur la valeur [CPair](#cpair_class) précédente stockée dans l’arbre.

### <a name="remarks"></a>Notes

Mises à jour du compteur de position actuel, *pos*. S’il n’y a plus d’entrées dans l’arbre, le compteur de position est réglé sur NULL.

## <a name="crbtreegettailposition"></a><a name="gettailposition"></a>CRBTree::GetTailPosition

Appelez cette méthode pour obtenir la valeur de position pour l’élément à la queue de l’arbre.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de position de l’élément à la queue de l’arbre.

### <a name="remarks"></a>Notes

La valeur `GetTailPosition` retournée par peut être utilisée avec des méthodes telles que [CRBTree::GetKeyAt](#getkeyat) ou [CRBTree::GetPrev](#getprev) pour traverser l’arbre et récupérer les valeurs.

## <a name="crbtreegetvalueat"></a><a name="getvalueat"></a>CRBTree::GetValueAt

Appelez cette méthode pour récupérer la valeur `CRBTree` stockée à une position donnée dans l’objet.

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valeur de retour

Renvoie une référence à la valeur `CRBTree` stockée à la position donnée de l’objet.

## <a name="crbtreeisempty"></a><a name="isempty"></a>CRBTree::IsEmpty

Appelez cette méthode pour tester un objet d’arbre vide.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’arbre est vide, FALSE autrement.

## <a name="crbtreekinargtype"></a><a name="kinargtype"></a>CRBTree::KINARGTYPE

Type utilisé lorsqu’une clé est passée comme argument d’entrée.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="crbtreekoutargtype"></a><a name="koutargtype"></a>CRBTree::KOUTARGTYPE

Type utilisé lorsqu’une clé est retournée comme argument de sortie.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="crbtreeremoveall"></a><a name="removeall"></a>CRBTree::RemoveAll

Appelez cette méthode pour supprimer `CRBTree` tous les éléments de l’objet.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Notes

Efface l’objet, `CRBTree` libérant la mémoire utilisée pour stocker les éléments.

## <a name="crbtreeremoveat"></a><a name="removeat"></a>CRBTree::RemoveAt

Appelez cette méthode pour supprimer l’élément `CRBTree` à la position donnée dans l’objet.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="remarks"></a>Notes

Supprime la paire de clés/valeur stockées à la position spécifiée. La mémoire utilisée pour stocker l’élément est libérée. Le POSITION référencé par *pos* devient invalide, et bien que la POSITION de tout autre élément dans l’arbre reste valide, ils ne conservent pas nécessairement le même ordre.

## <a name="crbtreesetvalueat"></a><a name="setvalueat"></a>CRBTree::SetValueAt

Appelez cette méthode pour modifier la valeur `CRBTree` stockée à une position donnée dans l’objet.

```cpp
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

*value*<br/>
La valeur à `CRBTree` ajouter à l’objet.

### <a name="remarks"></a>Notes

Modifie l’élément de valeur stocké `CRBTree` à la position donnée de l’objet.

## <a name="crbtreevinargtype"></a><a name="vinargtype"></a>CRBTree::VINARGTYPE

Type utilisé lorsqu’une valeur est adoptée comme argument d’entrée.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="crbtreevoutargtype"></a><a name="voutargtype"></a>CRBTree::VOUTARGTYPE

Type utilisé lorsqu’une valeur est adoptée comme argument de sortie.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
