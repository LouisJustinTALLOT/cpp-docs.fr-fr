---
title: Concurrency::direct3d, espace de noms
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::direct3d
- amprt/Concurrency::direct3d
- amp_short_vectors/Concurrency::direct3d
- amp_graphics/Concurrency::direct3d
- amp_math/Concurrency::direct3d
helpviewer_keywords:
- direct3d namespace
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
ms.openlocfilehash: e1374acbd7061afaba372100cf6e69d9d717da8a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127031"
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d, espace de noms

L’espace de noms `direct3d` fournit des fonctions qui prennent en charge l’interopérabilité D3D. Elle vous permet d’utiliser des ressources D3D pour le calcul dans le code AMP. Il permet également l’utilisation des ressources créées dans AMP dans le code D3D, sans créer de copies intermédiaires redondantes. Vous pouvez accélérer de façon incrémentielle les sections de calcul intensif de vos applications DirectX à C++ l’aide de amp et utiliser l’API D3D sur les données générées à partir des calculs amp.

## <a name="syntax"></a>Syntaxe

```cpp
namespace direct3d;
```

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|Name|Description|
|----------|-----------------|
|[scoped_d3d_access_lock, classe](scoped-d3d-access-lock-class.md)|Wrapper RAII pour un verrou d’accès D3D sur un objet `accelerator_view`.|

### <a name="structures"></a>Structures

|Name|Description|
|----------|-----------------|
|[adopt_d3d_access_lock_t, structure](adopt-d3d-access-lock-t-structure.md)|Type de balise indiquant que le verrou d’accès D3D doit être adopté au lieu d’être acquis.|

### <a name="functions"></a>Fonctions

|Name|Description|
|----------|-----------------|
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|Retourne la valeur absolue de l’argument.|
|[bride](concurrency-direct3d-namespace-functions-amp.md#clamp)|Surchargé. Attache _X à la plage de _Min et de _Max spécifiée|
|[countbits](concurrency-direct3d-namespace-functions-amp.md#countbits)|Compte le nombre de bits définis dans _X|
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|Crée une [classe accelerator_view](accelerator-view-class.md) à partir d’un pointeur vers une interface de périphérique Direct3D|
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|Acquiert un verrou sur un accelerator_view pour exécuter en toute sécurité des opérations D3D sur les ressources partagées avec le accelerator_view|
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|Tentative d’acquisition du verrou d’accès D3D sur un accelerator_view sans blocage.|
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|Libère le verrou d’accès D3D sur le accelerator_view donné.|
|[firstbithigh](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|Obtient l’emplacement du premier bit défini dans _X, en commençant par le bit de poids le plus élevé et en travaillant à la baisse|
|[firstbitlow](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|Obtient l’emplacement du premier bit défini dans _X, en commençant par le bit de poids le plus bas et en travaillant vers le haut|
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|Obtient l’interface de mémoire tampon D3D sous-jacente à un tableau.|
|[IMAX](concurrency-direct3d-namespace-functions-amp.md#imax)|Compare deux valeurs, en retournant la valeur supérieure.|
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|Compare deux valeurs, en retournant la valeur la plus petite.|
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|Retourne un indicateur booléen indiquant si le délai d’attente est désactivé pour le accelerator_view spécifié.|
|[Mad](concurrency-direct3d-namespace-functions-amp.md#mad)|Surchargé. Effectue une opération de multiplication/ajout arithmétique sur trois arguments : _X \* _Y + _Z|
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|Créez un tableau à partir d’un pointeur d’interface de mémoire tampon D3D.|
|[bruit](concurrency-direct3d-namespace-functions-amp.md#noise)|Génère une valeur aléatoire à l’aide de l’algorithme de bruit perl|
|[radians](concurrency-direct3d-namespace-functions-amp.md#radians)|Convertit _X de degrés en radians|
|[RCP](concurrency-direct3d-namespace-functions-amp.md#rcp)|Calcule une réciproque rapide et approximative de l’argument.|
|[reversebits](concurrency-direct3d-namespace-functions-amp.md#reversebits)|Inverse l’ordre des bits dans _X|
|[saturer](concurrency-direct3d-namespace-functions-amp.md#saturate)|Attache _X dans la plage comprise entre 0 et 1|
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|Surchargé. Retourne le signe de l’argument.|
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|Retourne une interpolation Smooth Hermite entre 0 et 1, si _X se trouve dans la plage [_Min, _Max].|
|[première](concurrency-direct3d-namespace-functions-amp.md#step)|Compare deux valeurs, en retournant 0 ou 1 en fonction de la valeur la plus élevée|
|[UMAX](concurrency-direct3d-namespace-functions-amp.md#umax)|Compare deux valeurs non signées, en retournant la valeur supérieure.|
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|Compare deux valeurs non signées, en retournant la valeur la plus petite.|

## <a name="requirements"></a>Spécifications

**En-tête :** amp.h

**Espace de noms :** Concurrency

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
