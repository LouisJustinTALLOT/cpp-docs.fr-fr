---
title: CSimpleMap, classe
ms.date: 11/04/2016
f1_keywords:
- CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayElementType
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayKeyType
- ATLSIMPCOLL/ATL::CSimpleMap::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::Add
- ATLSIMPCOLL/ATL::CSimpleMap::FindKey
- ATLSIMPCOLL/ATL::CSimpleMap::FindVal
- ATLSIMPCOLL/ATL::CSimpleMap::GetKeyAt
- ATLSIMPCOLL/ATL::CSimpleMap::GetSize
- ATLSIMPCOLL/ATL::CSimpleMap::GetValueAt
- ATLSIMPCOLL/ATL::CSimpleMap::Lookup
- ATLSIMPCOLL/ATL::CSimpleMap::Remove
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleMap::ReverseLookup
- ATLSIMPCOLL/ATL::CSimpleMap::SetAt
- ATLSIMPCOLL/ATL::CSimpleMap::SetAtIndex
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
ms.openlocfilehash: afd9f017bb0fb9a95a0ed4fd135dcbd5ea4ddba2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277940"
---
# <a name="csimplemap-class"></a>CSimpleMap, classe

Cette classe prend en charge un tableau de mappage simple.

## <a name="syntax"></a>Syntaxe

```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>
class CSimpleMap
```

#### <a name="parameters"></a>Paramètres

*TKey*<br/>
Le type d’élément clé.

*TVal*<br/>
Le type d’élément de valeur.

