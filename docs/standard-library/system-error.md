---
title: '&lt;system_error&gt;'
ms.date: 03/15/2019
f1_keywords:
- <system_error>
- system_error
helpviewer_keywords:
- system_error header
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
ms.openlocfilehash: b9ddb3117afe37060b8013be235bdb11a2a031ac
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898855"
---
# <a name="ltsystem_errorgt"></a>&lt;system_error&gt;

Incluez l’en-tête \<system_error > pour définir la `system_error` de la classe d’exception et les modèles associés pour le traitement des erreurs système de bas niveau.

## <a name="requirements"></a>Configuration requise pour

**En-tête :** \<system_error>

**Espace de noms :** std

## <a name="members"></a>Membres

### <a name="objects"></a>Objets du

|||
|-|-|
|[generic_category](../standard-library/system-error-functions.md#generic_category)|Représente la catégorie des erreurs génériques.|
|[is_error_code_enum_v](../standard-library/system-error-functions.md#is_error_code_enum_v)||
|[is_error_condition_enum_v](../standard-library/system-error-functions.md#is_error_condition_enum_v)||
|[system_category](../standard-library/system-error-functions.md#system_category)|Représente la catégorie des erreurs provoquées par des dépassements de capacité du système de bas niveau.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[make_error_code](../standard-library/system-error-functions.md#make_error_code)|Elle crée un objet `error_code`.|
|[make_error_condition](../standard-library/system-error-functions.md#make_error_condition)|Elle crée un objet `error_condition`.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator==](../standard-library/system-error-operators.md#op_eq_eq)|Teste si l’objet situé à gauche de l’opérateur est égal à l’objet situé à droite.|
|[!=, opérateur](../standard-library/system-error-operators.md#op_neq)|Teste si l’objet situé à gauche de l’opérateur n’est pas égal à l’objet situé à droite.|
|[operator<](../standard-library/system-error-operators.md#op_lt)|Vérifie si un objet est inférieur à l'objet passé en vue de leur comparaison.|
|[operator<<](../standard-library/system-error-operators.md#op_ostream)||

### <a name="enums"></a>Énumérations

|||
|-|-|
|[errc](../standard-library/system-error-enums.md#errc)|Fournit des noms symboliques pour toutes les macros de code d’erreur définies par POSIX dans `<errno.h>`.|

### <a name="classes-and-structs"></a>Classes et structs

|||
|-|-|
|[error_category](../standard-library/error-category-class.md)|Représente la base commune abstraite d’objets qui décrit une catégorie des codes d’erreur.|
|[error_code](../standard-library/error-code-class.md)|Représente les erreurs système de bas niveau spécifiques de l’implémentation.|
|[error_condition](../standard-library/error-condition-class.md)|Représente les codes d’erreur définis par l’utilisateur.|
|[hash](../standard-library/hash-structure.md#system_error)||
|[is_error_code_enum](../standard-library/is-error-code-enum-class.md)|Représente un prédicat de type qui teste la présence de l’énumération de [classe error_code](../standard-library/error-code-class.md).|
|[is_error_condition_enum](../standard-library/is-error-condition-enum-class.md)|Représente un prédicat de type qui teste la présence de l’énumération de [classe error_condition](../standard-library/error-condition-class.md).|
|[system_error](../standard-library/system-error-class.md)|Représente la classe de base pour toutes les exceptions levées pour signaler un dépassement de capacité du système de bas niveau.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
