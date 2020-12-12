---
description: 'En savoir plus sur : classe CSimpleMap'
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
ms.openlocfilehash: 66640e3fcd325d59b82a10d98188a6fcd74ca79d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140619"
---
# <a name="csimplemap-class"></a>CSimpleMap, classe

Cette classe fournit la prise en charge d’un tableau de mappage simple.

## <a name="syntax"></a>Syntaxe

```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>
class CSimpleMap
```

#### <a name="parameters"></a>Paramètres

*TKey*<br/>
Type d’élément clé.

*TVal*<br/>
Type d’élément de valeur.

*TEqual*<br/>
Objet de trait, définissant le test d’égalité pour les éléments de type `T` .

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleMap :: _ArrayElementType](#_arrayelementtype)|Typedef pour le type valeur.|
|[CSimpleMap :: _ArrayKeyType](#_arraykeytype)|Typedef pour le type de clé.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleMap::CSimpleMap](#csimplemap)|Constructeur.|
|[CSimpleMap :: ~ CSimpleMap](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleMap :: Add](#add)|Ajoute une clé et une valeur associée au tableau de la carte.|
|[CSimpleMap :: FindKey](#findkey)|Recherche une clé spécifique.|
|[CSimpleMap::FindVal](#findval)|Recherche une valeur spécifique.|
|[CSimpleMap::GetKeyAt](#getkeyat)|Récupère la clé spécifiée.|
|[CSimpleMap :: est à obtenir](#getsize)|Retourne le nombre d’entrées dans le tableau de mappage.|
|[CSimpleMap::GetValueAt](#getvalueat)|Récupère la valeur spécifiée.|
|[CSimpleMap :: Lookup](#lookup)|Retourne la valeur associée à la clé donnée.|
|[CSimpleMap :: Remove](#remove)|Supprime une clé et une valeur correspondante.|
|[CSimpleMap :: RemoveAll](#removeall)|Supprime toutes les clés et les valeurs.|
|[CSimpleMap :: RemoveAt](#removeat)|Supprime une clé spécifique et une valeur correspondante.|
|[CSimpleMap::ReverseLookup](#reverselookup)|Retourne la clé associée à la valeur donnée.|
|[CSimpleMap :: SetAt](#setat)|Définit la valeur associée à la clé donnée.|
|[CSimpleMap :: SetAtIndex (](#setatindex)|Définit la clé et la valeur spécifiques.|

## <a name="remarks"></a>Notes

`CSimpleMap` fournit la prise en charge d’un tableau de mappage simple d’un type donné `T` , en gérant un tableau non ordonné d’éléments clés et leurs valeurs associées.

Le paramètre `TEqual` fournit un moyen de définir une fonction d’égalité pour deux éléments de type `T` . En créant une classe similaire à [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md), il est possible de modifier le comportement du test d’égalité pour un tableau donné. Par exemple, lors de la gestion d’un tableau de pointeurs, il peut être utile de définir l’égalité comme en fonction des valeurs référencées par les pointeurs. L’implémentation par défaut utilise **Operator = = ()**.

`CSimpleMap`Et [CSimpleArray](../../atl/reference/csimplearray-class.md) sont fournis pour la compatibilité avec les versions précédentes de ATL, et les implémentations de collection plus complètes et efficaces sont fournies par [CAtlArray](../../atl/reference/catlarray-class.md) et [CAtlMap](../../atl/reference/catlmap-class.md).

Contrairement à d’autres collections de mappages dans ATL et MFC, cette classe est implémentée avec un tableau simple, et les recherches de recherche requièrent une recherche linéaire. `CAtlMap` doit être utilisé lorsque le tableau contient un grand nombre d’éléments.

## <a name="requirements"></a>Spécifications

**En-tête :** atlsimpcoll. h

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]

## <a name="csimplemapadd"></a><a name="add"></a> CSimpleMap :: Add

Ajoute une clé et une valeur associée au tableau de la carte.

```
BOOL Add(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé.

*multiples*<br/>
Valeur associée.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si la clé et la valeur ont été ajoutées avec succès ; sinon, FALSe.

### <a name="remarks"></a>Notes

Chaque paire clé/valeur ajoutée entraîne la libération et la réallocation de la mémoire du tableau de mappage, afin de garantir que les données pour chaque sont toujours stockées de façon contiguë. Autrement dit, le deuxième élément Key suit toujours directement le premier élément Key dans la mémoire, et ainsi de suite.

## <a name="csimplemap_arrayelementtype"></a><a name="_arrayelementtype"></a> CSimpleMap :: _ArrayElementType

Typedef pour le type de clé.

```
typedef TVal _ArrayElementType;
```

## <a name="csimplemap_arraykeytype"></a><a name="_arraykeytype"></a> CSimpleMap :: _ArrayKeyType

Typedef pour le type valeur.

```
typedef TKey _ArrayKeyType;
```

## <a name="csimplemapcsimplemap"></a><a name="csimplemap"></a> CSimpleMap::CSimpleMap

Constructeur.

```
CSimpleMap();
```

### <a name="remarks"></a>Notes

Initialise les données membres.

## <a name="csimplemapcsimplemap"></a><a name="dtor"></a> CSimpleMap :: ~ CSimpleMap

Destructeur.

```
~CSimpleMap();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="csimplemapfindkey"></a><a name="findkey"></a> CSimpleMap :: FindKey

Recherche une clé spécifique.

```
int FindKey(const TKey& key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé à rechercher.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’index de la clé si elle est trouvée ; sinon, retourne-1.

## <a name="csimplemapfindval"></a><a name="findval"></a> CSimpleMap::FindVal

Recherche une valeur spécifique.

```
int FindVal(const TVal& val) const;
```

### <a name="parameters"></a>Paramètres

*multiples*<br/>
Valeur à rechercher.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’index de la valeur s’il est trouvé ; sinon, retourne-1.

## <a name="csimplemapgetkeyat"></a><a name="getkeyat"></a> CSimpleMap::GetKeyAt

Récupère la clé à l’index spécifié.

```
TKey& GetKeyAt(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de la clé à retourner.

### <a name="return-value"></a>Valeur renvoyée

Retourne la clé référencée par *nIndex*.

### <a name="remarks"></a>Notes

L’index passé par *nIndex* doit être valide pour que la valeur de retour soit significative.

## <a name="csimplemapgetsize"></a><a name="getsize"></a> CSimpleMap :: est à obtenir

Retourne le nombre d’entrées dans le tableau de mappage.

```
int GetSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre d’entrées (une clé et une valeur sont une entrée) dans le tableau de mappage.

## <a name="csimplemapgetvalueat"></a><a name="getvalueat"></a> CSimpleMap::GetValueAt

Récupère la valeur au niveau de l’index spécifique.

```
TVal& GetValueAt(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de la valeur à retourner.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur référencée par *nIndex*.

### <a name="remarks"></a>Notes

L’index passé par *nIndex* doit être valide pour que la valeur de retour soit significative.

## <a name="csimplemaplookup"></a><a name="lookup"></a> CSimpleMap :: Lookup

Retourne la valeur associée à la clé donnée.

```
TVal Lookup(const TKey& key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur associée. Si aucune clé correspondante n’est trouvée, la valeur NULL est retournée.

## <a name="csimplemapremove"></a><a name="remove"></a> CSimpleMap :: Remove

Supprime une clé et une valeur correspondante.

```
BOOL Remove(const TKey& key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si la clé et la valeur correspondante ont été supprimées avec succès ; sinon, FALSe.

## <a name="csimplemapremoveall"></a><a name="removeall"></a> CSimpleMap :: RemoveAll

Supprime toutes les clés et les valeurs.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Notes

Supprime toutes les clés et valeurs de l’objet de tableau de mappage.

## <a name="csimplemapremoveat"></a><a name="removeat"></a> CSimpleMap :: RemoveAt

Supprime une clé et une valeur associée à l’index spécifié.

```
BOOL RemoveAt(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de la clé et de la valeur associée à supprimer.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe si l’index spécifié est un index non valide.

## <a name="csimplemapreverselookup"></a><a name="reverselookup"></a> CSimpleMap::ReverseLookup

Retourne la clé associée à la valeur donnée.

```
TKey ReverseLookup(const TVal& val) const;
```

### <a name="parameters"></a>Paramètres

*multiples*<br/>
La valeur.

### <a name="return-value"></a>Valeur renvoyée

Retourne la clé associée. Si aucune clé correspondante n’est trouvée, la valeur NULL est retournée.

## <a name="csimplemapsetat"></a><a name="setat"></a> CSimpleMap :: SetAt

Définit la valeur associée à la clé donnée.

```
BOOL SetAt(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé.

*multiples*<br/>
Nouvelle valeur à assigner.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si la clé a été trouvée et si la valeur a été modifiée avec succès ; sinon, FALSe.

## <a name="csimplemapsetatindex"></a><a name="setatindex"></a> CSimpleMap :: SetAtIndex (

Définit la clé et la valeur à un index spécifié.

```
BOOL SetAtIndex(
    int nIndex,
    const TKey& key,
    const TVal& val);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index référençant la clé et le jumelage de valeurs à modifier.

*key*<br/>
Nouvelle clé.

*multiples*<br/>
Nouvelle valeur.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe si l’index n’est pas valide.

### <a name="remarks"></a>Notes

Met à jour la clé et la valeur vers laquelle pointe *nIndex*.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
