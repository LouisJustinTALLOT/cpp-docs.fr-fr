---
title: Concurrency::Direct3D Namespace | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp/Concurrency::direct3d
- amprt/Concurrency::direct3d
- amp_short_vectors/Concurrency::direct3d
- amp_graphics/Concurrency::direct3d
- amp_math/Concurrency::direct3d
dev_langs:
- C++
helpviewer_keywords:
- direct3d namespace
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9516e3f89d393405a5f71af569a50e46e381d579
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687385"
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d, espace de noms
Le `direct3d` espace de noms fournit des fonctions qui prennent en charge l’interopérabilité de D3D. Il permet d’utiliser les ressources D3D transparente pour le calcul dans le code AMP ainsi autoriser l’utilisation de ressources créées dans le code D3D, de gestion du matériel sans créer des copies redondantes intermédiaires. Vous pouvez accélérer les sections intensif du calcul de vos applications DirectX à l’aide de C++ AMP et utilisent l’API de D3D dans les données générées à partir des calculs de l’AMP progressivement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace direct3d;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="classes"></a>Classes  
  
|Nom|Description|  
|----------|-----------------|  
|[scoped_d3d_access_lock, classe](scoped-d3d-access-lock-class.md)|Un wrapper RAII de verrou D3D accès sur un `accelerator_view` objet.|  
  
### <a name="structures"></a>Structures  
  
|Nom|Description|  
|----------|-----------------|  
|[adopt_d3d_access_lock_t, structure](adopt-d3d-access-lock-t-structure.md)|Type de balise pour indiquer le verrou d’accès D3D doit être adoptée plutôt qu’acquis.|  
  
### <a name="functions"></a>Fonctions  
  
|Nom|Description|  
|----------|-----------------|  
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|Retourne la valeur absolue de l’argument|  
|[clamp](concurrency-direct3d-namespace-functions-amp.md#clamp)|Surchargé. Crochets _X à la plage spécifiée de _Min et de _Max|  
|[countbits](concurrency-direct3d-namespace-functions-amp.md#countbits)|Compte le nombre de bits définis dans _X|  
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|Crée un [accelerator_view, classe](accelerator-view-class.md) d’un pointeur vers une interface de périphérique Direct3D|  
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|Acquiert un verrou sur une accelerator_view afin d’exécuter des opérations D3D sur les ressources partagées avec l’accelerator_view en toute sécurité|  
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|Tentative d’acquisition du verrou d’accès de D3D sur un accelerator_view sans se bloquer.|  
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|Déverrouiller l’accès D3D l’accelerator_view donné.|  
|[firstbithigh](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|Obtient l’emplacement du premier bit ensemble dans _X, depuis le bit d’ordre le plus élevé et l’utilisation vers le bas|  
|[firstbitlow](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|Obtient l’emplacement du premier bit ensemble dans _X, commençant par le bit d’ordre le plus bas et d’utilisation vers le haut|  
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|Obtenir l’interface de mémoire tampon D3D sous-jacent d’un tableau.|  
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|Compare deux valeurs de retour de la valeur supérieure.|  
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|Compare deux valeurs de retour de la valeur qui est plus petite.|  
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|Retourne un indicateur booléen qui indique si l’option délai d’attente est désactivée pour l’accelerator_view spécifié.|  
|[mad](concurrency-direct3d-namespace-functions-amp.md#mad)|Surchargé. Effectue une opération de multiplication/ajouter arithmétique sur trois arguments : _X * _Y + _Z|  
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|Créer un tableau à partir d’un pointeur d’interface de mémoire tampon D3D.|  
|[bruit](concurrency-direct3d-namespace-functions-amp.md#noise)|Génère une valeur aléatoire à l’aide de l’algorithme de bruit Perlin|  
|[radians](concurrency-direct3d-namespace-functions-amp.md#radians)|Convertit les _X de degrés en radians|  
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|Calcule un réciproque rapide et approximative de l’argument|  
|[reversebits](concurrency-direct3d-namespace-functions-amp.md#reversebits)|Inverse l’ordre des octets dans _X|  
|[saturate](concurrency-direct3d-namespace-functions-amp.md#saturate)|Crochets _X dans la plage de 0 à 1|  
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|Surchargé. Retourne le signe de l’argument|  
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|Retourne une interpolation Hermite lisse entre 0 et 1, si _X se trouve dans la plage [_Min, _Max].|  
|[step](concurrency-direct3d-namespace-functions-amp.md#step)|Compare deux valeurs de retour de 0 ou 1 selon la valeur est supérieure|  
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|Compare deux valeurs non signées, retournant la valeur supérieure.|  
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|Compare deux valeurs non signées, retournant la valeur qui est plus petite.|  

## <a name="requirements"></a>Spécifications  
 **En-tête :** amp.h  
  
 **Espace de noms :** Concurrency  
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
