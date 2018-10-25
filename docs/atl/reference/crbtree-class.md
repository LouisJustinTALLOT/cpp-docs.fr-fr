---
title: Crbtree, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9e8ed5434ab9eac05c20055c788ab289800e9479
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059351"
---
# <a name="crbtree-class"></a>Crbtree, classe

Cette classe fournit des méthodes pour la création et l’utilisation d’une arborescence rouge-noire.

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

*V*<br/>
Le type d’élément de valeur.

*KTraits*<br/>
Le code utilisé pour copier ou déplacer les éléments clés. Consultez [celementtraits, classe](../../atl/reference/celementtraits-class.md) pour plus d’informations.

*VTraits*<br/>
Le code utilisé pour copier ou déplacer des éléments de valeur.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CRBTree::KINARGTYPE](#kinargtype)|Type utilisé lorsqu’une touche est passée comme argument d’entrée.|
|[CRBTree::KOUTARGTYPE](#koutargtype)|Type utilisé pour une clé est retournée comme un argument de sortie.|
|[CRBTree::VINARGTYPE](#vinargtype)|Type utilisé lorsqu’une valeur est passée comme argument d’entrée.|
|[CRBTree::VOUTARGTYPE](#voutargtype)|Type utilisé lorsqu’une valeur est passée comme un argument de sortie.|

### <a name="public-classes"></a>Classes publiques

|Nom|Description|
|----------|-----------------|
|[Classe de CRBTree::CPair](#cpair_class)|Une classe qui contient les éléments clé / valeur.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRBTree :: ~ CRBTree](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)|Appelez cette méthode pour trouver la position de l’élément qui utilise la clé disponible suivante.|
|[CRBTree::GetAt](#getat)|Appelez cette méthode pour obtenir l’élément à une position donnée dans l’arborescence.|
|[CRBTree::GetCount](#getcount)|Appelez cette méthode pour obtenir le nombre d’éléments dans l’arborescence.|
|[CRBTree::GetHeadPosition](#getheadposition)|Appelez cette méthode pour obtenir la valeur de la position de l’élément au début de l’arborescence.|
|[CRBTree::GetKeyAt](#getkeyat)|Appelez cette méthode pour obtenir la clé à partir d’une position donnée dans l’arborescence.|
|[CRBTree::GetNext](#getnext)|Appelez cette méthode pour obtenir un pointeur vers un élément stocké dans le `CRBTree` de l’objet et avance la position de l’élément suivant.|
|[CRBTree::GetNextAssoc](#getnextassoc)|Appelez cette méthode pour obtenir la clé et la valeur d’un élément stocké dans la classe map et avance la position de l’élément suivant.|
|[CRBTree::GetNextKey](#getnextkey)|Appelez cette méthode pour obtenir la clé d’un élément stocké dans l’arborescence et avance la position de l’élément suivant.|
|[CRBTree::GetNextValue](#getnextvalue)|Appelez cette méthode pour obtenir la valeur d’un élément stocké dans l’arborescence et avance la position de l’élément suivant.|
|[CRBTree::GetPrev](#getprev)|Appelez cette méthode pour obtenir un pointeur vers un élément stocké dans le `CRBTree` de l’objet, puis mettez à jour la position de l’élément précédent.|
|[CRBTree::GetTailPosition](#gettailposition)|Appelez cette méthode pour obtenir la valeur de la position de l’élément à la fin de l’arborescence.|
|[CRBTree::GetValueAt](#getvalueat)|Appelez cette méthode pour récupérer la valeur stockée à une position donnée dans le `CRBTree` objet.|
|[CRBTree::IsEmpty](#isempty)|Appelez cette méthode à tester pour un objet d’arborescence vide.|
|[CRBTree::RemoveAll](#removeall)|Appelez cette méthode pour supprimer tous les éléments à partir de la `CRBTree` objet.|
|[CRBTree::RemoveAt](#removeat)|Appelez cette méthode pour supprimer l’élément à la position donnée dans le `CRBTree` objet.|
|[CRBTree::SetValueAt](#setvalueat)|Appelez cette méthode pour modifier la valeur stockée à une position donnée dans le `CRBTree` objet.|

## <a name="remarks"></a>Notes

Une arborescence rouge-noire est une arborescence de recherche binaire qui utilise un supplémentaire des informations par nœud pour vous assurer qu’il reste « équilibre », « qui est, la hauteur de l’arborescence ne croître disproportionnellement élevée et affecter les performances.

Cette classe de modèle est conçue pour être utilisé par [CRBMap](../../atl/reference/crbmap-class.md) et [CRBMultiMap](../../atl/reference/crbmultimap-class.md). La majeure partie des méthodes qui composent ces classes dérivées sont fournis par `CRBTree`.

Pour obtenir une description plus complète de diverses classes de collection et leurs fonctions et les caractéristiques de performances, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcoll.h

##  <a name="cpair_class"></a>  Classe de CRBTree::CPair

Une classe qui contient les éléments clé / valeur.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Notes

Cette classe est utilisée par les méthodes [CRBTree::GetAt](#getat), [CRBTree::GetNext](#getnext), et [CRBTree::GetPrev](#getprev) pour accéder aux éléments de clé et la valeur stockées dans la structure d’arborescence.

Les membres sont les suivantes :

|||
|-|-|
|`m_key`|Le stockage de l’élément clé de membre de données.|
|`m_value`|Le membre de données stocker l’élément de valeur.|

##  <a name="dtor"></a>  CRBTree :: ~ CRBTree

Destructeur.

```
~CRBTree() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées. Appels [CRBTree::RemoveAll](#removeall) pour supprimer tous les éléments.

##  <a name="findfirstkeyafter"></a>  CRBTree::FindFirstKeyAfter

Appelez cette méthode pour trouver la position de l’élément qui utilise la clé disponible suivante.

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Une valeur de clé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la position de l’élément qui utilise la clé disponible suivante. S’il n’existe aucun autre élément, la valeur NULL est retournée.

### <a name="remarks"></a>Notes

Cette méthode rend plus facile à parcourir l’arborescence sans avoir à calculer les valeurs de position au préalable.

##  <a name="getat"></a>  CRBTree::GetAt

Appelez cette méthode pour obtenir l’élément à une position donnée dans l’arborescence.

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Paramètres

*points de vente*<br/>
La valeur de position.

*key*<br/>
La variable qui reçoit la clé.

*valeur*<br/>
La variable qui reçoit la valeur.

### <a name="return-value"></a>Valeur de retour

Les deux premiers formulaires retournent un pointeur vers un [CPair](#cpair_class). La troisième forme obtienne une clé et une valeur pour la position donnée.

### <a name="remarks"></a>Notes

La valeur de position peut être préalablement déterminée par un appel à une méthode comme [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::GetTailPosition](#gettailposition).

Dans les versions debug, un échec d’assertion se produit si *pos* est égal à NULL.

##  <a name="getcount"></a>  CRBTree::GetCount

Appelez cette méthode pour obtenir le nombre d’éléments dans l’arborescence.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments (chaque paire clé/valeur est un élément) stockés dans l’arborescence.

##  <a name="getheadposition"></a>  CRBTree::GetHeadPosition

Appelez cette méthode pour obtenir la valeur de la position de l’élément au début de l’arborescence.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la position de l’élément au début de l’arborescence.

### <a name="remarks"></a>Notes

La valeur retournée par `GetHeadPosition` peut être utilisé avec des méthodes telles que [CRBTree::GetKeyAt](#getkeyat) ou [CRBTree::GetNext](#getnext) à parcourir l’arborescence et récupérer des valeurs.

##  <a name="getkeyat"></a>  CRBTree::GetKeyAt

Appelez cette méthode pour obtenir la clé à partir d’une position donnée dans l’arborescence.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Paramètres

*points de vente*<br/>
La valeur de position.

### <a name="return-value"></a>Valeur de retour

Retourne la clé stockée à la position *pos* dans l’arborescence.

### <a name="remarks"></a>Notes

Si *pos* n’est pas une valeur valide de position, les résultats sont imprévisibles. Dans les versions debug, un échec d’assertion se produit si *pos* est égal à NULL.

##  <a name="getnext"></a>  CRBTree::GetNext

Appelez cette méthode pour obtenir un pointeur vers un élément stocké dans le `CRBTree` de l’objet et avance la position de l’élément suivant.

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>Paramètres

*points de vente*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la prochaine [CPair](#cpair_class) valeur dans l’arborescence.

### <a name="remarks"></a>Notes

Le *pos* position est mis à jour après chaque appel. Si l’élément récupéré est le dernier dans l’arborescence, *pos* est définie sur NULL.

##  <a name="getnextassoc"></a>  CRBTree::GetNextAssoc

Appelez cette méthode pour obtenir la clé et la valeur d’un élément stocké dans la classe map et avance la position de l’élément suivant.

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Paramètres

*points de vente*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

*key*<br/>
Paramètre de modèle qui spécifie le type de clé de l’arborescence.

*valeur*<br/>
Paramètre de modèle qui spécifie le type de valeur de l’arborescence.

### <a name="remarks"></a>Notes

Le *pos* position est mis à jour après chaque appel. Si l’élément récupéré est le dernier dans l’arborescence, *pos* est définie sur NULL.

##  <a name="getnextkey"></a>  CRBTree::GetNextKey

Appelez cette méthode pour obtenir la clé d’un élément stocké dans l’arborescence et avance la position de l’élément suivant.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*points de vente*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la clé suivante dans l’arborescence.

### <a name="remarks"></a>Notes

Met à jour le compteur de position actuelle, *pos*. S’il n’y a aucune entrée dans l’arborescence, le compteur de position est défini sur NULL.

##  <a name="getnextvalue"></a>  CRBTree::GetNextValue

Appelez cette méthode pour obtenir la valeur d’un élément stocké dans l’arborescence et avance la position de l’élément suivant.

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>Paramètres

*points de vente*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la valeur suivante dans l’arborescence.

### <a name="remarks"></a>Notes

Met à jour le compteur de position actuelle, *pos*. S’il n’y a aucune entrée dans l’arborescence, le compteur de position est défini sur NULL.

##  <a name="getprev"></a>  CRBTree::GetPrev

Appelez cette méthode pour obtenir un pointeur vers un élément stocké dans le `CRBTree` de l’objet, puis mettez à jour la position de l’élément précédent.

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>Paramètres

*points de vente*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la précédente [CPair](#cpair_class) valeur stockée dans l’arborescence.

### <a name="remarks"></a>Notes

Met à jour le compteur de position actuelle, *pos*. S’il n’y a aucune entrée dans l’arborescence, le compteur de position est défini sur NULL.

##  <a name="gettailposition"></a>  CRBTree::GetTailPosition

Appelez cette méthode pour obtenir la valeur de la position de l’élément à la fin de l’arborescence.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de la position de l’élément à la fin de l’arborescence.

### <a name="remarks"></a>Notes

La valeur retournée par `GetTailPosition` peut être utilisé avec des méthodes telles que [CRBTree::GetKeyAt](#getkeyat) ou [CRBTree::GetPrev](#getprev) à parcourir l’arborescence et récupérer des valeurs.

##  <a name="getvalueat"></a>  CRBTree::GetValueAt

Appelez cette méthode pour récupérer la valeur stockée à une position donnée dans le `CRBTree` objet.

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>Paramètres

*points de vente*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la valeur stockée à la position donnée dans le `CRBTree` objet.

##  <a name="isempty"></a>  CRBTree::IsEmpty

Appelez cette méthode à tester pour un objet d’arborescence vide.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’arborescence est vide, sinon FALSE.

##  <a name="kinargtype"></a>  CRBTree::KINARGTYPE

Type utilisé lorsqu’une touche est passée comme argument d’entrée.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

##  <a name="koutargtype"></a>  CRBTree::KOUTARGTYPE

Type utilisé pour une clé est retournée comme un argument de sortie.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

##  <a name="removeall"></a>  CRBTree::RemoveAll

Appelez cette méthode pour supprimer tous les éléments à partir de la `CRBTree` objet.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Notes

Efface le `CRBTree` objet, la mémoire utilisée pour stocker les éléments.

##  <a name="removeat"></a>  CRBTree::RemoveAt

Appelez cette méthode pour supprimer l’élément à la position donnée dans le `CRBTree` objet.

```
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Paramètres

*points de vente*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

### <a name="remarks"></a>Notes

Supprime la paire clé/valeur stockée à la position spécifiée. La mémoire utilisée pour stocker l’élément est libérée. La POSITION référencée par *pos* devient non valide et pendant que la POSITION de tous les autres éléments dans l’arborescence de la validité, ils ne font pas nécessairement conserver le même ordre.

##  <a name="setvalueat"></a>  CRBTree::SetValueAt

Appelez cette méthode pour modifier la valeur stockée à une position donnée dans le `CRBTree` objet.

```
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>Paramètres

*points de vente*<br/>
Le compteur de position, retourné par un appel précédent à des méthodes telles que [CRBTree::GetHeadPosition](#getheadposition) ou [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).

*valeur*<br/>
La valeur à ajouter à la `CRBTree` objet.

### <a name="remarks"></a>Notes

Modifie l’élément de la valeur stockée à la position donnée dans le `CRBTree` objet.

##  <a name="vinargtype"></a>  CRBTree::VINARGTYPE

Type utilisé lorsqu’une valeur est passée comme argument d’entrée.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

##  <a name="voutargtype"></a>  CRBTree::VOUTARGTYPE

Type utilisé lorsqu’une valeur est passée comme un argument de sortie.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
