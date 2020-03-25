---
title: numériques (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/numeric>
- cliext::accumulate
- cliext::adjacent_difference
- cliext::inner_product
- cliext::partial_sum
helpviewer_keywords:
- numeric functions [STL/CLR]
- <cliext/numeric> header [STL/CLR]
- <numeric> header [STL/CLR]
- accumulate function [STL/CLR]
- adjacent_difference function [STL/CLR]
- inner_product function [STL/CLR]
- partial_sum function [STL/CLR]
ms.assetid: 1dc4d9a3-e734-459c-9678-5d9be0ef4c79
ms.openlocfilehash: 1939a6dd9b6d8186eb278623f3b0a5a3d851f4d3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208479"
---
# <a name="numeric-stlclr"></a>numériques (STL/CLR)

Définit les fonctions de modèle de conteneur qui exécutent des algorithmes fournis pour le traitement numérique.

## <a name="syntax"></a>Syntaxe

```
#include <cliext/numeric>
```

## <a name="requirements"></a>Spécifications

**En-tête :** \<cliext/Numeric >

**Espace de noms :** cliext

## <a name="declarations"></a>Déclarations

|Fonction|Description|
|--------------|-----------------|
|[accumulate (STL/CLR)](#accumulate)|Calcule la somme de tous les éléments d’une plage spécifiée incluant une valeur initiale en calculant des sommes partielles successives, ou calcule le résultat des résultats partiels successifs obtenus de la même façon en utilisant une opération binaire spécifiée autre que la somme.|
|[adjacent_difference (STL/CLR)](#adjacent_difference)|Détermine les différences successives entre chaque élément et son prédécesseur au sein d'une plage d'entrée, puis génère les résultats dans une plage de destination ou calcule le résultat d'une procédure généralisée dans laquelle l'opération de différence est remplacée par une autre opération binaire spécifiée.|
|[inner_product (STL/CLR)](#inner_product)|Calcule la somme du produit d’éléments de deux plages et l’ajoute à une valeur initiale spécifiée, ou calcule le résultat d’une procédure généralisée dans laquelle les opérations binaires de somme et de produit sont remplacées par d’autres opérations binaires spécifiées.|
|[partial_sum (STL/CLR)](#partial_sum)|Calcule une série de sommes dans une plage d’entrée à partir du premier élément jusqu’au `i`Th et stocke le résultat de chaque somme dans `i`ième élément d’une plage de destination ou calcule le résultat d’une procédure généralisée où l’opération de somme est remplacée par une autre opération binaire spécifiée.|

## <a name="members"></a>Membres

## <a name="accumulate-stlclr"></a><a name="accumulate"></a>cumul (STL/CLR)

Calcule la somme de tous les éléments d’une plage spécifiée incluant une valeur initiale en calculant des sommes partielles successives, ou calcule le résultat des résultats partiels successifs obtenus de la même façon en utilisant une opération binaire spécifiée autre que la somme.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _Ty> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);
template<class _InIt, class _Ty, class _Fn2> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);
```

### <a name="remarks"></a>Notes

Cette fonction se comporte de la même façon que C++ la fonction numérique standard de la bibliothèque `accumulate`. Pour plus d’informations, consultez [cumul](../standard-library/numeric-functions.md#accumulate).

## <a name="adjacent_difference-stlclr"></a><a name="adjacent_difference"></a>adjacent_difference (STL/CLR)

Détermine les différences successives entre chaque élément et son prédécesseur au sein d'une plage d'entrée, puis génère les résultats dans une plage de destination ou calcule le résultat d'une procédure généralisée dans laquelle l'opération de différence est remplacée par une autre opération binaire spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,
        _OutIt _Dest);
template<class _InIt, class _OutIt, class _Fn2> inline
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Notes

Cette fonction se comporte de la même façon que C++ la fonction numérique standard de la bibliothèque `adjacent_difference`. Pour plus d’informations, consultez [adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference).

## <a name="inner_product-stlclr"></a><a name="inner_product"></a>inner_product (STL/CLR)

Calcule la somme du produit d’éléments de deux plages et l’ajoute à une valeur initiale spécifiée, ou calcule le résultat d’une procédure généralisée dans laquelle les opérations binaires de somme et de produit sont remplacées par d’autres opérations binaires spécifiées.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt1, class _InIt2, class _Ty> inline
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Ty _Val);
template<class _InIt1, class _InIt2, class _Ty, class _Fn21,
       class _Fn22> inline
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Ty _Val, _Fn21 _Func1, _Fn22 _Func2);
```

### <a name="remarks"></a>Notes

Cette fonction se comporte de la même façon que C++ la fonction numérique standard de la bibliothèque `inner_product`. Pour plus d’informations, consultez [inner_product](../standard-library/numeric-functions.md#inner_product).

## <a name="partial_sum-stlclr"></a><a name="partial_sum"></a>partial_sum (STL/CLR)

Calcule une série de sommes dans une plage d’entrée à partir du premier élément jusqu’au `i`Th et stocke le résultat de chaque somme dans `i`ième élément d’une plage de destination ou calcule le résultat d’une procédure généralisée où l’opération de somme est remplacée par une autre opération binaire spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);
template<class _InIt, class _OutIt, class _Fn2> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Notes

Cette fonction se comporte de la même façon que C++ la fonction numérique standard de la bibliothèque `partial_sum`. Pour plus d’informations, consultez [partial_sum](../standard-library/numeric-functions.md#partial_sum).
