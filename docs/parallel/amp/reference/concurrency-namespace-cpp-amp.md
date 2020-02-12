---
title: Concurrency, espace de noms (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- AMP/Concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
ms.openlocfilehash: 34c3c10fa6bec2737ba78a71c282f90f284a28c2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139369"
---
# <a name="concurrency-namespace-c-amp"></a>Concurrency, espace de noms (C++ AMP)

Fournit des classes et des fonctions qui accélèrent C++ l’exécution du code sur du matériel parallèle aux données. Pour plus d’informations, consultez [ C++ vue d’ensemble du amp](../cpp-amp-overview.md)

## <a name="syntax"></a>Syntaxe

```cpp
namespace Concurrency;
```

## <a name="members"></a>Membres

### <a name="namespaces"></a>Espaces de noms

|Name|Description|
|----------|-----------------|
|[Concurrency::direct3d, espace de noms](concurrency-direct3d-namespace.md)|Fournit des fonctions qui prennent en charge l’interopérabilité D3D. Permet l’utilisation transparente des ressources D3D pour le calcul dans le code AMP et l’utilisation des ressources créées dans AMP dans le code D3D, sans créer de copies intermédiaires redondantes. Vous pouvez utiliser C++ amp pour accélérer de façon incrémentielle les sections de calcul intensif de vos applications DirectX et utiliser l’API D3D sur les données générées à partir de calculs amp.|
|[Concurrency::fast_math, espace de noms](concurrency-fast-math-namespace.md)|Les fonctions de l’espace de noms `fast_math` ne sont pas conformes à C99. Seules les versions à simple précision de chaque fonction sont fournies. Ces fonctions utilisent les fonctions intrinsèques DirectX, qui sont plus rapides que les fonctions correspondantes dans l’espace de noms `precise_math` et ne nécessitent pas de prise en charge de la double précision étendue sur l’accélérateur, mais elles sont moins précises. Il existe deux versions de chaque fonction pour la compatibilité au niveau de la source avec le code C99 ; les deux versions prennent et retournent des valeurs à simple précision.|
|[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)|Fournit des types et des fonctions conçus pour la programmation graphique.|
|[Concurrency::precise_math, espace de noms](concurrency-precise-math-namespace.md)|Les fonctions de l’espace de noms `precise_math` sont conformes à C99. Les versions à simple précision et à double précision de chaque fonction sont incluses. Ces fonctions incluent les fonctions à simple précision, nécessitent une prise en charge étendue de la double précision sur l’accélérateur.|

### <a name="classes"></a>Classes

|Name|Description|
|----------|-----------------|
|[accelerator, classe](accelerator-class.md)|Représente une abstraction d’un nœud de calcul optimisé pour les DP physiques.|
|[accelerator_view, classe](accelerator-view-class.md)|Représente une abstraction d’appareil virtuel sur C++ un accélérateur parallèle de données amp.|
|[accelerator_view_removed, classe](accelerator-view-removed-class.md)|Exception levée en cas d’échec d’un appel DirectX sous-jacent en raison du mécanisme de récupération et de la détection du délai d’attente Windows.|
|[array, classe](array-class.md)|Agrégat de données sur un `accelerator_view` dans le domaine de la grille. Il s’agit d’une collection de variables, une pour chaque élément dans un domaine de grille. Chaque variable contient une valeur qui correspond à un C++ certain type.|
|[array_view, classe](array-view-class.md)|Représente une vue dans les données d’un tableau\<T, N >.|
|[completion_future, classe](completion-future-class.md)|Représente un futur qui correspond à une C++ opération asynchrone amp.|
|[extent, classe](extent-class.md)|Représente un vecteur de N valeurs entières qui spécifient les limites d’un espace N-dimensionnel dont l’origine est 0. Les valeurs du vecteur de coordonnée sont triées du plus significatif au moins significatif. Par exemple, dans l’espace 3D cartésien, le vecteur d’étendue (7, 5, 3) représente un espace dans lequel la plage z est comprise entre 0 et 7, les plages de coordonnées y comprises entre 0 et 5, et les plages de coordonnées x comprises entre 0 et 3.|
|[index, classe](index-class.md)|Définit un point d’index N-dimensionnel.|
|[invalid_compute_domain, classe](invalid-compute-domain-class.md)|Exception levée lorsque le runtime ne peut pas démarrer un noyau à l’aide du domaine de calcul spécifié sur le site d’appel `parallel_for_each`.|
|[out_of_memory (classe)](out-of-memory-class.md)|Exception levée en cas d’échec d’une méthode en raison d’un manque de mémoire système ou de périphérique.|
|[runtime_exception, classe](runtime-exception-class.md)|Type de base pour les exceptions dans C++ la bibliothèque amp.|
|[tile_barrier, classe](tile-barrier-class.md)|Classe de fonctionnalité qui ne peut être créée que par le système et qui est passée à une expression lambda `parallel_for_each` en mosaïque dans le cadre du paramètre `tiled_index`. Il fournit une méthode, `wait()`, dont l’objectif est de synchroniser l’exécution des threads qui s’exécutent dans le groupe de threads (vignette).|
|[tiled_extent, classe](tiled-extent-class.md)|Un objet `tiled_extent` est un objet `extent` d’une à trois dimensions qui subdivise l’espace d’étendue en mosaïques unidimensionnelles, bidimensionnelles ou tridimensionnelles.|
|[tiled_index, classe](tiled-index-class.md)|Fournit un index dans un objet `tiled_grid`. Cette classe possède des propriétés pour accéder à l’élément par rapport à l’origine de la vignette locale et par rapport à l’origine globale.|
|[uninitialized_object, classe](uninitialized-object-class.md)|Exception levée lorsqu’un objet non initialisé est utilisé.|
|[unsupported_feature, classe](unsupported-feature-class.md)|Exception levée lorsqu’une fonctionnalité non prise en charge est utilisée.|

### <a name="enumerations"></a>Énumérations

|Name|Description|
|----------|-----------------|
|[Énumération access_type](concurrency-namespace-enums-amp.md#access_type)|Spécifie le type d’accès aux données.|
|[Énumération queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)|Spécifie les modes de mise en file d’attente pris en charge sur l’accélérateur.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|--------------|-----------------|
|[Operator = =, opérateurC++ (amp)](concurrency-namespace-operators-amp.md#operator_eq_eq)|Détermine si les structures de données spécifiées sont égales.|
|[Operator ! =, opérateurC++ (amp)](concurrency-namespace-operators-amp.md#operator_neq)|Détermine si les structures de données spécifiées sont inégales.|
|[opérateur Operator + (C++ amp)](concurrency-namespace-operators-amp.md#operator_add)|Calcule la somme au niveau du composant des arguments spécifiés.|
|[opérateur-opérateur (C++ amp)](concurrency-namespace-operators-amp.md#operator-)|Calcule la différence au niveau du composant entre les arguments spécifiés.|
|[Operator *, opérateurC++ (amp)](concurrency-namespace-operators-amp.md#operator_star)|Calcule le produit au niveau du composant des arguments spécifiés.|
|[opérateur/opérateur (C++ amp)](concurrency-namespace-operators-amp.md#operator_div)|Calcule le quotient au niveau du composant des arguments spécifiés.|
|[opérateur%, opérateurC++ (amp)](concurrency-namespace-operators-amp.md#operator_mod)|Calcule le modulo du premier argument spécifié par le deuxième argument spécifié.|

### <a name="functions"></a>Fonctions

|Name|Description|
|----------|-----------------|
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les accès à la mémoire aient été effectués.|
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|Réinitialise le C++ Runtime amp.|
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|Surchargé. Si la valeur stockée à l’emplacement spécifié est égale à la première valeur spécifiée, la deuxième valeur spécifiée est stockée au même emplacement qu’une opération atomique.|
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|Surchargé. Définit la valeur stockée à l’emplacement spécifié à la valeur spécifiée comme une opération atomique.|
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|Surchargé. Définit la valeur stockée à l’emplacement spécifié à la somme de cette valeur et une valeur spécifiée comme une opération atomique.|
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|Surchargé. Définit la valeur stockée à l’emplacement spécifié sur la `and` au niveau du bit de cette valeur et une valeur spécifiée comme une opération atomique.|
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|Surchargé. Décrémente la valeur stockée à l’emplacement spécifié et stocke le résultat au même emplacement qu’une opération atomique.|
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|Surchargé. Incrémente la valeur stockée à l’emplacement spécifié et stocke le résultat au même emplacement qu’une opération atomique.|
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|Surchargé. Définit la valeur stockée à l’emplacement spécifié à la plus grande de cette valeur et une valeur spécifiée comme une opération atomique.|
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|Surchargé. Définit la valeur stockée à l’emplacement spécifié à la valeur la plus petite de cette valeur et une valeur spécifiée sous la forme d’une opération atomique.|
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|Surchargé. Définit la valeur stockée à l’emplacement spécifié sur la `or` au niveau du bit de cette valeur et une valeur spécifiée comme une opération atomique.|
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|Surchargé. Affecte à la valeur stockée à l’emplacement spécifié la différence entre cette valeur et une valeur spécifiée comme une opération atomique.|
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|Surchargé. Définit la valeur stockée à l’emplacement spécifié sur la `xor` au niveau du bit de cette valeur et une valeur spécifiée comme une opération atomique.|
|[copy](concurrency-namespace-functions-amp.md#copy)|Copie un C++ objet amp. Toutes les exigences de transfert de données synchrones sont respectées. Les données ne peuvent pas être copiées lorsque le code exécute du code sur un accélérateur. La forme générale de cette fonction est `copy(src, dest)`.|
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|Copie un C++ objet amp et retourne [completion_future](completion-future-class.md) qui peuvent être attendues. Les données ne peuvent pas être copiées lorsque le code s’exécute sur un accélérateur. La forme générale de cette fonction est `copy(src, dest)`.|
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|Abandonne l’exécution d’une fonction qui a la clause de restriction `restrict(amp)`.|
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|Imprime une chaîne mise en forme dans la fenêtre **sortie** de Visual Studio et déclenche une exception [runtime_exception](runtime-exception-class.md) qui a la même chaîne de mise en forme.|
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|Imprime une chaîne mise en forme dans la fenêtre **sortie** de Visual Studio. Elle est appelée à partir d’une fonction qui a la clause de restriction `restrict(amp)`.|
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que tous les accès à la mémoire globale aient été effectués.|
|[Fonction parallel_for_each (C++ amp)](concurrency-namespace-functions-amp.md#parallel_for_each)|Exécute une fonction sur le domaine de calcul.|
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|Bloque l’exécution de tous les threads dans une mosaïque jusqu’à ce que `tile_static` accès à la mémoire soit terminé.|

## <a name="constants"></a>Constantes

|Name|Description|
|----------|-----------------|
|[Constante HLSL_MAX_NUM_BUFFERS](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|Nombre maximal de mémoires tampons autorisées par DirectX.|
|[Constante MODULENAME_MAX_LENGTH](concurrency-namespace-constants-amp.md#modulename_max_length)|Stocke la longueur maximale du nom du module. Cette valeur doit être la même sur le compilateur et le Runtime.|

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

## <a name="see-also"></a>Voir aussi

[Référence (C++ AMP)](reference-cpp-amp.md)
