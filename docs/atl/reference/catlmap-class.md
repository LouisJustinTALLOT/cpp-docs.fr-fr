---
description: 'En savoir plus sur : classe CAtlMap'
title: CAtlMap, classe
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
ms.openlocfilehash: 721f0f3a41afb409ec8cdc505a5f5e5324cdb9bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147249"
---
# <a name="catlmap-class"></a>CAtlMap, classe

Cette classe fournit des méthodes pour créer et gérer un objet Map.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
```

### <a name="parameters"></a>Paramètres

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
|[CAtlMap :: KINARGTYPE](#kinargtype)|Type utilisé quand une clé est passée comme argument d’entrée|
|[CAtlMap :: KOUTARGTYPE](#koutargtype)|Type utilisé quand une clé est retournée en tant qu’argument de sortie.|
|[CAtlMap :: VINARGTYPE](#vinargtype)|Type utilisé quand une valeur est passée comme argument d’entrée.|
|[CAtlMap :: VOUTARGTYPE](#voutargtype)|Type utilisé quand une valeur est passée comme argument de sortie.|

### <a name="public-classes"></a>Classes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlMap :: CPair, classe](#cpair_class)|Classe contenant les éléments de clé et de valeur.|

### <a name="cpair-data-members"></a>Membres de données CPair

|Nom|Description|
|----------|-----------------|
|[CPair :: m_key](#m_key)|Membre de données qui stocke l’élément clé.|
|[CPair :: m_value](#m_value)|Membre de données qui stocke l’élément de valeur.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlMap :: CAtlMap](#catlmap)|Constructeur.|
|[CAtlMap :: ~ CAtlMap](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlMap :: AssertValid](#assertvalid)|Appelez cette méthode pour déclencher une assertion si le `CAtlMap` n’est pas valide.|
|[CAtlMap ::D isableAutoRehash](#disableautorehash)|Appelez cette méthode pour désactiver le rehachage automatique de l' `CAtlMap` objet.|
|[CAtlMap :: EnableAutoRehash](#enableautorehash)|Appelez cette méthode pour activer le rehachage automatique de l' `CAtlMap` objet.|
|[CAtlMap :: GetAt](#getat)|Appelez cette méthode pour retourner l’élément à une position spécifiée dans la classe Map.|
|[CAtlMap :: GetCount](#getcount)|Appelez cette méthode pour récupérer le nombre d’éléments dans la classe Map.|
|[CAtlMap :: GetHashTableSize](#gethashtablesize)|Appelez cette méthode pour déterminer le nombre d’emplacements dans la table de hachage de la carte.|
|[CAtlMap :: GetKeyAt](#getkeyat)|Appelez cette méthode pour récupérer la clé stockée à la position donnée dans l' `CAtlMap` objet.|
|[CAtlMap :: GetNext](#getnext)|Appelez cette méthode pour obtenir un pointeur vers la paire d’éléments suivante stockée dans l' `CAtlMap` objet.|
|[CAtlMap :: GetNextAssoc](#getnextassoc)|Obtient l’élément suivant pour l’itération.|
|[CAtlMap :: GetNextKey](#getnextkey)|Appelez cette méthode pour récupérer la clé suivante de l' `CAtlMap` objet.|
|[CAtlMap :: GetNextValue](#getnextvalue)|Appelez cette méthode pour récupérer la valeur suivante de l' `CAtlMap` objet.|
|[CAtlMap :: GetStartPosition](#getstartposition)|Appelez cette méthode pour démarrer une itération de mappage.|
|[CAtlMap :: GetValueAt](#getvalueat)|Appelez cette méthode pour récupérer la valeur stockée à une position donnée dans l' `CAtlMap` objet.|
|[CAtlMap :: InitHashTable](#inithashtable)|Appelez cette méthode pour initialiser la table de hachage.|
|[CAtlMap :: IsEmpty](#isempty)|Appelez cette méthode pour tester un objet Map vide.|
|[CAtlMap :: Lookup](#lookup)|Appelez cette méthode pour rechercher des clés ou des valeurs dans l' `CAtlMap` objet.|
|[CAtlMap :: rehash](#rehash)|Appelez cette méthode pour rehacher l' `CAtlMap` objet.|
|[CAtlMap :: RemoveAll](#removeall)|Appelez cette méthode pour supprimer tous les éléments de l' `CAtlMap` objet.|
|[CAtlMap :: RemoveAtPos](#removeatpos)|Appelez cette méthode pour supprimer l’élément à la position donnée dans l' `CAtlMap` objet.|
|[CAtlMap :: RemoveKey](#removekey)|Appelez cette méthode pour supprimer un élément de l' `CAtlMap` objet, en fonction de la clé.|
|[CAtlMap :: SetAt](#setat)|Appelez cette méthode pour insérer une paire d’éléments dans la classe Map.|
|[CAtlMap :: SetOptimalLoad](#setoptimalload)|Appelez cette méthode pour définir la charge optimale de l' `CAtlMap` objet.|
|[CAtlMap :: SetValueAt](#setvalueat)|Appelez cette méthode pour modifier la valeur stockée à une position donnée dans l' `CAtlMap` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|Remplace ou ajoute un nouvel élément à `CAtlMap` .|

## <a name="remarks"></a>Notes

`CAtlMap` fournit la prise en charge d’un tableau de mappage d’un type donné, en gérant un tableau non ordonné d’éléments clés et leurs valeurs associées. Les éléments (composés d’une clé et d’une valeur) sont stockés à l’aide d’un algorithme de hachage, ce qui permet de stocker et de récupérer efficacement une grande quantité de données.

Les paramètres *KTraits* et *VTraits* sont des classes de caractéristiques qui contiennent tout code supplémentaire nécessaire pour copier ou déplacer des éléments.

Une alternative à `CAtlMap` est offerte par la classe [CRBMap](../../atl/reference/crbmap-class.md) . `CRBMap` stocke également des paires clé/valeur, mais présente des caractéristiques de performances différentes. Le temps nécessaire à l’insertion d’un élément, à la recherche d’une clé ou à la suppression d’une clé d’un `CRBMap` objet est du journal des commandes *(n)*, où *n* est le nombre d’éléments. Pour `CAtlMap` , toutes ces opérations prennent généralement un temps constant, bien que les scénarios les plus défavorables peuvent être de l’ordre *n*. Par conséquent, dans un cas typique, `CAtlMap` est plus rapide.

L’autre différence entre `CRBMap` et `CAtlMap` devient évidente lors de l’itération dans les éléments stockés. Dans un `CRBMap` , les éléments sont visités dans un ordre trié. Dans un `CAtlMap` , les éléments ne sont pas ordonnés et aucun ordre ne peut être déduit.

Quand un petit nombre d’éléments doit être stocké, envisagez d’utiliser la classe [CSimpleMap](../../atl/reference/csimplemap-class.md) à la place.

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="catlmapassertvalid"></a><a name="assertvalid"></a> CAtlMap :: AssertValid

Appelez cette méthode pour déclencher une assertion si l' `CAtlMap` objet n’est pas valide.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Notes

Dans les versions Debug, cette méthode entraîne une assertion si l' `CAtlMap` objet n’est pas valide.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlMap :: CAtlMap](#catlmap).

## <a name="catlmapcatlmap"></a><a name="catlmap"></a> CAtlMap :: CAtlMap

Constructeur.

```cpp
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```

### <a name="parameters"></a>Paramètres

*nBins*<br/>
Nombre d’emplacements fournissant des pointeurs vers les éléments stockés. Consultez les notes plus loin dans cette rubrique pour obtenir une explication des emplacements.

*fOptimalLoad*<br/>
Taux de charge optimal.

*fLoThreshold*<br/>
Seuil inférieur pour le ratio de charge.

*fHiThreshold*<br/>
Seuil supérieur du ratio de charge.

*nBlockSize*<br/>
Taille du bloc.

### <a name="remarks"></a>Notes

`CAtlMap` fait référence à tous ses éléments stockés en créant d’abord un index à l’aide d’un algorithme de hachage sur la clé. Cet index fait référence à un « bin » qui contient un pointeur vers les éléments stockés. Si l’emplacement est déjà utilisé, une liste liée est créée pour accéder aux éléments suivants. Parcourir une liste est plus lent que d’accéder directement à l’élément approprié, de sorte que la structure de la carte doit équilibrer les besoins de stockage par rapport aux performances. Les paramètres par défaut ont été choisis pour obtenir de bons résultats dans la plupart des cas.

Le ratio de charge est le rapport entre le nombre d’emplacements et le nombre d’éléments stockés dans l’objet de carte. Lorsque la structure de la carte est recalculée, la valeur du paramètre *fOptimalLoad* est utilisée pour calculer le nombre d’emplacements requis. Cette valeur peut être modifiée à l’aide de la méthode [CAtlMap :: SetOptimalLoad](#setoptimalload) .

Le paramètre *fLoThreshold* est la valeur inférieure que le ratio de charge peut atteindre avant que `CAtlMap` ne recalcule la taille optimale de la carte.

Le paramètre *fHiThreshold* est la valeur supérieure que le ratio de charge peut atteindre avant que l' `CAtlMap` objet ne recalcule la taille optimale de la carte.

Ce processus de recalcul (appelé rehachage) est activé par défaut. Si vous souhaitez désactiver ce processus, par exemple lors de l’entrée de nombreuses données à la fois, appelez la méthode [CAtlMap ::D isableautorehash](#disableautorehash) . Réactivez-la à l’aide de la méthode [CAtlMap :: EnableAutoRehash](#enableautorehash) .

Le paramètre *nBlockSize* est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Les tailles de bloc plus volumineuses réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources.

Avant de pouvoir stocker des données, il est nécessaire d’initialiser la table de hachage avec un appel à [CAtlMap :: InitHashTable](#inithashtable).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

## <a name="catlmapcatlmap"></a><a name="dtor"></a> CAtlMap :: ~ CAtlMap

Destructeur.

```cpp
~CAtlMap() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="catlmapcpair-class"></a><a name="cpair_class"></a> CAtlMap :: CPair, classe