*TEqual*<br/>
Un objet de trait, en définissant le test d’égalité pour les éléments de type `T`.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|TypeDef pour le type de valeur.|
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|TypeDef pour le type de clé.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleMap::CSimpleMap](#csimplemap)|Constructeur.|
|[CSimpleMap::~CSimpleMap](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleMap::Add](#add)|Ajoute une clé et la valeur associée dans le tableau de mappage.|
|[CSimpleMap::FindKey](#findkey)|Recherche une clé spécifique.|
|[CSimpleMap::FindVal](#findval)|Recherche une valeur spécifique.|
|[CSimpleMap::GetKeyAt](#getkeyat)|Récupère la clé spécifiée.|
|[CSimpleMap::GetSize](#getsize)|Retourne le nombre d’entrées dans le tableau de mappage.|
|[CSimpleMap::GetValueAt](#getvalueat)|Récupère la valeur spécifiée.|
|[CSimpleMap::Lookup](#lookup)|Retourne la valeur associée à la clé donnée.|
|[CSimpleMap::Remove](#remove)|Supprime une clé et la valeur correspondante.|
|[CSimpleMap::RemoveAll](#removeall)|Supprime toutes les clés et valeurs.|
|[CSimpleMap::RemoveAt](#removeat)|Supprime une clé spécifique et la valeur correspondante.|
|[CSimpleMap::ReverseLookup](#reverselookup)|Retourne la clé associée à la valeur donnée.|
|[CSimpleMap::SetAt](#setat)|Définit la valeur associée à la clé donnée.|
|[CSimpleMap::SetAtIndex](#setatindex)|Définit la clé spécifique et la valeur.|

## <a name="remarks"></a>Notes

`CSimpleMap` Fournit la prise en charge pour un tableau de mappage simple de n’importe quel type de donnée `T`, la gestion d’un tableau non ordonné d’éléments clés et leurs valeurs associées.

Le paramètre `TEqual` fournit un moyen de définir une fonction d’égalité pour les deux éléments de type `T`. En créant une classe similaire à [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md), il est possible de modifier le comportement du test d’égalité pour n’importe quel tableau donné. Par exemple, lorsque vous travaillez avec un tableau de pointeurs, il peut être utile définir l’égalité en tant qu’en fonction des valeurs que les pointeurs de référence. L’implémentation par défaut utilise **Operator == ()**.

Les deux `CSimpleMap` et [CSimpleArray](../../atl/reference/csimplearray-class.md) sont fournies pour la compatibilité avec ATL précédente libère et implémentations de collections plus complète et efficace sont fournies par [CAtlArray](../../atl/reference/catlarray-class.md) et [ CAtlMap](../../atl/reference/catlmap-class.md).

Contrairement à d’autres collections de mappage dans ATL et MFC, cette classe est implémentée avec un simple tableau, et les recherches de recherche nécessitent une recherche linéaire. `CAtlMap` doit être utilisé lorsque le tableau contient un grand nombre d’éléments.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsimpcoll.h

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]

##  <a name="add"></a>  CSimpleMap::Add

Ajoute une clé et la valeur associée dans le tableau de mappage.

```
BOOL Add(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé.

*val*<br/>
La valeur associée.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si la clé et la valeur a été ajouté avec succès, FALSE sinon.

### <a name="remarks"></a>Notes

Chaque paire clé / valeur ajoutée entraîne le mappage mémoire libérée et réalloué, afin de garantir les données pour chaque sont toujours stockées de façon contiguë de tableau. Autrement dit, le deuxième élément clé directement suit toujours le premier élément de clé dans la mémoire et ainsi de suite.

##  <a name="_arrayelementtype"></a>  CSimpleMap::_ArrayElementType

Typedef pour le type de clé.

```
typedef TVal _ArrayElementType;
```

##  <a name="_arraykeytype"></a>  CSimpleMap::_ArrayKeyType

Typedef pour le type de valeur.

```
typedef TKey _ArrayKeyType;
```

##  <a name="csimplemap"></a>  CSimpleMap::CSimpleMap

Constructeur.

```
CSimpleMap();
```

### <a name="remarks"></a>Notes

Initialise les membres de données.

##  <a name="dtor"></a>  CSimpleMap::~CSimpleMap

Destructeur.

```
~CSimpleMap();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

##  <a name="findkey"></a>  CSimpleMap::FindKey

Recherche une clé spécifique.

```
int FindKey(const TKey& key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé à rechercher.

### <a name="return-value"></a>Valeur de retour

Retourne l’index de la clé si trouvée, sinon retourne -1.

##  <a name="findval"></a>  CSimpleMap::FindVal

Recherche une valeur spécifique.

```
int FindVal(const TVal& val) const;
```

### <a name="parameters"></a>Paramètres

*val*<br/>
La valeur à rechercher.

### <a name="return-value"></a>Valeur de retour

Retourne que l’index de la valeur s’il est trouvé, sinon, retourne -1.

##  <a name="getkeyat"></a>  CSimpleMap::GetKeyAt

Récupère la clé à l’index spécifié.

```
TKey& GetKeyAt(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index de la clé à retourner.

### <a name="return-value"></a>Valeur de retour

Retourne la clé référencée par *nIndex*.

### <a name="remarks"></a>Notes

L’index passé *nIndex* doit être valide pour la valeur de retour explicite.

##  <a name="getsize"></a>  CSimpleMap::GetSize

Retourne le nombre d’entrées dans le tableau de mappage.

```
int GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’entrées (une clé et la valeur est une entrée) dans le tableau de mappage.

##  <a name="getvalueat"></a>  CSimpleMap::GetValueAt

Récupère la valeur à l’index spécifique.

```
TVal& GetValueAt(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de la valeur à retourner.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur référencée par *nIndex*.

### <a name="remarks"></a>Notes

L’index passé *nIndex* doit être valide pour la valeur de retour explicite.

##  <a name="lookup"></a>  CSimpleMap::Lookup

Retourne la valeur associée à la clé donnée.

```
TVal Lookup(const TKey& key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur associée. Si aucune clé correspondante n’est trouvé, NULL est retournée.

##  <a name="remove"></a>  CSimpleMap::Remove

Supprime une clé et la valeur correspondante.

```
BOOL Remove(const TKey& key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si la clé et la valeur correspondante, a été supprimé avec succès, FALSE sinon.

##  <a name="removeall"></a>  CSimpleMap::RemoveAll

Supprime toutes les clés et valeurs.

```
void RemoveAll();
```

### <a name="remarks"></a>Notes

Supprime toutes les clés et valeurs de l’objet de tableau de mappage.

##  <a name="removeat"></a>  CSimpleMap::RemoveAt

Supprime une clé et la valeur associée à l’index spécifié.

```
BOOL RemoveAt(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index de la clé et la valeur associée à supprimer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE si l’index spécifié est un index non valide.

##  <a name="reverselookup"></a>  CSimpleMap::ReverseLookup

Retourne la clé associée à la valeur donnée.

```
TKey ReverseLookup(const TVal& val) const;
```

### <a name="parameters"></a>Paramètres

*val*<br/>
La valeur.

### <a name="return-value"></a>Valeur de retour

Retourne la clé associée. Si aucune clé correspondante n’est trouvé, NULL est retournée.

##  <a name="setat"></a>  CSimpleMap::SetAt

Définit la valeur associée à la clé donnée.

```
BOOL SetAt(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé.

*val*<br/>
La nouvelle valeur à affecter.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si la clé a été trouvée, et la valeur a été modifié avec succès.

##  <a name="setatindex"></a>  CSimpleMap::SetAtIndex

Définit la clé et la valeur à l’index spécifié.

```
BOOL SetAtIndex(
    int nIndex,
    const TKey& key,
    const TVal& val);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index, faisant référence à la clé et la valeur jumelage pour modifier.

*key*<br/>
La nouvelle clé.

*val*<br/>
Nouvelle valeur.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si réussi et FALSE si l’index n’est pas valide.

### <a name="remarks"></a>Notes

Met à jour de la clé et la valeur indiquée par *nIndex*.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
