---
description: 'En savoir plus sur : espace de noms d’accès concurrentiel (C++ AMP)'
title: Concurrency, espace de noms (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- AMP/Concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
ms.openlocfilehash: 9334634dc3d332b24f067c04f00e82feea5a6001
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342580"
---
# <a name="concurrency-namespace-c-amp"></a>Concurrency, espace de noms (C++ AMP)

Fournit des classes et des fonctions qui accélèrent l’exécution du code C++ sur le matériel parallèle de données. Pour plus d’informations, consultez [C++ amp vue d’ensemble](../cpp-amp-overview.md)

## <a name="syntax"></a>Syntaxe

```cpp
namespace Concurrency;
```

## <a name="members"></a>Membres

### <a name="namespaces"></a>Espaces de noms

|Nom|Description|
|----------|-----------------|
|[Concurrency::direct3d, espace de noms](concurrency-direct3d-namespace.md)|Fournit des fonctions qui prennent en charge l’interopérabilité D3D. Permet l’utilisation transparente des ressources D3D pour le calcul dans le code AMP et l’utilisation des ressources créées dans AMP dans le code D3D, sans créer de copies intermédiaires redondantes. Vous pouvez utiliser C++ AMP pour accélérer de manière incrémentielle les sections de calcul intensif de vos applications DirectX et utiliser l’API D3D sur les données générées à partir de calculs AMP.|
|[Concurrency::fast_math, espace de noms](concurrency-fast-math-namespace.md)|Les fonctions de l' `fast_math` espace de noms ne sont pas conformes à C99. Seules les versions à simple précision de chaque fonction sont fournies. Ces fonctions utilisent les fonctions intrinsèques DirectX, qui sont plus rapides que les fonctions correspondantes dans l' `precise_math` espace de noms et ne nécessitent pas de prise en charge de la double précision étendue sur l’accélérateur, mais elles sont moins précises. Il existe deux versions de chaque fonction pour la compatibilité au niveau de la source avec le code C99 ; les deux versions prennent et retournent des valeurs à simple précision.|
|[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)|Fournit des types et des fonctions conçus pour la programmation graphique.|
|[Concurrence ::p espace de noms recise_math](concurrency-precise-math-namespace.md)|Les fonctions de l' `precise_math` espace de noms sont conformes à C99. Les versions à simple précision et à double précision de chaque fonction sont incluses. Ces fonctions incluent les fonctions à simple précision, nécessitent une prise en charge étendue de la double précision sur l’accélérateur.|

### <a name="classes"></a>Classes

|Nom|Description|
|----------|-----------------|
|[Classe d’accélérateur](accelerator-class.md)|Représente une abstraction d’un nœud de calcul optimisé pour les DP physiques.|
|[Classe accelerator_view](accelerator-view-class.md)|Représente une abstraction d’appareil virtuel sur une C++ AMP accélérateur parallèle de données.|
|[Classe accelerator_view_removed](accelerator-view-removed-class.md)|Exception levée en cas d’échec d’un appel DirectX sous-jacent en raison du mécanisme de récupération et de la détection du délai d’attente Windows.|
|[Array, classe](array-class.md)|Agrégat de données sur un `accelerator_view` dans le domaine de la grille. Il s’agit d’une collection de variables, une pour chaque élément dans un domaine de grille. Chaque variable contient une valeur qui correspond à un type C++.|
|[Classe array_view](array-view-class.md)|Représente une vue dans les données d’un tableau \<T,N> .|
|[Classe completion_future](completion-future-class.md)|Représente un futur qui correspond à une opération asynchrone C++ AMP.|
|[extent, classe](extent-class.md)|Représente un vecteur de N valeurs entières qui spécifient les limites d’un espace N-dimensionnel dont l’origine est 0. Les valeurs du vecteur de coordonnée sont triées du plus significatif au moins significatif. Par exemple, dans l’espace 3D cartésien, le vecteur d’étendue (7, 5, 3) représente un espace dans lequel la plage z est comprise entre 0 et 7, les plages de coordonnées y comprises entre 0 et 5, et les plages de coordonnées x comprises entre 0 et 3.|
|[Classe d’index](index-class.md)|Définit un point d’index N-dimensionnel.|
|[Classe invalid_compute_domain](invalid-compute-domain-class.md)|Exception levée lorsque le runtime ne peut pas démarrer un noyau à l’aide du domaine de calcul spécifié sur le `parallel_for_each` site d’appel.|
|[Classe out_of_memory](out-of-memory-class.md)|Exception levée en cas d’échec d’une méthode en raison d’un manque de mémoire système ou de périphérique.|
|[Classe runtime_exception](runtime-exception-class.md)|Type de base pour les exceptions dans la bibliothèque de C++ AMP.|
|[Classe tile_barrier](tile-barrier-class.md)|Classe de fonctionnalité qui peut être créée uniquement par le système et passée à une `parallel_for_each` expression lambda en mosaïque dans le cadre du `tiled_index` paramètre. Il fournit une méthode, `wait()` , dont l’objectif est de synchroniser l’exécution des threads qui s’exécutent dans le groupe de threads (vignette).|
|[Classe tiled_extent](tiled-extent-class.md)|Un `tiled_extent` objet est un `extent` objet d’une à trois dimensions qui subdivise l’espace d’étendue en mosaïques unidimensionnelles, à deux dimensions ou en trois dimensions.|
|[Classe tiled_index](tiled-index-class.md)|Fournit un index dans un `tiled_grid` objet. Cette classe possède des propriétés pour accéder à l’élément par rapport à l’origine de la vignette locale et par rapport à l’origine globale.|
|[Classe uninitialized_object](uninitialized-object-class.md)|Exception levée lorsqu’un objet non initialisé est utilisé.|
|[Classe unsupported_feature](unsupported-feature-class.md)|Exception levée lorsqu’une fonctionnalité non prise en charge est utilisée.|

### <a name="enumerations"></a>Énumérations

|Nom|Description|
|----------|-----------------|
|[access_type, énumération](concurrency-namespace-enums-amp.md#access_type)|Spécifie le type d’accès aux données.|
|[Énumération queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)|Spécifie les modes de mise en file d’attente pris en charge sur l’accélérateur.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|--------------|-----------------|
|[opérateur Operator = = (C++ AMP)](concurrency-namespace-operators-amp.md#operator_eq_eq)|Détermine si les structures de données spécifiées sont égales.|
|[Operator ! =, opérateur (C++ AMP)](concurrency-namespace-operators-amp.md#operator_neq)|Détermine si les structures de données spécifiées sont inégales.|
|[Operator +, opérateur (C++ AMP)](concurrency-namespace-operators-amp.md#operator_add)|Calcule la somme au niveau du composant des arguments spécifiés.|
|[operator-, opérateur (C++ AMP)](concurrency-namespace-operators-amp.md#operator-)|Calcule la différence au niveau du composant entre les arguments spécifiés.|
|[Operator *, opérateur (C++ AMP)](concurrency-namespace-operators-amp.md#operator_star)|Calcule le produit au niveau du composant des arguments spécifiés.|
|[opérateur Operator/(C++ AMP)](concurrency-namespace-operators-amp.md#operator_div)|Calcule le quotient au niveau du composant des arguments spécifiés.|
|[Operator%, opérateur (C++ AMP)](concurrency-namespace-operators-amp.md#operator_mod)|Calcule le modulo du premier argument spécifié par le deuxième argument spécifié.|

### <a name="functions"></a>Fonctions

|Nom|Description|
|----------|-----------------|
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les accès à la mémoire aient été effectués.|
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|Réinitialise le runtime C++ AMP.|
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|Surchargé. Si la valeur stockée à l’emplacement spécifié est égale à la première valeur spécifiée, la deuxième valeur spécifiée est stockée au même emplacement qu’une opération atomique.|
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|Surchargé. Définit la valeur stockée à l’emplacement spécifié à la valeur spécifiée comme une opération atomique.|
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|Surchargé. Définit la valeur stockée à l’emplacement spécifié à la somme de cette valeur et une valeur spécifiée comme une opération atomique.|
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|Surchargé. Définit la valeur stockée à l’emplacement spécifié sur l' `and` opération de bits de cette valeur et une valeur spécifiée sous la forme d’une opération atomique.|
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|Surchargé. Décrémente la valeur stockée à l’emplacement spécifié et stocke le résultat au même emplacement qu’une opération atomique.|
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|Surchargé. Incrémente la valeur stockée à l’emplacement spécifié et stocke le résultat au même emplacement qu’une opération atomique.|
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|Surchargé. Définit la valeur stockée à l’emplacement spécifié à la plus grande de cette valeur et une valeur spécifiée comme une opération atomique.|
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|Surchargé. Définit la valeur stockée à l’emplacement spécifié à la valeur la plus petite de cette valeur et une valeur spécifiée sous la forme d’une opération atomique.|
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|Surchargé. Définit la valeur stockée à l’emplacement spécifié sur l' `or` opération de bits de cette valeur et une valeur spécifiée sous la forme d’une opération atomique.|
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|Surchargé. Affecte à la valeur stockée à l’emplacement spécifié la différence entre cette valeur et une valeur spécifiée comme une opération atomique.|
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|Surchargé. Définit la valeur stockée à l’emplacement spécifié sur l' `xor` opération de bits de cette valeur et une valeur spécifiée sous la forme d’une opération atomique.|
|[copy](concurrency-namespace-functions-amp.md#copy)|Copie un objet C++ AMP. Toutes les exigences de transfert de données synchrones sont respectées. Les données ne peuvent pas être copiées lorsque le code exécute du code sur un accélérateur. La forme générale de cette fonction est `copy(src, dest)` .|
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|Copie un objet C++ AMP et retourne [completion_future](completion-future-class.md) qui peut être attendu. Les données ne peuvent pas être copiées lorsque le code s’exécute sur un accélérateur. La forme générale de cette fonction est `copy(src, dest)` .|
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|Abandonne l’exécution d’une fonction qui a la `restrict(amp)` clause de restriction.|
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|Imprime une chaîne mise en forme dans la fenêtre **sortie** de Visual Studio et déclenche une exception [runtime_exception](runtime-exception-class.md) qui a la même chaîne de mise en forme.|
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|Imprime une chaîne mise en forme dans la fenêtre **sortie** de Visual Studio. Elle est appelée à partir d’une fonction qui a la `restrict(amp)` clause de restriction.|
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les accès à la mémoire globale aient été effectués.|
|[parallel_for_each, fonction (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)|Exécute une fonction sur le domaine de calcul.|
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que les accès à la `tile_static` mémoire aient été effectués.|

## <a name="constants"></a>Constantes

|Nom|Description|
|----------|-----------------|
|[HLSL_MAX_NUM_BUFFERS, constante](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|Nombre maximal de mémoires tampons autorisées par DirectX.|
|[Constante MODULENAME_MAX_LENGTH](concurrency-namespace-constants-amp.md#modulename_max_length)|Stocke la longueur maximale du nom du module. Cette valeur doit être la même sur le compilateur et le Runtime.|

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

## <a name="see-also"></a>Voir aussi

[Référence (C++ AMP)](reference-cpp-amp.md)