Classe contenant les éléments de clé et de valeur.

```cpp
class CPair : public __POSITION
```

### <a name="remarks"></a>Notes

Cette classe est utilisée par les méthodes [CAtlMap :: GetNext](#getnext) et [CAtlMap :: Lookup](#lookup) pour accéder aux éléments de clé et de valeur stockés dans la structure de mappage.

## <a name="catlmapdisableautorehash"></a><a name="disableautorehash"></a> CAtlMap ::D isableAutoRehash

Appelez cette méthode pour désactiver le rehachage automatique de l' `CAtlMap` objet.

```cpp
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>Notes

Lorsque le rehachage automatique est activé (ce qui est le cas par défaut), le nombre d’emplacements dans la table de hachage est recalculé automatiquement si la valeur de la charge (le rapport entre le nombre d’emplacements et le nombre d’éléments stockés dans le tableau) est supérieure aux valeurs maximales ou minimales spécifiées au moment de la création de la carte.

`DisableAutoRehash` est particulièrement utile quand un grand nombre d’éléments est ajouté à la carte à la fois. Au lieu de déclencher le processus de rehachage chaque fois que les limites sont dépassées, il est plus efficace d’appeler `DisableAutoRehash` , d’ajouter les éléments et enfin d’appeler [CAtlMap :: EnableAutoRehash](#enableautorehash).

## <a name="catlmapenableautorehash"></a><a name="enableautorehash"></a> CAtlMap :: EnableAutoRehash

Appelez cette méthode pour activer le rehachage automatique de l' `CAtlMap` objet.

```cpp
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>Notes

Lorsque le rehachage automatique est activé (ce qui est le cas par défaut), le nombre d’emplacements dans la table de hachage est recalculé automatiquement si la valeur de la charge (le rapport entre le nombre d’emplacements et le nombre d’éléments stockés dans le tableau) est supérieure aux valeurs maximales ou minimales spécifiées au moment de la création de la carte.

`EnableAutoRefresh` est le plus souvent utilisé après un appel à [CAtlMap ::D isableautorehash](#disableautorehash).

## <a name="catlmapgetat"></a><a name="getat"></a> CAtlMap :: GetAt

Appelez cette méthode pour retourner l’élément à une position spécifiée dans la classe Map.

```cpp
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap :: GetNextAssoc](#getnextassoc) ou [CAtlMap :: GetStartPosition](#getstartposition).

*key*<br/>
Paramètre de modèle qui spécifie le type de la clé de la carte.

*value*<br/>
Paramètre de modèle qui spécifie le type de la valeur de la carte.

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers la paire actuelle d’éléments clé/valeur stockés dans le mappage.

### <a name="remarks"></a>Notes

Dans les versions Debug, une erreur d’assertion se produit si *pos* est égal à null.

## <a name="catlmapgetcount"></a><a name="getcount"></a> CAtlMap :: GetCount

Appelez cette méthode pour récupérer le nombre d’éléments dans la classe Map.

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre d’éléments dans l’objet Map. Un élément unique est une paire clé/valeur.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlMap :: CAtlMap](#catlmap).

## <a name="catlmapgethashtablesize"></a><a name="gethashtablesize"></a> CAtlMap :: GetHashTableSize

Appelez cette méthode pour déterminer le nombre d’emplacements dans la table de hachage de la carte.

```cpp
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre d’emplacements dans la table de hachage. Pour obtenir une explication, consultez [CAtlMap :: CAtlMap](#catlmap) .

## <a name="catlmapgetkeyat"></a><a name="getkeyat"></a> CAtlMap :: GetKeyAt

Appelez cette méthode pour récupérer la clé stockée à la position donnée dans l' `CAtlMap` objet.

```cpp
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap :: GetNextAssoc](#getnextassoc) ou [CAtlMap :: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à la clé stockée à la position donnée dans l' `CAtlMap` objet.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlMap :: CAtlMap](#catlmap).

## <a name="catlmapgetnext"></a><a name="getnext"></a> CAtlMap :: GetNext

Appelez cette méthode pour obtenir un pointeur vers la paire d’éléments suivante stockée dans l' `CAtlMap` objet.

```cpp
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap :: GetNextAssoc](#getnextassoc) ou [CAtlMap :: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers la paire suivante d’éléments clé/valeur stockés dans le mappage. Le compteur de position *pos* est mis à jour après chaque appel. Si l’élément récupéré est le dernier dans le mappage, *pos* a la valeur null.

## <a name="catlmapgetnextassoc"></a><a name="getnextassoc"></a> CAtlMap :: GetNextAssoc

Obtient l’élément suivant pour l’itération.

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap :: GetNextAssoc](#getnextassoc) ou [CAtlMap :: GetStartPosition](#getstartposition).

*key*<br/>
Paramètre de modèle qui spécifie le type de la clé de la carte.

*value*<br/>
Paramètre de modèle qui spécifie le type de la valeur de la carte.

### <a name="remarks"></a>Notes

Le compteur de position *pos* est mis à jour après chaque appel. Si l’élément récupéré est le dernier dans le mappage, *pos* a la valeur null.

## <a name="catlmapgetnextkey"></a><a name="getnextkey"></a> CAtlMap :: GetNextKey

Appelez cette méthode pour récupérer la clé suivante de l' `CAtlMap` objet.

```cpp
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap :: GetNextAssoc](#getnextassoc) ou [CAtlMap :: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à la clé suivante dans le mappage.

### <a name="remarks"></a>Notes

Met à jour le compteur de position actuelle, *pos*. S’il n’y a plus d’entrées dans le mappage, le compteur de position est défini sur NULL.

## <a name="catlmapgetnextvalue"></a><a name="getnextvalue"></a> CAtlMap :: GetNextValue

Appelez cette méthode pour récupérer la valeur suivante de l' `CAtlMap` objet.

```cpp
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap :: GetNextAssoc](#getnextassoc) ou [CAtlMap :: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à la valeur suivante dans la classe Map.

### <a name="remarks"></a>Notes

Met à jour le compteur de position actuelle, *pos*. S’il n’y a plus d’entrées dans le mappage, le compteur de position est défini sur NULL.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlMap :: CAtlMap](#catlmap).

## <a name="catlmapgetstartposition"></a><a name="getstartposition"></a> CAtlMap :: GetStartPosition

Appelez cette méthode pour démarrer une itération de mappage.

```cpp
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la position de début, ou la valeur NULL est retournée si le mappage est vide.

### <a name="remarks"></a>Notes

Appelez cette méthode pour démarrer une itération de mappage en retournant une valeur de POSITION qui peut être passée à la `GetNextAssoc` méthode.

> [!NOTE]
> La séquence d’itération n’est pas prévisible

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlMap :: CAtlMap](#catlmap).

## <a name="catlmapgetvalueat"></a><a name="getvalueat"></a> CAtlMap :: GetValueAt

Appelez cette méthode pour récupérer la valeur stockée à une position donnée dans l' `CAtlMap` objet.

```cpp
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap :: GetNextAssoc](#getnextassoc) ou [CAtlMap :: GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à la valeur stockée à la position donnée dans l' `CAtlMap` objet.

## <a name="catlmapinithashtable"></a><a name="inithashtable"></a> CAtlMap :: InitHashTable

Appelez cette méthode pour initialiser la table de hachage.

```cpp
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>Paramètres

*nBins*<br/>
Nombre d’emplacements utilisés par la table de hachage. Pour obtenir une explication, consultez [CAtlMap :: CAtlMap](#catlmap) .

*bAllocNow*<br/>
Indication d’indicateur lorsque la mémoire doit être allouée.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas d’initialisation réussie, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

`InitHashTable` doit être appelé avant que tous les éléments soient stockés dans la table de hachage.  Si cette méthode n’est pas appelée explicitement, elle est automatiquement appelée la première fois qu’un élément est ajouté à l’aide du nombre d’emplacements spécifié par le `CAtlMap` constructeur.  Dans le cas contraire, le mappage sera initialisé à l’aide du nouveau nombre d’emplacements spécifié par le paramètre *nBins* .

Si le paramètre *bAllocNow* a la valeur false, la mémoire requise par la table de hachage n’est pas allouée tant qu’elle n’est pas requise pour la première fois. Cela peut être utile s’il est incertain si la carte sera utilisée.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlMap :: CAtlMap](#catlmap).

## <a name="catlmapisempty"></a><a name="isempty"></a> CAtlMap :: IsEmpty

Appelez cette méthode pour tester un objet Map vide.

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si le mappage est vide ; sinon, FALSe.

## <a name="catlmapkinargtype"></a><a name="kinargtype"></a> CAtlMap :: KINARGTYPE

Type utilisé quand une clé est passée comme argument d’entrée.

```cpp
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="catlmapkoutargtype"></a><a name="koutargtype"></a> CAtlMap :: KOUTARGTYPE

Type utilisé quand une clé est retournée en tant qu’argument de sortie.

```cpp
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="catlmaplookup"></a><a name="lookup"></a> CAtlMap :: Lookup

Appelez cette méthode pour rechercher des clés ou des valeurs dans l' `CAtlMap` objet.

```cpp
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la clé qui identifie l’élément à rechercher.

*value*<br/>
Variable qui reçoit la valeur recherchée.

### <a name="return-value"></a>Valeur renvoyée

La première forme de la méthode retourne la valeur true si la clé est trouvée ; sinon, false. Les deuxième et troisième formes retournent un pointeur vers un [CPair](#cpair_class) qui peut être utilisé comme position pour les appels à [CAtlMap :: GetNext](#getnext) , et ainsi de suite.

### <a name="remarks"></a>Notes

`Lookup` utilise un algorithme de hachage pour trouver rapidement l’élément cartographique contenant une clé qui correspond exactement au paramètre de clé donné.

## <a name="catlmapoperator-"></a><a name="operator_at"></a> CAtlMap ::, opérateur \[\]

Remplace ou ajoute un nouvel élément à `CAtlMap` .

```cpp
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé de l’élément à ajouter ou remplacer.

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à la valeur associée à la clé donnée.

### <a name="example"></a>Exemple

Si la clé existe déjà, l’élément est remplacé. Si la clé n’existe pas, un nouvel élément est ajouté. Consultez l’exemple de [CAtlMap :: CAtlMap](#catlmap).

## <a name="catlmaprehash"></a><a name="rehash"></a> CAtlMap :: rehash

Appelez cette méthode pour rehacher l' `CAtlMap` objet.

```cpp
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>Paramètres

*nBins*<br/>
Nouveau nombre d’emplacements à utiliser dans la table de hachage. Pour obtenir une explication, consultez [CAtlMap :: CAtlMap](#catlmap) .

### <a name="remarks"></a>Notes

Si *nBins* a la valeur 0, `CAtlMap` calcule un nombre raisonnable en fonction du nombre d’éléments dans le mappage et du paramètre de charge optimal. Normalement, le processus de rehachage est automatique, mais si [CAtlMap ::D isableautorehash](#disableautorehash) a été appelé, cette méthode effectue le redimensionnement nécessaire.

## <a name="catlmapremoveall"></a><a name="removeall"></a> CAtlMap :: RemoveAll

Appelez cette méthode pour supprimer tous les éléments de l' `CAtlMap` objet.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Notes

Efface l' `CAtlMap` objet et libère la mémoire utilisée pour stocker les éléments.

## <a name="catlmapremoveatpos"></a><a name="removeatpos"></a> CAtlMap :: RemoveAtPos

Appelez cette méthode pour supprimer l’élément à la position donnée dans l' `CAtlMap` objet.

```cpp
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap :: GetNextAssoc](#getnextassoc) ou [CAtlMap :: GetStartPosition](#getstartposition).

### <a name="remarks"></a>Notes

Supprime la paire clé/valeur stockée à la position spécifiée. La mémoire utilisée pour stocker l’élément est libérée. La POSITION référencée par *pos* devient non valide et, tandis que la position de tous les autres éléments de la classe Map reste valide, elle ne conserve pas nécessairement le même ordre.

## <a name="catlmapremovekey"></a><a name="removekey"></a> CAtlMap :: RemoveKey

Appelez cette méthode pour supprimer un élément de l' `CAtlMap` objet, en fonction de la clé.

```cpp
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé correspondant à la paire d’éléments que vous souhaitez supprimer.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si la clé est trouvée et supprimée, FALSe en cas d’échec.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlMap :: CAtlMap](#catlmap).

## <a name="catlmapsetat"></a><a name="setat"></a> CAtlMap :: SetAt

Appelez cette méthode pour insérer une paire d’éléments dans la classe Map.

```cpp
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à ajouter à l' `CAtlMap` objet.

*value*<br/>
Valeur à ajouter à l' `CAtlMap` objet.

### <a name="return-value"></a>Valeur renvoyée

Retourne la position de la paire d’éléments clé/valeur dans l' `CAtlMap` objet.

### <a name="remarks"></a>Notes

`SetAt` remplace un élément existant si une clé correspondante est trouvée. Si la clé est introuvable, une nouvelle paire clé/valeur est créée.

## <a name="catlmapsetoptimalload"></a><a name="setoptimalload"></a> CAtlMap :: SetOptimalLoad

Appelez cette méthode pour définir la charge optimale de l' `CAtlMap` objet.

```cpp
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>Paramètres

*fOptimalLoad*<br/>
Taux de charge optimal.

*fLoThreshold*<br/>
Seuil inférieur pour le ratio de charge.

*fHiThreshold*<br/>
Seuil supérieur du ratio de charge.

*bRehashNow*<br/>
Indicateur qui spécifie si la table de hachage doit être recalculée.

### <a name="remarks"></a>Notes

Cette méthode redéfinit la valeur de chargement optimale pour l' `CAtlMap` objet. Consultez [CAtlMap :: CAtlMap](#catlmap) pour une discussion sur les différents paramètres. Si *bRehashNow* a la valeur true et que le nombre d’éléments est en dehors des valeurs minimales et maximales, la table de hachage est recalculée.

## <a name="catlmapsetvalueat"></a><a name="setvalueat"></a> CAtlMap :: SetValueAt

Appelez cette méthode pour modifier la valeur stockée à une position donnée dans l' `CAtlMap` objet.

```cpp
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap :: GetNextAssoc](#getnextassoc) ou [CAtlMap :: GetStartPosition](#getstartposition).

*value*<br/>
Valeur à ajouter à l' `CAtlMap` objet.

### <a name="remarks"></a>Notes

Modifie l’élément de valeur stocké à la position donnée dans l' `CAtlMap` objet.

## <a name="catlmapvinargtype"></a><a name="vinargtype"></a> CAtlMap :: VINARGTYPE

Type utilisé quand une valeur est passée comme argument d’entrée.

```cpp
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="catlmapvoutargtype"></a><a name="voutargtype"></a> CAtlMap :: VOUTARGTYPE

Type utilisé quand une valeur est passée comme argument de sortie.

```cpp
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="catlmapcpairm_key"></a><a name="m_key"></a> CAtlMap :: CPair :: m_key

Membre de données qui stocke l’élément clé.

```cpp
const K m_key;
```

### <a name="parameters"></a>Paramètres

*DK*<br/>
Type d’élément clé.

## <a name="catlmapcpairm_value"></a><a name="m_value"></a> CAtlMap :: CPair :: m_value

Membre de données qui stocke l’élément de valeur.

```cpp
V  m_value;
```

### <a name="parameters"></a>Paramètres

*V*<br/>
Type d’élément de valeur.

## <a name="see-also"></a>Voir aussi

[Exemple de texte défilant](../../overview/visual-cpp-samples.md)<br/>
[Exemple UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
