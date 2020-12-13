---
description: 'En savoir plus sur : Concurrency :: Graphics, espace de noms'
title: Concurrency::graphics, espace de noms
ms.date: 11/04/2016
f1_keywords:
- AMP_GRAPHICS/Concurrency
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
ms.openlocfilehash: f4ab25a6bc6e7bfd318ea58bb6a7efe403c51a89
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132832"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics, espace de noms

L’espace de noms Graphics fournit des types et des fonctions conçus pour la programmation graphique.

## <a name="syntax"></a>Syntaxe

```cpp
namespace graphics;
```

## <a name="members"></a>Membres

### <a name="namespaces"></a>Espaces de noms

|Nom|Description|
|----------|-----------------|
|[Concurrency :: Graphics ::d espace de noms irect3d](concurrency-graphics-direct3d-namespace.md)|Fournit des fonctions pour l’interopérabilité Direct3D.|

### <a name="typedefs"></a>Typedefs

|Nom|Description|
|----------|-----------------|
|`uint`|Le type d’élément pour [uint_2](uint-2-class.md)classe, la [classe Uint_3](uint-3-class.md)et la [classe uint_4](uint-4-class.md). Colonnes définies comme `typedef unsigned int uint;`.|

### <a name="enumerations"></a>Énumérations

|Nom|Description|
|----------|-----------------|
|[énumération address_mode](concurrency-graphics-namespace-enums.md#address_mode).|Spécifie les modes d’adresse pris en charge pour l’échantillonnage de texture.|
|[filter_mode, énumération](concurrency-graphics-namespace-enums.md#filter_mode)|Spécifie les modes de filtre pris en charge pour l’échantillonnage de texture.|

### <a name="classes"></a>Classes

|Nom|Description|
|----------|-----------------|
|[texture, classe](texture-class.md)|Une texture est un agrégat de données sur un accelerator_view dans le domaine de l’étendue. Il s’agit d’une collection de variables, une pour chaque élément dans un domaine d’étendue. Chaque variable contient une valeur correspondant au type primitif C++ (unsigned int, int, float, double) ou à un type scalaire normal, ou unorm (défini dans Concurrency :: Graphics) ou des types de vecteurs courts éligibles définis dans Concurrency :: Graphics.|
|[Classe writeonly_texture_view](writeonly-texture-view-class.md)|Un writeonly_texture_view fournit un accès WriteOnly à une texture.|
|[Classe double_2](double-2-class.md)|Représente un vecteur abrégé de 2 **`double`** valeurs.|
|[Classe double_3](double-3-class.md)|Représente un vecteur de type short de 3 **`double`** valeurs.|
|[Classe double_4](double-4-class.md)|Représente un vecteur de type short de 4 **`double`** valeurs.|
|[Classe float_2](float-2-class.md)|Représente un vecteur abrégé de 2 **`float`** valeurs.|
|[Classe float_3](float-3-class.md)|Représente un vecteur de type short de 3 **`float`** valeurs.|
|[Classe float_4](float-4-class.md)|Représente un vecteur de type short de 4 **`float`** valeurs.|
|[Classe int_2](int-2-class.md)|Représente un vecteur abrégé de 2 **`int`** valeurs.|
|[Classe int_3](int-3-class.md)|Représente un vecteur de type short de 3 **`int`** valeurs.|
|[Classe int_4](int-4-class.md)|Représente un vecteur de type short de 4 **`int`** valeurs.|
|[Classe norm_2](norm-2-class.md)|Représente un vecteur abrégé de 2 `norm` valeurs.|
|[Classe norm_3](norm-3-class.md)|Représente un vecteur de type short de 3 `norm` valeurs.|
|[Classe norm_4](norm-4-class.md)|Représente un vecteur de type short de 4 `norm` valeurs.|
|[Classe uint_2](uint-2-class.md)|Représente un vecteur abrégé de 2 `uint` valeurs.|
|[Classe uint_3](uint-3-class.md)|Représente un vecteur de type short de 3 `uint` valeurs.|
|[Classe uint_4](uint-4-class.md)|Représente un vecteur de type short de 4 `uint` valeurs.|
|[Classe unorm_2](unorm-2-class.md)|Représente un vecteur abrégé de 2 `unorm` valeurs.|
|[Classe unorm_3](unorm-3-class.md)|Représente un vecteur de type short de 3 `unorm` valeurs.|
|[Classe unorm_4](unorm-4-class.md)|Représente un vecteur de type short de 4 `unorm` valeurs.|
|[sampler, classe](sampler-class.md)|Représente la configuration de l’échantillonneur utilisée pour l’échantillonnage de texture.|
|[short_vector Structure](short-vector-structure.md)|Fournit une implémentation de base d’un vecteur de valeurs Short.|
|[short_vector_traits Structure](short-vector-traits-structure.md)|Fournit la récupération de la longueur et du type d’un vecteur abrégé.|
|[Classe texture_view](texture-view-class.md)|Fournit un accès en lecture et un accès en écriture à une texture.|

### <a name="functions"></a>Fonctions

|Nom|Description|
|----------|-----------------|
|[copy](concurrency-graphics-namespace-functions.md#copy)|Surchargé. Copie le contenu de la texture source dans la mémoire tampon de l’hôte de destination.|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|Surchargé. Copie de façon asynchrone le contenu de la texture source dans la mémoire tampon de l’hôte de destination.|

## <a name="requirements"></a>Spécifications

**En-tête :** amp_graphics. h

**Espace de noms :** Concurrency

## <a name="see-also"></a>Voir aussi

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
