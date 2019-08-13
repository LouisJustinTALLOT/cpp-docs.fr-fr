---
title: '&lt;optional&gt;'
ms.date: 08/06/2019
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.openlocfilehash: f3b4896a3cb4774e46b36480dd9769fa131fc287
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957180"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

Définit la classe de modèle de conteneur `optional` et plusieurs modèles de prise en charge.

## <a name="requirements"></a>Configuration requise

**En-tête:** \<> facultative

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
> Outre les comparaisons relationnelles, \<les opérateurs > facultatifs prennent également en charge la comparaison avec **nullopt** et. `T`

### <a name="functions"></a>Fonctions

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Rend un objet facultatif.|
|[swap](../standard-library/optional-functions.md#swap)|Échange les valeurs contenues de deux `optional` objets.|

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
|[nullopt](../standard-library/optional-functions.md#nullopt)|Instance de `nullopt_t` pour les comparaisons.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
