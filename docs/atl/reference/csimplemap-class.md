---
title: Classe CSimpleMap
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
ms.openlocfilehash: eed41c2250728d257b6d303e79c3afd36a543dbb
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747641"
---
# <a name="csimplemap-class"></a>Classe CSimpleMap

Cette classe fournit un support pour un tableau de cartographie simple.

## <a name="syntax"></a>Syntaxe

```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>
class CSimpleMap
```

#### <a name="parameters"></a>Paramètres

*TKey*<br/>
Le type d’élément clé.

*TVal (en)*<br/>
Le type d’élément de valeur.

*TEqual (TEqual)*<br/>
Un objet trait, définissant le `T`critère d’égalité pour les éléments de type .

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|Typedef pour le type de valeur.|
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|Typedef pour le type clé.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleMap::CSimpleMap](#csimplemap)|Constructeur.|
|[CSimpleMap: :CSimpleMap](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleMap::Ajouter](#add)|Ajoute une touche et une valeur associée au tableau de la carte.|
|[CSimpleMap::FindKey](#findkey)|Trouve une clé spécifique.|
|[CSimpleMap::FindVal](#findval)|Trouve une valeur spécifique.|
|[CSimpleMap::GetKeyAt](#getkeyat)|Récupère la clé spécifiée.|
|[CSimpleMap::GetSize](#getsize)|Retourne le nombre d’entrées dans le tableau de cartographie.|
|[CSimpleMap::GetValueAt](#getvalueat)|Récupère la valeur spécifiée.|
|[CSimpleMap::Lookup](#lookup)|Retourne la valeur associée à la clé donnée.|
|[CSimpleMap::Supprimer](#remove)|Supprime une touche et une valeur correspondante.|
|[CSimpleMap::RemoveAll](#removeall)|Supprime toutes les touches et toutes les valeurs.|
|[CSimpleMap::RemoveAt](#removeat)|Supprime une clé spécifique et une valeur correspondante.|
|[CSimpleMap::ReverseLookup](#reverselookup)|Retourne la clé associée à la valeur donnée.|
|[CSimpleMap::SetAt](#setat)|Définit la valeur associée à la clé donnée.|
|[CSimpleMap::SetAtIndex](#setatindex)|Définit la clé et la valeur spécifiques.|

## <a name="remarks"></a>Notes

`CSimpleMap`fournit un support pour un tableau `T`de cartographie simple de n’importe quel type donné, la gestion d’un tableau non ordonné d’éléments clés et leurs valeurs associées.

Le `TEqual` paramètre fournit un moyen de définir `T`une fonction d’égalité pour deux éléments de type . En créant une classe similaire à [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md), il est possible de modifier le comportement du test d’égalité pour n’importe quel tableau donné. Par exemple, lorsqu’il s’agit d’un tableau de pointeurs, il peut être utile de définir l’égalité comme en fonction des valeurs de référence des pointeurs. La mise en œuvre par défaut utilise **l’opérateurMD()**.

Les `CSimpleMap` deux et [CSimpleArray](../../atl/reference/csimplearray-class.md) sont fournis pour la compatibilité avec les versions précédentes ATL, et des implémentations de collecte plus complètes et efficaces sont fournis par [CAtlArray](../../atl/reference/catlarray-class.md) et [CAtlMap](../../atl/reference/catlmap-class.md).

Contrairement à d’autres collections de cartes dans ATL et MFC, cette classe est implémentée avec un tableau simple, et les recherches de recherche nécessitent une recherche linéaire. `CAtlMap`doit être utilisé lorsque le tableau contient un grand nombre d’éléments.

## <a name="requirements"></a>Spécifications

**En-tête:** atlsimpcoll.h

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]

## <a name="csimplemapadd"></a><a name="add"></a>CSimpleMap::Ajouter

Ajoute une touche et une valeur associée au tableau de la carte.

```
BOOL Add(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé.

*Val*<br/>
La valeur associée.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si la clé et la valeur ont été ajoutées avec succès, FALSE autrement.

### <a name="remarks"></a>Notes

Chaque paire de clés et de valeur ajoutée provoque la mémoire du tableau de cartographie d’être libérée et réaffectée, afin de s’assurer que les données pour chacun est toujours stockée de manière contigu. C’est-à-dire que le deuxième élément clé suit toujours directement le premier élément clé de la mémoire et ainsi de suite.

## <a name="csimplemap_arrayelementtype"></a><a name="_arrayelementtype"></a>CSimpleMap::_ArrayElementType

Un tapdef pour le type clé.

```
typedef TVal _ArrayElementType;
```

## <a name="csimplemap_arraykeytype"></a><a name="_arraykeytype"></a>CSimpleMap::_ArrayKeyType

Un tapdef pour le type de valeur.

```
typedef TKey _ArrayKeyType;
```

## <a name="csimplemapcsimplemap"></a><a name="csimplemap"></a>CSimpleMap::CSimpleMap

Constructeur.

```
CSimpleMap();
```

### <a name="remarks"></a>Notes

Initialise les membres des données.

## <a name="csimplemapcsimplemap"></a><a name="dtor"></a>CSimpleMap: :CSimpleMap

Destructeur.

```
~CSimpleMap();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="csimplemapfindkey"></a><a name="findkey"></a>CSimpleMap::FindKey

Trouve une clé spécifique.

```
int FindKey(const TKey& key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé à rechercher.

### <a name="return-value"></a>Valeur de retour

Retourne l’index de la clé si elle est trouvée, sinon retourne -1.

## <a name="csimplemapfindval"></a><a name="findval"></a>CSimpleMap::FindVal

Trouve une valeur spécifique.

```
int FindVal(const TVal& val) const;
```

### <a name="parameters"></a>Paramètres

*Val*<br/>
Valeur à rechercher.

### <a name="return-value"></a>Valeur de retour

Retourne l’indice de la valeur s’il est trouvé, sinon les rendements -1.

## <a name="csimplemapgetkeyat"></a><a name="getkeyat"></a>CSimpleMap::GetKeyAt

Récupère la clé à l’index spécifié.

```
TKey& GetKeyAt(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de la clé à retourner.

### <a name="return-value"></a>Valeur de retour

Retourne la clé référencée par *nIndex*.

### <a name="remarks"></a>Notes

L’indice passé par *nIndex* doit être valide pour que la valeur de rendement soit significative.

## <a name="csimplemapgetsize"></a><a name="getsize"></a>CSimpleMap::GetSize

Retourne le nombre d’entrées dans le tableau de cartographie.

```
int GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’entrées (une clé et la valeur est une entrée) dans le tableau de cartographie.

## <a name="csimplemapgetvalueat"></a><a name="getvalueat"></a>CSimpleMap::GetValueAt

Récupère la valeur à l’index spécifique.

```
TVal& GetValueAt(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’indice de la valeur à revenir.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur référencée par *nIndex*.

### <a name="remarks"></a>Notes

L’indice passé par *nIndex* doit être valide pour que la valeur de rendement soit significative.

## <a name="csimplemaplookup"></a><a name="lookup"></a>CSimpleMap::Lookup

Retourne la valeur associée à la clé donnée.

```
TVal Lookup(const TKey& key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur associée. Si aucune clé correspondante n’est trouvée, NULL est retourné.

## <a name="csimplemapremove"></a><a name="remove"></a>CSimpleMap::Supprimer

Supprime une touche et une valeur correspondante.

```
BOOL Remove(const TKey& key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si la clé, et la valeur correspondante, ont été supprimés avec succès, FALSE autrement.

## <a name="csimplemapremoveall"></a><a name="removeall"></a>CSimpleMap::RemoveAll

Supprime toutes les touches et toutes les valeurs.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Notes

Supprime toutes les touches et les valeurs de l’objet de tableau de cartographie.

## <a name="csimplemapremoveat"></a><a name="removeat"></a>CSimpleMap::RemoveAt

Supprime une clé et la valeur associée à l’index spécifié.

```
BOOL RemoveAt(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index de la clé et la valeur associée à supprimer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI sur le succès, FALSE si l’indice spécifié est un indice invalide.

## <a name="csimplemapreverselookup"></a><a name="reverselookup"></a>CSimpleMap::ReverseLookup

Retourne la clé associée à la valeur donnée.

```
TKey ReverseLookup(const TVal& val) const;
```

### <a name="parameters"></a>Paramètres

*Val*<br/>
Valeur.

### <a name="return-value"></a>Valeur de retour

Retourne la clé associée. Si aucune clé correspondante n’est trouvée, NULL est retourné.

## <a name="csimplemapsetat"></a><a name="setat"></a>CSimpleMap::SetAt

Définit la valeur associée à la clé donnée.

```
BOOL SetAt(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé.

*Val*<br/>
La nouvelle valeur à attribuer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si la clé a été trouvée, et la valeur a été changée avec succès, FALSE autrement.

## <a name="csimplemapsetatindex"></a><a name="setatindex"></a>CSimpleMap::SetAtIndex

Définit la clé et la valeur à un indice spécifié.

```
BOOL SetAtIndex(
    int nIndex,
    const TKey& key,
    const TVal& val);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index, en référence à la clé et l’appariement de valeur pour changer.

*key*<br/>
Nouvelle clé.

*Val*<br/>
Nouvelle valeur.

### <a name="return-value"></a>Valeur de retour

Rendements VRAI en cas de succès, FALSE si l’indice n’était pas valide.

### <a name="remarks"></a>Notes

Mises à jour à la fois la clé et la valeur indiquée par *nIndex*.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
