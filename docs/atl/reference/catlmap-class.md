---
title: Classe CAtlMap
ms.date: 11/04/2016
f1_keywords:
- CAtlMap
- ATLCOLL/ATL::CAtlMap
- ATLCOLL/ATL::CAtlMap::KINARGTYPE
- ATLCOLL/ATL::CAtlMap::KOUTARGTYPE
- ATLCOLL/ATL::CAtlMap::VINARGTYPE
- ATLCOLL/ATL::CAtlMap::VOUTARGTYPE
- ATLCOLL/ATL::CPair::m_key
- ATLCOLL/ATL::CPair::m_value
- ATLCOLL/ATL::CAtlMap::CAtlMap
- ATLCOLL/ATL::CAtlMap::AssertValid
- ATLCOLL/ATL::CAtlMap::DisableAutoRehash
- ATLCOLL/ATL::CAtlMap::EnableAutoRehash
- ATLCOLL/ATL::CAtlMap::GetAt
- ATLCOLL/ATL::CAtlMap::GetCount
- ATLCOLL/ATL::CAtlMap::GetHashTableSize
- ATLCOLL/ATL::CAtlMap::GetKeyAt
- ATLCOLL/ATL::CAtlMap::GetNext
- ATLCOLL/ATL::CAtlMap::GetNextAssoc
- ATLCOLL/ATL::CAtlMap::GetNextKey
- ATLCOLL/ATL::CAtlMap::GetNextValue
- ATLCOLL/ATL::CAtlMap::GetStartPosition
- ATLCOLL/ATL::CAtlMap::GetValueAt
- ATLCOLL/ATL::CAtlMap::InitHashTable
- ATLCOLL/ATL::CAtlMap::IsEmpty
- ATLCOLL/ATL::CAtlMap::Lookup
- ATLCOLL/ATL::CAtlMap::Rehash
- ATLCOLL/ATL::CAtlMap::RemoveAll
- ATLCOLL/ATL::CAtlMap::RemoveAtPos
- ATLCOLL/ATL::CAtlMap::RemoveKey
- ATLCOLL/ATL::CAtlMap::SetAt
- ATLCOLL/ATL::CAtlMap::SetOptimalLoad
- ATLCOLL/ATL::CAtlMap::SetValueAt
helpviewer_keywords:
- CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
ms.openlocfilehash: 8a89ca7f7dedcd386abdd41e7487f1b838260c83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321441"
---
# <a name="catlmap-class"></a>Classe CAtlMap

Cette classe fournit des méthodes pour créer et gérer un objet de carte.

