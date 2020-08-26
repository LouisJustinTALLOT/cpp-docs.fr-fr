---
title: '&lt;facultatif&gt;'
ms.date: 08/06/2019
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.openlocfilehash: 31a3d9aad539e45bb835331a4ef63690d0e16f49
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842674"
---
# <a name="ltoptionalgt"></a>&lt;facultatif&gt;

Définit le modèle de classe `optional` de conteneur et plusieurs modèles de prise en charge.

## <a name="requirements"></a>Configuration requise

**En-tête :**\<optional>

**Espace de noms :** std

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur = =](../standard-library/optional-operators.md#op_eq_eq)|Teste si un objet est égal à un autre objet.|
|[opérateur ! =](../standard-library/optional-operators.md#op_neq)|Teste si un objet n’est pas égal à un autre objet.|
|[<d’opérateur ](../standard-library/optional-operators.md#op_lt)|Teste si l’objet situé à gauche est inférieur à l’objet situé à droite.|
|[<opérateur =](../standard-library/optional-operators.md#op_lt_eq)|Teste si l’objet situé à gauche est inférieur ou égal à l’objet situé à droite.|
|[>d’opérateur ](../standard-library/optional-operators.md#op_gt)|Teste si l’objet situé à gauche est supérieur à l’objet situé à droite.|
|[>opérateur =](../standard-library/optional-operators.md#op_lt_eq)|Teste si l’objet situé à gauche est supérieur ou égal à l’objet situé à droite.|

> [!NOTE]
> Outre les comparaisons relationnelles, \<optional> les opérateurs prennent également en charge la comparaison avec **nullopt** et `T` .

### <a name="functions"></a>Functions

|Nom|Description|
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Rend un objet facultatif.|
|[swap](../standard-library/optional-functions.md#swap)|Échange les valeurs contenues de deux `optional` objets.|

### <a name="classes-and-structs"></a>Classes et structs

|Nom|Description|
|-|-|
|Hachage|Retourne un hachage de l’objet contenu.|
|[optional, classe](../standard-library/optional-class.md)|Décrit un objet qui peut ou non contenir une valeur.|
|[struct nullopt_t](../standard-library/nullopt-t-structure.md)|Décrit un objet qui ne contient pas de valeur.|
|[classe bad_optional_access](../standard-library/bad-optional-access-class.md)|Décrit un objet levé en tant qu’exception pour signaler une tentative d’accès à une valeur absente.|

### <a name="objects"></a>Objets

|Nom|Description|
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)|Instance de `nullopt_t` pour les comparaisons.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
