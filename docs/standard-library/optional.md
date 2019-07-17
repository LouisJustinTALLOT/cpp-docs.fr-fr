---
title: '&lt;optional&gt;'
ms.date: 11/04/2016
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.assetid: 8b4ab09e-1475-434a-b4e0-fdbc07a08b5b
ms.openlocfilehash: c73ad2ad94a5de29bc2c457fdf6ca8b9c783615c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268481"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

Définit la classe de modèle de conteneur facultative et plusieurs modèles de prise en charge.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<facultatif >

**Espace de noms :** std

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator==](../standard-library/optional-operators.md#op_eq_eq)|Teste si l'objet `optional` situé à gauche de l'opérateur est égal à l'objet `optional` situé à droite.|
|[!=, opérateur](../standard-library/optional-operators.md#op_neq)|Teste si l'objet `optional` situé à gauche de l'opérateur n'est pas égal à l'objet `optional` situé à droite.|
|[operator<](../standard-library/optional-operators.md#op_lt)|Teste si l'objet `optional` situé à gauche de l'opérateur est inférieur à l'objet `optional` situé à droite.|
|[operator<=](../standard-library/optional-operators.md#op_lt_eq)|Teste si l'objet `optional` situé à gauche de l'opérateur est inférieur ou égal à l'objet `optional` situé à droite.|
|[operator>](../standard-library/optional-operators.md#op_gt)|Teste si l'objet `optional` situé à gauche de l'opérateur est supérieur à l'objet `optional` situé à droite.|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|Teste si l'objet `optional` situé à gauche de l'opérateur est supérieur ou égal à l'objet `optional` situé à droite.|

> [!NOTE]
> En plus de relationnel compare, \<facultatif > opérateurs prennent également en charge la comparaison avec **nullopt** et `T`.

### <a name="functions"></a>Fonctions

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Rend un objet facultatif.|
|[swap](../standard-library/optional-functions.md#swap)||

### <a name="classes-and-structs"></a>Classes et structs

|||
|-|-|
|[hash]()||
|[Classe facultative](../standard-library/optional-class.md)|Décrit un objet qui peut ou ne peut pas contenir une valeur.|
|[nullopt_t Struct](../standard-library/nullopt-t-structure.md)|Décrit un objet ne pas contenant une valeur.|
|[bad_optional_access, classe](../standard-library/bad-optional-access-class.md)|Décrit un objet levé en tant qu’exception pour signaler une tentative pour accéder à une valeur non il.|

### <a name="objects"></a>Objets

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)||

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