## <a name="syntax"></a>Syntaxe

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
```

#### <a name="parameters"></a>Paramètres

*K*<br/>
Le type d’élément clé.

*V*<br/>
Le type d’élément de valeur.

*Les KTraits*<br/>
Le code utilisé pour copier ou déplacer des éléments clés. Voir [CElementTraits Class](../../atl/reference/celementtraits-class.md) pour plus de détails.

*VTraits*<br/>
Le code utilisé pour copier ou déplacer des éléments de valeur.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CAtlMap::KINARGTYPE](#kinargtype)|Type utilisé lorsqu’une clé est adoptée comme argument d’entrée|
|[CAtlMap::KOUTARGTYPE](#koutargtype)|Type utilisé lorsqu’une clé est retournée comme argument de sortie.|
|[CAtlMap::VINARGTYPE](#vinargtype)|Type utilisé lorsqu’une valeur est adoptée comme argument d’entrée.|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|Type utilisé lorsqu’une valeur est adoptée comme argument de sortie.|

### <a name="public-classes"></a>Classes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlMap::Classe CPair](#cpair_class)|Une classe contenant la clé et les éléments de valeur.|

### <a name="cpair-data-members"></a>Membres de CPair Data

|Nom|Description|
|----------|-----------------|
|[CPair::m_key](#m_key)|Le membre des données stockant l’élément clé.|
|[CPair::m_value](#m_value)|Le membre des données stockant l’élément de valeur.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlMap::CAtlMap](#catlmap)|Constructeur.|
|[CAtlMap: :CAtlMap](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlMap::AssertValid](#assertvalid)|Appelez cette méthode pour provoquer `CAtlMap` un ASSERT si le n’est pas valide.|
|[CAtlMap::DIsableAutoRehash](#disableautorehash)|Appelez cette méthode pour désactiver le `CAtlMap` rehashing automatique de l’objet.|
|[CAtlMap::EnableAutoRehash](#enableautorehash)|Appelez cette méthode pour permettre le `CAtlMap` rehashing automatique de l’objet.|
|[CAtlMap::GetAt](#getat)|Appelez cette méthode pour retourner l’élément à une position spécifiée dans la carte.|
|[CAtlMap::GetCount](#getcount)|Appelez cette méthode pour récupérer le nombre d’éléments dans la carte.|
|[CAtlMap::GetHashTableSize](#gethashtablesize)|Appelez cette méthode pour déterminer le nombre de bacs dans le tableau de hachage de la carte.|
|[CAtlMap::GetKeyAt](#getkeyat)|Appelez cette méthode pour récupérer la clé `CAtlMap` stockée à la position donnée dans l’objet.|
|[CAtlMap::GetNext](#getnext)|Appelez cette méthode pour obtenir un pointeur `CAtlMap` sur la paire d’élément suivant stockée dans l’objet.|
|[CAtlMap::GetNextAssoc](#getnextassoc)|Obtient le prochain élément pour itérer.|
|[CAtlMap::GetNextKey](#getnextkey)|Appelez cette méthode pour récupérer `CAtlMap` la touche suivante de l’objet.|
|[CAtlMap::GetNextValue](#getnextvalue)|Appelez cette méthode pour obtenir `CAtlMap` la valeur suivante de l’objet.|
|[CAtlMap::GetStartPosition](#getstartposition)|Appelez cette méthode pour démarrer une itération de carte.|
|[CAtlMap::GetValueAt](#getvalueat)|Appelez cette méthode pour récupérer la valeur `CAtlMap` stockée à une position donnée dans l’objet.|
|[CAtlMap::InitHashTable](#inithashtable)|Appelez cette méthode pour initialiser la table de hachage.|
|[CAtlMap::IsEmpty](#isempty)|Appelez cette méthode pour tester un objet de carte vide.|
|[CAtlMap::Lookup](#lookup)|Appelez cette méthode pour rechercher des `CAtlMap` clés ou des valeurs dans l’objet.|
|[CAtlMap::Rehash](#rehash)|Appelez cette méthode pour `CAtlMap` rehash l’objet.|
|[CAtlMap::RemoveAll](#removeall)|Appelez cette méthode pour supprimer `CAtlMap` tous les éléments de l’objet.|
|[CAtlMap::RemoveAtPos](#removeatpos)|Appelez cette méthode pour supprimer l’élément `CAtlMap` à la position donnée dans l’objet.|
|[CAtlMap::RemoveKey](#removekey)|Appelez cette méthode pour supprimer `CAtlMap` un élément de l’objet, compte tenu de la clé.|
|[CAtlMap::SetAt](#setat)|Appelez cette méthode pour insérer une paire d’éléments dans la carte.|
|[CAtlMap::SetOptimalLoad](#setoptimalload)|Appelez cette méthode pour définir `CAtlMap` la charge optimale de l’objet.|
|[CAtlMap::SetValueAt](#setvalueat)|Appelez cette méthode pour modifier la valeur `CAtlMap` stockée à une position donnée dans l’objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|Remplace ou ajoute un nouvel `CAtlMap`élément à la .|

## <a name="remarks"></a>Notes

`CAtlMap`fournit un soutien pour un tableau de cartographie de n’importe quel type donné, la gestion d’un éventail non ordonné d’éléments clés et leurs valeurs associées. Les éléments (composés d’une clé et d’une valeur) sont stockés à l’aide d’un algorithme de hachage, ce qui permet de stocker et de récupérer efficacement une grande quantité de données.

Les paramètres *KTraits* et *VTraits* sont des classes de traits qui contiennent n’importe quel code supplémentaire nécessaire pour copier ou déplacer des éléments.

Une alternative `CAtlMap` à est proposée par la classe [CRBMap.](../../atl/reference/crbmap-class.md) `CRBMap`stocke également des paires de clés/valeur, mais présente des caractéristiques de performance différentes. Le temps nécessaire pour insérer un élément, rechercher `CRBMap` une clé, ou supprimer une clé d’un objet est de journal de *commande(n)*, où *n* est le nombre d’éléments. Pour `CAtlMap`, toutes ces opérations prennent généralement un temps constant, bien que les pires scénarios pourraient être de l’ordre *n*. Par conséquent, dans `CAtlMap` un cas typique, est plus rapide.

L’autre `CRBMap` différence `CAtlMap` entre et devient apparente lors de l’itération à travers les éléments stockés. Dans `CRBMap`un , les éléments sont visités dans un ordre trié. Dans `CAtlMap`un , les éléments ne sont pas commandés, et aucune commande ne peut être déduite.

Lorsqu’un petit nombre d’éléments doivent être stockés, envisagez plutôt d’utiliser la classe [CSimpleMap.](../../atl/reference/csimplemap-class.md)

Pour plus d’informations, voir [cours de collecte ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlcoll.h

## <a name="catlmapassertvalid"></a><a name="assertvalid"></a>CAtlMap::AssertValid

Appelez cette méthode pour provoquer `CAtlMap` un ASSERT si l’objet n’est pas valide.

```
void AssertValid() const;
```

### <a name="remarks"></a>Notes

Dans les constructions de débog, cette `CAtlMap` méthode provoquera un ASSERT si l’objet n’est pas valide.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapcatlmap"></a><a name="catlmap"></a>CAtlMap::CAtlMap

Constructeur.

```
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```

### <a name="parameters"></a>Paramètres

*nBins (en)*<br/>
Le nombre de bacs fournissant des indications aux éléments stockés. Voir Remarques plus tard dans ce sujet pour une explication des bacs.

*fOptimalLoad (en)*<br/>
Le rapport de charge optimal.

*fLoThreshold*<br/>
Le seuil inférieur pour le ratio de charge.

*fHiThreshold*<br/>
Le seuil supérieur pour le ratio de charge.

*nBlockSize (en)*<br/>
Taille du bloc.

### <a name="remarks"></a>Notes

`CAtlMap`référence à tous ses éléments stockés en créant d’abord un index à l’aide d’un algorithme de hachage sur la clé. Cet index fait référence à un "bin" qui contient un pointeur sur les éléments stockés. Si le bac est déjà utilisé, une liste de personnes liées est créée pour accéder aux éléments suivants. Traverser une liste est plus lent que d’accéder directement à l’élément correct, et donc la structure de la carte doit équilibrer les exigences de stockage par rapport aux performances. Les paramètres par défaut ont été choisis pour donner de bons résultats dans la plupart des cas.

Le rapport de charge est le rapport entre le nombre de bacs et le nombre d’éléments stockés dans l’objet cartographique. Lorsque la structure de la carte est recalculée, la valeur du paramètre *fOptimalLoad* sera utilisée pour calculer le nombre de bacs requis. Cette valeur peut être modifiée à l’aide de la méthode [CAtlMap::SetOptimalLoad.](#setoptimalload)

Le paramètre *fLoThreshold* est la valeur inférieure `CAtlMap` que le rapport de charge peut atteindre avant recalculera la taille optimale de la carte.

Le paramètre *fHiThreshold* est la valeur supérieure `CAtlMap` que le rapport de charge peut atteindre avant que l’objet recalcule la taille optimale de la carte.

Ce processus de recalcul (connu sous le nom de rehashing) est activé par défaut. Si vous voulez désactiver ce processus, peut-être lors de la saisie d’un grand nombre de données à la fois, appelez le [CAtlMap::DisableAutoRehash](#disableautorehash) méthode. Réactivez-le avec la méthode [CAtlMap::EnableAutoRehash.](#enableautorehash)

Le *paramètre nBlockSize* est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est nécessaire. De plus grandes tailles de blocs réduisent les appels aux routines d’allocation de mémoire, mais utilisent plus de ressources.

Avant que toutes les données puissent être stockées, il est nécessaire d’initialiser la table de hachage avec un appel à [CAtlMap::InitHashTable](#inithashtable).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

## <a name="catlmapcatlmap"></a><a name="dtor"></a>CAtlMap: :CAtlMap

Destructeur.

```
~CAtlMap() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="catlmapcpair-class"></a><a name="cpair_class"></a>CAtlMap::Classe CPair

