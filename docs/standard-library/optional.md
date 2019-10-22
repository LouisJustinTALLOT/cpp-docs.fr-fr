---
title: '&lt;optional&gt;'
ms.date: 08/06/2019
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.openlocfilehash: bce31811c98d351f3c561b3136d41f7ed23d13e0
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687259"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

Définit le modèle de classe de conteneur `optional` et plusieurs modèles de prise en charge.

## <a name="requirements"></a>spécifications

**En-tête :** \<optional >

**Espace de noms :** std

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator==](../standard-library/optional-operators.md#op_eq_eq)|Teste si un objet est égal à un autre objet.|
|[!=, opérateur](../standard-library/optional-operators.md#op_neq)|Teste si un objet n’est pas égal à un autre objet.|
|[operator<](../standard-library/optional-operators.md#op_lt)|Teste si l’objet situé à gauche est inférieur à l’objet situé à droite.|
|[operator<=](../standard-library/optional-operators.md#op_lt_eq)|Teste si l’objet situé à gauche est inférieur ou égal à l’objet situé à droite.|
|[operator>](../standard-library/optional-operators.md#op_gt)|Teste si l’objet situé à gauche est supérieur à l’objet situé à droite.|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|Teste si l’objet situé à gauche est supérieur ou égal à l’objet situé à droite.|

> [!NOTE]
> Outre les comparaisons relationnelles, les opérateurs \<optional > prennent également en charge la comparaison avec **nullopt** et `T`.

### <a name="functions"></a>Fonctions

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Rend un objet facultatif.|
|[swap](../standard-library/optional-functions.md#swap)|Échange les valeurs contenues de deux objets `optional`.|

### <a name="classes-and-structs"></a>Classes et structs

|||
|-|-|
|hash|Retourne un hachage de l’objet contenu.|
|[classe facultative](../standard-library/optional-class.md)|Décrit un objet qui peut ou non contenir une valeur.|
|[struct nullopt_t](../standard-library/nullopt-t-structure.md)|Décrit un objet qui ne contient pas de valeur.|
|[bad_optional_access, classe](../standard-library/bad-optional-access-class.md)|Décrit un objet levé en tant qu’exception pour signaler une tentative d’accès à une valeur absente.|

### <a name="objects"></a>Objets

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)|Une instance de `nullopt_t` pour les comparaisons.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
