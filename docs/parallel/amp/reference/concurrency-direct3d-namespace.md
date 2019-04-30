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
ms.openlocfilehash: 6afbd7b3a3f4280ad658c1cb9d8802cc3251d0ed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405480"
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d, espace de noms

Le `direct3d` espace de noms fournit des fonctions qui prennent en charge l’interopérabilité D3D. Il permet une utilisation transparente les ressources D3D pour le calcul dans le code AMP ainsi autoriser l’utilisation des ressources créées dans AMP dans le code D3D, sans créer de copies intermédiaires redondantes. Vous pouvez progressivement accélérer les sections intensives de calcul de vos applications DirectX à l’aide de C++ AMP et utiliser l’API D3D sur les données générées par des calculs AMP.

## <a name="syntax"></a>Syntaxe

```
namespace direct3d;
```

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|Nom|Description|
|----------|-----------------|
|[scoped_d3d_access_lock, classe](scoped-d3d-access-lock-class.md)|Wrapper RAII pour un verrou d’accès D3D sur un `accelerator_view` objet.|

### <a name="structures"></a>Structures

|Nom|Description|
|----------|-----------------|
|[adopt_d3d_access_lock_t, structure](adopt-d3d-access-lock-t-structure.md)|Type de balise pour indiquer le verrou d’accès D3D doit être adopté plutôt qu’interrompu.|

### <a name="functions"></a>Fonctions

|Nom|Description|
|----------|-----------------|
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|Retourne la valeur absolue de l’argument|
|[clamp](concurrency-direct3d-namespace-functions-amp.md#clamp)|Surchargé. Fixe _X à la plage _Min et _Max spécifiée|
|[countbits](concurrency-direct3d-namespace-functions-amp.md#countbits)|Compte le nombre de bits dans _X|
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|Crée un [accelerator_view, classe](accelerator-view-class.md) à partir d’un pointeur vers une interface de périphérique Direct3D|
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|Acquiert un verrou sur un accelerator_view pour exécuter sans risque les opérations D3D sur les ressources partagées avec l’accelerator_view|
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|Tenter d’acquérir le verrou d’accès D3D sur un accelerator_view sans blocage.|
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|Libérer le verrou d’accès D3D sur l’accelerator_view donné.|
|[firstbithigh](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|Obtient l’emplacement du premier bit défini dans _X, en commençant à partir de bit d’ordre le plus élevé et l’utilisation vers le bas|
|[firstbitlow](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|Obtient l’emplacement du premier bit défini dans _X, en commençant à partir de bit d’ordre le plus bas et l’utilisation vers le haut|
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|Obtenir l’interface de mémoire tampon D3D sous-jacente d’un tableau.|
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|Compare deux valeurs, en retournant la valeur est supérieure.|
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|Compare deux valeurs, en retournant la valeur est inférieure.|
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|Retourne un indicateur booléen indiquant si le délai d’attente est désactivé pour l’accelerator_view spécifié.|
|[mad](concurrency-direct3d-namespace-functions-amp.md#mad)|Surchargé. Effectue une opération arithmétique multiplication/addition sur trois arguments : _X \* _Y + _Z|
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|Créer un tableau à partir d’un pointeur d’interface de mémoire tampon D3D.|
|[noise](concurrency-direct3d-namespace-functions-amp.md#noise)|Génère une valeur aléatoire à l’aide de l’algorithme de bruit de Perlin|
|[radians](concurrency-direct3d-namespace-functions-amp.md#radians)|Convertit _X de degrés en radians.|
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|Calcule une réciproque rapide et approximative de l’argument|
|[reversebits](concurrency-direct3d-namespace-functions-amp.md#reversebits)|Inverse l’ordre des bits dans _X|
|[saturate](concurrency-direct3d-namespace-functions-amp.md#saturate)|Fixe _X dans la plage de 0 à 1|
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|Surchargé. Retourne le signe de l’argument|
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|Retourne une interpolation Hermite fluide entre 0 et 1, si _X se trouve dans la plage [_Min, _Max].|
|[step](concurrency-direct3d-namespace-functions-amp.md#step)|Compare deux valeurs, retourne 0 ou 1 selon la valeur est supérieure|
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|Compare deux valeurs non signées, retournant la valeur est supérieure.|
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|Compare deux valeurs non signées, retournant la valeur est inférieure.|

## <a name="requirements"></a>Configuration requise

**En-tête :** amp.h

**Espace de noms :** Concurrence

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