Une classe contenant la clé et les éléments de valeur.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Notes

Cette classe est utilisée par les méthodes [CAtlMap::GetNext](#getnext) et [CAtlMap::Lookup](#lookup) pour accéder à la clé et les éléments de valeur stockés dans la structure de cartographie.

## <a name="catlmapdisableautorehash"></a><a name="disableautorehash"></a>CAtlMap::DIsableAutoRehash

Appelez cette méthode pour désactiver le `CAtlMap` rehashing automatique de l’objet.

```
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>Notes

Lorsque le rehashing automatique est activé (ce qui est par défaut), le nombre de bacs dans le tableau de hachage sera automatiquement recalculé si la valeur de charge (le rapport entre le nombre de bacs au nombre d’éléments stockés dans le tableau) dépasse les valeurs maximales ou minimales spécifiées au moment de la création de la carte.

`DisableAutoRehash`est plus utile quand un grand nombre d’éléments seront ajoutés à la carte à la fois. Au lieu de déclencher le processus de rehashing chaque fois que `DisableAutoRehash`les limites sont dépassées, il est plus efficace d’appeler, ajouter les éléments, et enfin appeler [CAtlMap::EnableAutoRehash](#enableautorehash).

## <a name="catlmapenableautorehash"></a><a name="enableautorehash"></a>CAtlMap::EnableAutoRehash

Appelez cette méthode pour permettre le `CAtlMap` rehashing automatique de l’objet.

```
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>Notes

Lorsque le rehashing automatique est activé (ce qui est par défaut), le nombre de bacs dans le tableau de hachage sera automatiquement recalculé si la valeur de charge (le rapport entre le nombre de bacs au nombre d’éléments stockés dans le tableau) dépasse les valeurs maximales ou minimales spécifiées au moment de la création de la carte.

`EnableAutoRefresh`est le plus souvent utilisé après un appel à [CAtlMap::DisableAutoRehash](#disableautorehash).

## <a name="catlmapgetat"></a><a name="getat"></a>CAtlMap::GetAt

Appelez cette méthode pour retourner l’élément à une position spécifiée dans la carte.

```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

*key*<br/>
Paramètre de modèle spécifiant le type de clé de la carte.

*value*<br/>
Paramètre de modèle spécifiant le type de valeur de la carte.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur à la paire actuelle d’éléments clés/valeurs stockés dans la carte.

### <a name="remarks"></a>Notes

Dans les constructions de débog, une erreur d’affirmation se produira si *pos* est égal à NULL.

## <a name="catlmapgetcount"></a><a name="getcount"></a>CAtlMap::GetCount

Appelez cette méthode pour récupérer le nombre d’éléments dans la carte.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments dans l’objet de la carte. Un seul élément est une paire de clé/valeur.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgethashtablesize"></a><a name="gethashtablesize"></a>CAtlMap::GetHashTableSize

Appelez cette méthode pour déterminer le nombre de bacs dans le tableau de hachage de la carte.

```
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de bacs dans le tableau de hachage. Voir [CAtlMap::CAtlMap](#catlmap) pour une explication.

## <a name="catlmapgetkeyat"></a><a name="getkeyat"></a>CAtlMap::GetKeyAt

Appelez cette méthode pour récupérer la clé `CAtlMap` stockée à la position donnée dans l’objet.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valeur de retour

Renvoie une référence à la clé `CAtlMap` stockée à la position donnée dans l’objet.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgetnext"></a><a name="getnext"></a>CAtlMap::GetNext

Appelez cette méthode pour obtenir un pointeur `CAtlMap` sur la paire d’élément suivant stockée dans l’objet.

```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur à la prochaine paire d’éléments clés/valeurs stockés dans la carte. Le compteur de position *pos* est mis à jour après chaque appel. Si l’élément récupéré est le dernier de la carte, *pos* est réglé sur NULL.

## <a name="catlmapgetnextassoc"></a><a name="getnextassoc"></a>CAtlMap::GetNextAssoc

Obtient le prochain élément pour itérer.

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

*key*<br/>
Paramètre de modèle spécifiant le type de clé de la carte.

*value*<br/>
Paramètre de modèle spécifiant le type de valeur de la carte.

### <a name="remarks"></a>Notes

Le compteur de position *pos* est mis à jour après chaque appel. Si l’élément récupéré est le dernier de la carte, *pos* est réglé sur NULL.

## <a name="catlmapgetnextkey"></a><a name="getnextkey"></a>CAtlMap::GetNextKey

Appelez cette méthode pour récupérer `CAtlMap` la touche suivante de l’objet.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valeur de retour

Renvoie une référence à la prochaine clé de la carte.

### <a name="remarks"></a>Notes

Mises à jour du compteur de position actuel, *pos*. S’il n’y a plus d’entrées dans la carte, le compteur de position est réglé sur NULL.

## <a name="catlmapgetnextvalue"></a><a name="getnextvalue"></a>CAtlMap::GetNextValue

Appelez cette méthode pour obtenir `CAtlMap` la valeur suivante de l’objet.

```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valeur de retour

Renvoie une référence à la valeur suivante de la carte.

### <a name="remarks"></a>Notes

Mises à jour du compteur de position actuel, *pos*. S’il n’y a plus d’entrées dans la carte, le compteur de position est réglé sur NULL.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgetstartposition"></a><a name="getstartposition"></a>CAtlMap::GetStartPosition

Appelez cette méthode pour démarrer une itération de carte.

```
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la position de départ, ou NULL est retourné si la carte est vide.

### <a name="remarks"></a>Notes

Appelez cette méthode pour démarrer une itération de carte en `GetNextAssoc` retournant une valeur POSITION qui peut être transmise à la méthode.

> [!NOTE]
> La séquence d’itération n’est pas prévisible

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapgetvalueat"></a><a name="getvalueat"></a>CAtlMap::GetValueAt

Appelez cette méthode pour récupérer la valeur `CAtlMap` stockée à une position donnée dans l’objet.

```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valeur de retour

Renvoie une référence à la valeur `CAtlMap` stockée à la position donnée de l’objet.

## <a name="catlmapinithashtable"></a><a name="inithashtable"></a>CAtlMap::InitHashTable

Appelez cette méthode pour initialiser la table de hachage.

```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>Paramètres

*nBins (en)*<br/>
Le nombre de bacs utilisés par la table de hachage. Voir [CAtlMap::CAtlMap](#catlmap) pour une explication.

*bAllocNow*<br/>
Une indication de drapeau lorsque la mémoire doit être allouée.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur l’initialisation réussie, FALSE sur l’échec.

### <a name="remarks"></a>Notes

`InitHashTable`doit être appelé avant que tous les éléments soient stockés dans la table de hachage.  Si cette méthode n’est pas appelée explicitement, elle sera appelée automatiquement la `CAtlMap` première fois qu’un élément est ajouté à l’aide du nombre de bacs spécifié par le constructeur.  Dans le cas contraire, la carte sera parasminée à l’aide du nouveau nombre de bacs spécifié par le paramètre *nBins.*

Si le *paramètre bAllocNow* est faux, la mémoire requise par la table de hachage ne sera pas allouée jusqu’à ce qu’elle soit d’abord requise. Cela peut être utile s’il n’est pas certain que la carte sera utilisée.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapisempty"></a><a name="isempty"></a>CAtlMap::IsEmpty

Appelez cette méthode pour tester un objet de carte vide.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si la carte est vide, FALSE autrement.

## <a name="catlmapkinargtype"></a><a name="kinargtype"></a>CAtlMap::KINARGTYPE

Type utilisé lorsqu’une clé est passée comme argument d’entrée.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="catlmapkoutargtype"></a><a name="koutargtype"></a>CAtlMap::KOUTARGTYPE

Type utilisé lorsqu’une clé est retournée comme argument de sortie.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="catlmaplookup"></a><a name="lookup"></a>CAtlMap::Lookup

Appelez cette méthode pour rechercher des `CAtlMap` clés ou des valeurs dans l’objet.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la clé qui identifie l’élément à lever.

*value*<br/>
Variable qui reçoit la valeur recherchée.

### <a name="return-value"></a>Valeur de retour

La première forme de la méthode revient vrai si la clé est trouvée, autrement fausse. Les deuxième et troisième formes renvoient un pointeur à un [CPair](#cpair_class) qui peut être utilisé comme une position pour les appels à [CAtlMap::GetNext](#getnext) et ainsi de suite.

### <a name="remarks"></a>Notes

`Lookup`utilise un algorithme de hachage pour trouver rapidement l’élément de carte contenant une clé qui correspond exactement au paramètre clé donné.

## <a name="catlmapoperator-"></a><a name="operator_at"></a>CAtlMap::opérateur\[\]

Remplace ou ajoute un nouvel `CAtlMap`élément à la .

```
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
La clé de l’élément à ajouter ou à remplacer.

### <a name="return-value"></a>Valeur de retour

Renvoie une référence à la valeur associée à la clé donnée.

### <a name="example"></a>Exemple

Si la clé existe déjà, l’élément est remplacé. Si la clé n’existe pas, un nouvel élément est ajouté. Voir l’exemple pour [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmaprehash"></a><a name="rehash"></a>CAtlMap::Rehash

Appelez cette méthode pour `CAtlMap` rehash l’objet.

```
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>Paramètres

*nBins (en)*<br/>
Le nouveau nombre de bacs à utiliser dans la table de hachage. Voir [CAtlMap::CAtlMap](#catlmap) pour une explication.

### <a name="remarks"></a>Notes

Si *nBins* est `CAtlMap` 0, calcule un nombre raisonnable en fonction du nombre d’éléments dans la carte et du réglage optimal de la charge. Normalement, le processus de rehashing est automatique, mais si [CAtlMap::DisableAutoRehash](#disableautorehash) a été appelé, cette méthode effectuera la resizing nécessaire.

## <a name="catlmapremoveall"></a><a name="removeall"></a>CAtlMap::RemoveAll

Appelez cette méthode pour supprimer `CAtlMap` tous les éléments de l’objet.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Notes

Efface l’objet, `CAtlMap` libérant la mémoire utilisée pour stocker les éléments.

## <a name="catlmapremoveatpos"></a><a name="removeatpos"></a>CAtlMap::RemoveAtPos

Appelez cette méthode pour supprimer l’élément `CAtlMap` à la position donnée dans l’objet.

```
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

### <a name="remarks"></a>Notes

Supprime la paire de clés/valeur stockées à la position spécifiée. La mémoire utilisée pour stocker l’élément est libérée. Le POSITION référencé par *pos* devient invalide, et bien que la POSITION de tout autre élément de la carte reste valide, ils ne conservent pas nécessairement le même ordre.

## <a name="catlmapremovekey"></a><a name="removekey"></a>CAtlMap::RemoveKey

Appelez cette méthode pour supprimer `CAtlMap` un élément de l’objet, compte tenu de la clé.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
La clé correspondant à la paire d’éléments que vous souhaitez supprimer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si la clé est trouvée et enlevée, FALSE sur l’échec.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlMap::CAtlMap](#catlmap).

## <a name="catlmapsetat"></a><a name="setat"></a>CAtlMap::SetAt

Appelez cette méthode pour insérer une paire d’éléments dans la carte.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
La valeur clé à `CAtlMap` ajouter à l’objet.

*value*<br/>
La valeur à `CAtlMap` ajouter à l’objet.

### <a name="return-value"></a>Valeur de retour

Retourne la position de la paire `CAtlMap` d’éléments de clé/valeur dans l’objet.

### <a name="remarks"></a>Notes

`SetAt`remplace un élément existant si une clé correspondante est trouvée. Si la clé n’est pas trouvée, une nouvelle paire de clés/valeur est créée.

## <a name="catlmapsetoptimalload"></a><a name="setoptimalload"></a>CAtlMap::SetOptimalLoad

Appelez cette méthode pour définir `CAtlMap` la charge optimale de l’objet.

```
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>Paramètres

*fOptimalLoad (en)*<br/>
Le rapport de charge optimal.

*fLoThreshold*<br/>
Le seuil inférieur pour le ratio de charge.

*fHiThreshold*<br/>
Le seuil supérieur pour le ratio de charge.

*bRehashNow (en)*<br/>
Indicateur indiquant si la table de hachage doit être recalculée.

### <a name="remarks"></a>Notes

Cette méthode redéfinit la valeur `CAtlMap` de charge optimale pour l’objet. Voir [CAtlMap::CAtlMap](#catlmap) pour une discussion des différents paramètres. Si *bRehashNow* est vrai, et le nombre d’éléments est en dehors des valeurs minimales et maximales, la table de hachage est recalculée.

## <a name="catlmapsetvalueat"></a><a name="setvalueat"></a>CAtlMap::SetValueAt

Appelez cette méthode pour modifier la valeur `CAtlMap` stockée à une position donnée dans l’objet.

```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>Paramètres

*Pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

*value*<br/>
La valeur à `CAtlMap` ajouter à l’objet.

### <a name="remarks"></a>Notes

Modifie l’élément de valeur stocké `CAtlMap` à la position donnée de l’objet.

## <a name="catlmapvinargtype"></a><a name="vinargtype"></a>CAtlMap::VINARGTYPE

Type utilisé lorsqu’une valeur est adoptée comme argument d’entrée.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="catlmapvoutargtype"></a><a name="voutargtype"></a>CAtlMap::VOUTARGTYPE

Type utilisé lorsqu’une valeur est adoptée comme argument de sortie.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="catlmapcpairm_key"></a><a name="m_key"></a>CAtlMap::CPair::m_key

Le membre des données stockant l’élément clé.

```
const K m_key;
```

### <a name="parameters"></a>Paramètres

*K*<br/>
Le type d’élément clé.

## <a name="catlmapcpairm_value"></a><a name="m_value"></a>CAtlMap::CPair::m_value

Le membre des données stockant l’élément de valeur.

```
V  m_value;
```

### <a name="parameters"></a>Paramètres

*V*<br/>
Le type d’élément de valeur.

## <a name="see-also"></a>Voir aussi

[Échantillon de marquee](../../overview/visual-cpp-samples.md)<br/>
[Exemple UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
