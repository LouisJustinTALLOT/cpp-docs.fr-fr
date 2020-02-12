---
title: Concurrency::graphics, espace de noms
ms.date: 11/04/2016
f1_keywords:
- AMP_GRAPHICS/Concurrency
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
ms.openlocfilehash: c7e3b245c8d9e6ba0c563a63910fadd678523087
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139450"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics, espace de noms

L’espace de noms Graphics fournit des types et des fonctions conçus pour la programmation graphique.

## <a name="syntax"></a>Syntaxe

```cpp
namespace graphics;
```

## <a name="members"></a>Membres

### <a name="namespaces"></a>Espaces de noms

|Name|Description|
|----------|-----------------|
|[Concurrency::graphics::direct3d, espace de noms](concurrency-graphics-direct3d-namespace.md)|Fournit des fonctions pour l’interopérabilité Direct3D.|

### <a name="typedefs"></a>Typedefs

|Name|Description|
|----------|-----------------|
|`uint`|Le type d’élément pour [uint_2](uint-2-class.md)classe, la [classe Uint_3](uint-3-class.md)et la [classe uint_4](uint-4-class.md). Colonnes définies comme `typedef unsigned int uint;`.|

### <a name="enumerations"></a>Énumérations

|Name|Description|
|----------|-----------------|
|[énumération address_mode](concurrency-graphics-namespace-enums.md#address_mode).|Spécifie les modes d’adresse pris en charge pour l’échantillonnage de texture.|
|[Énumération filter_mode](concurrency-graphics-namespace-enums.md#filter_mode)|Spécifie les modes de filtre pris en charge pour l’échantillonnage de texture.|

### <a name="classes"></a>Classes

|Name|Description|
|----------|-----------------|
|[texture, classe](texture-class.md)|Une texture est un agrégat de données sur un accelerator_view dans le domaine de l’étendue. Il s’agit d’une collection de variables, une pour chaque élément dans un domaine d’étendue. Chaque variable contient une valeur correspondant au C++ type primitif (unsigned int, int, float, double) ou à un type scalaire normal, ou unorm (défini dans Concurrency :: Graphics) ou des types de vecteurs courts éligibles définis dans Concurrency :: Graphics.|
|[writeonly_texture_view, classe](writeonly-texture-view-class.md)|Un writeonly_texture_view fournit un accès WriteOnly à une texture.|
|[double_2, classe](double-2-class.md)|Représente un vecteur abrégé de 2 valeurs `double`.|
|[double_3, classe](double-3-class.md)|Représente un vecteur de type short de 3 valeurs de `double`.|
|[double_4, classe](double-4-class.md)|Représente un vecteur de type short de 4 valeurs `double`.|
|[float_2, classe](float-2-class.md)|Représente un vecteur abrégé de 2 valeurs `float`.|
|[float_3, classe](float-3-class.md)|Représente un vecteur de type short de 3 valeurs de `float`.|
|[float_4, classe](float-4-class.md)|Représente un vecteur de type short de 4 valeurs `float`.|
|[int_2, classe](int-2-class.md)|Représente un vecteur abrégé de 2 valeurs `int`.|
|[int_3, classe](int-3-class.md)|Représente un vecteur de type short de 3 valeurs de `int`.|
|[int_4, classe](int-4-class.md)|Représente un vecteur de type short de 4 valeurs `int`.|
|[norm_2, classe](norm-2-class.md)|Représente un vecteur abrégé de 2 valeurs `norm`.|
|[norm_3, classe](norm-3-class.md)|Représente un vecteur de type short de 3 valeurs de `norm`.|
|[norm_4, classe](norm-4-class.md)|Représente un vecteur de type short de 4 valeurs `norm`.|
|[uint_2, classe](uint-2-class.md)|Représente un vecteur abrégé de 2 valeurs `uint`.|
|[uint_3, classe](uint-3-class.md)|Représente un vecteur de type short de 3 valeurs de `uint`.|
|[uint_4, classe](uint-4-class.md)|Représente un vecteur de type short de 4 valeurs `uint`.|
|[unorm_2, classe](unorm-2-class.md)|Représente un vecteur abrégé de 2 valeurs `unorm`.|
|[unorm_3, classe](unorm-3-class.md)|Représente un vecteur de type short de 3 valeurs de `unorm`.|
|[unorm_4, classe](unorm-4-class.md)|Représente un vecteur de type short de 4 valeurs `unorm`.|
|[sampler, classe](sampler-class.md)|Représente la configuration de l’échantillonneur utilisée pour l’échantillonnage de texture.|
|[short_vector, structure](short-vector-structure.md)|Fournit une implémentation de base d’un vecteur de valeurs Short.|
|[short_vector_traits, structure](short-vector-traits-structure.md)|Fournit la récupération de la longueur et du type d’un vecteur abrégé.|
|[texture_view, classe](texture-view-class.md)|Fournit un accès en lecture et un accès en écriture à une texture.|

### <a name="functions"></a>Fonctions

|Name|Description|
|----------|-----------------|
|[copy](concurrency-graphics-namespace-functions.md#copy)|Surchargé. Copie le contenu de la texture source dans la mémoire tampon de l’hôte de destination.|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|Surchargé. Copie de façon asynchrone le contenu de la texture source dans la mémoire tampon de l’hôte de destination.|

## <a name="requirements"></a>Spécifications

**En-tête :** amp_graphics. h

**Espace de noms :** Concurrency

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
