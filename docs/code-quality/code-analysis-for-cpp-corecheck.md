---
description: 'En savoir plus sur : informations de référence sur le vérificateur de C++ Core Guidelines'
title: Référence du vérificateur de C++ Core Guidelines
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
ms.openlocfilehash: 40d0e713d8064a952c785ca44ac5a7ba60f41b61
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151578"
---
# <a name="c-core-guidelines-checker-reference"></a>Référence du vérificateur de C++ Core Guidelines

Cette section répertorie les avertissements du vérificateur d’C++ Core Guidelines. Pour plus d’informations sur l’analyse du code, consultez [ `/analyze` (analyse du code)](../build/reference/analyze-code-analysis.md) et [démarrage rapide : analyse du code pour C/C++](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Certains avertissements appartiennent à plusieurs groupes, et tous les avertissements ne disposent pas d’une rubrique de référence complète.

## <a name="owner_pointer-group"></a>Groupe de OWNER_POINTER

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)\
Retourne un objet de portée à la place d’un segment de mémoire alloué s’il a un constructeur de déplacement. Consultez [C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md)\
Réinitialiser ou supprimer explicitement un \<T> pointeur propriétaire'*variable*'. Consultez [C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md)\
Ne supprimez pas un propriétaire \<T> qui peut être dans un État non valide. Consultez [C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md)\
N’assignez pas à un propriétaire \<T> qui peut être dans un état valide. Consultez [C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md)\
N’assignez pas un pointeur brut à un propriétaire \<T> . Consultez [C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md)\
Préférer les objets délimités, pas de tas-Allocate inutilement. Consultez [C++ Core Guidelines R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md)\
Le symbole'*symbol*'n’est jamais testé pour la valeur null, il peut être marqué comme not_null. Consultez [C++ Core Guidelines F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md)\
Le symbole'*symbol*'n’est pas testé pour vérifier la valeur NULL sur tous les chemins d’accès. Consultez [C++ Core Guidelines F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md)\
Le type de l’expression'*expr*'est déjà GSL :: not_null. Ne Testez pas la valeur null. Consultez [C++ Core Guidelines F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="raw_pointer-group"></a>Groupe de RAW_POINTER

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md)\
N’assignez pas le résultat d’une allocation ou d’un appel de fonction avec une \<T> valeur de retour owner à un pointeur brut ; utilisez à la \<T> place owner. Consultez [C++ Core Guidelines I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md)\
Ne supprimez pas un pointeur brut qui n’est pas un propriétaire \<T> . Consultez [C++ Core Guidelines I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)\
Retourne un objet de portée à la place d’un segment de mémoire alloué s’il a un constructeur de déplacement. Consultez [C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md)\
Évitez malloc () et Free (), préférez la version nothrow de New with Delete. Consultez [C++ Core Guidelines R. 10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md)\
Évitez d’appeler New et Delete explicitement, utilisez std :: make_unique à la \<T> place. Consultez [C++ Core Guidelines R. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md)\
Le symbole'*symbol*'n’est jamais testé pour la valeur null, il peut être marqué comme not_null. Consultez [C++ Core Guidelines F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md)\
Le symbole'*symbol*'n’est pas testé pour vérifier la valeur NULL sur tous les chemins d’accès. Consultez [C++ Core Guidelines F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md)\
Le type de l’expression'*expr*'est déjà GSL :: not_null. Ne Testez pas la valeur null. Consultez [C++ Core Guidelines F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md)\
N’utilisez pas l’arithmétique de pointeur. Utilisez à la place span. Consultez [C++ Core Guidelines limites. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)\
Expression'*expr*' : dégradation de tableau à pointeur. Consultez [C++ Core Guidelines limites. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="unique_pointer-group"></a>Groupe de UNIQUE_POINTER

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md)\
Le paramètre'*paramètre*'est une référence au `const` pointeur unique, utilisez const t * ou const t& à la place. Consultez [C++ Core Guidelines R. 32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md)\
Le paramètre'*paramètre*'est une référence au pointeur unique et il n’est jamais réassigné ou réinitialisé, utilisez t * ou t& à la place. Consultez [C++ Core Guidelines R. 33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)\
Déplacez, copiez, réassignez ou réinitialisez un pointeur intelligent local'*symbol*'. Consultez [C++ Core Guidelines R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md)\
Le paramètre de pointeur intelligent'*symbol*'est utilisé uniquement pour accéder au pointeur contenu. Utilisez à la place T * ou T&. Consultez [C++ Core Guidelines R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="shared_pointer-group"></a>Groupe de SHARED_POINTER

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)\
Déplacez, copiez, réassignez ou réinitialisez un pointeur intelligent local'*symbol*'. Consultez [C++ Core Guidelines R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md)\
Le paramètre de pointeur intelligent'*symbol*'est utilisé uniquement pour accéder au pointeur contenu. Utilisez à la place T * ou T&. Consultez [C++ Core Guidelines R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md)\
Le paramètre de pointeur partagé'*symbol*'est passé par la référence rvalue. Passer par valeur à la place. Consultez [C++ Core Guidelines R. 34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md)\
Le paramètre de pointeur partagé'*symbol*'est passé par référence et n’est pas réinitialisé ou réassigné. Utilisez à la place T * ou T&. Consultez [C++ Core Guidelines R. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md)\
Le paramètre de pointeur partagé'*symbol*'n’est pas copié ou déplacé. Utilisez à la place T * ou T&. Consultez [C++ Core Guidelines R. 36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>Groupe de déclarations

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md)\
L’initialiseur global appelle une fonction non constexpr'*symbol*'. Consultez [C++ Core Guidelines I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md)\
L’initialiseur global accède à l’objet extern'*symbol*'. Consultez [C++ Core Guidelines I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md)\
Évitez les objets sans nom avec une construction et une destruction personnalisées. Voir [es. 84 : ne pas (essayez) de déclarer une variable locale sans nom](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>Groupe de classes

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md)\
Si vous définissez ou supprimez une opération par défaut dans le type'*symbol*', définissez ou supprimez-les toutes. Consultez [C++ Core Guidelines C. 21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md)\
La fonction'*symbol*'doit être marquée avec’override'. Consultez [C. 128 : les fonctions virtuelles doivent spécifier exactement une de virtuelle, override ou final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md)\
La fonction'*Symbol_1*'masque une fonction non virtuelle'*symbol_2*'. Voir [C++ Core Guidelines C. 128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md)\
La fonction'*symbol*'doit spécifier un seul’Virtual', 'override’ou’final'. Consultez [C. 128 : les fonctions virtuelles doivent spécifier exactement une de virtuelle, override ou final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

[C26436 NEED_VIRTUAL_DTOR](C26436.md)\
Le type'*symbol*'avec une fonction virtuelle a besoin d’un destructeur public virtuel ou non virtuel protégé. Voir [C++ Core Guidelines C. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).

[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md)\
Le destructeur de substitution ne doit pas utiliser de spécificateurs explicites’override’ou’Virtual'. Consultez [C. 128 : les fonctions virtuelles doivent spécifier exactement une de virtuelle, override ou final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="style-group"></a>Groupe de styles

[C26438 NO_GOTO](C26438.md)\
Évitez `goto` . Consultez [C++ Core Guidelines es. 76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Groupe de fonctions

[C26439 SPECIAL_NOEXCEPT](C26439.md)\
Ce genre de fonction ne peut pas être levée. Déclarez-le **`noexcept`** . Voir [C++ Core Guidelines F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md)\
La fonction'*symbol*'peut être déclarée **`noexcept`** . Voir [C++ Core Guidelines F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md)\
La fonction est déclarée **`noexcept`** , mais elle appelle une fonction qui peut lever des exceptions.
Consultez [C++ Core Guidelines : F. 6 : Si votre fonction ne peut pas être levée, déclarez-la noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Groupe d’accès concurrentiel

[C26441 NO_UNNAMED_GUARDS](C26441.md)\
Les objets Guard doivent être nommés. Consultez [C++ Core Guidelines CP. 44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>Groupe CONSt

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md)\
L’argument de référence'*argument*'pour la fonction'*Function*'peut être marqué comme `const` . Consultez [C++ Core Guidelines con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[USE_CONST_POINTER_ARGUMENTS C26461](c26461.md): \
L’argument de pointeur'*argument*'pour la fonction'*Function*'peut être marqué comme pointeur vers `const` . Consultez [C++ Core Guidelines con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md)\
La valeur vers laquelle pointe'*variable*'est assignée une seule fois. Marquez-la comme pointeur vers `const` . Consultez [C++ Core Guidelines con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md)\
Les éléments du tableau'*Array*'ne sont assignés qu’une seule fois. Marquez les éléments `const` . Consultez [C++ Core Guidelines con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md)\
Les valeurs vers lesquelles pointent des éléments de tableau'*Array*'ne sont assignées qu’une seule fois, marquez les éléments comme pointeur vers `const` . Consultez [C++ Core Guidelines con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md)\
La variable'*variable*'n’est assignée qu’une seule fois, marquez-la comme `const` . Consultez [C++ Core Guidelines con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md)\
Cette *fonction* de fonction peut être marquée `constexpr` si l’évaluation au moment de la compilation est souhaitée. Voir [C++ Core Guidelines F. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md)\
Cette *fonction* d’appel de fonction peut utiliser `constexpr` si l’évaluation au moment de la compilation est souhaitée. Consultez [C++ Core Guidelines con. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>Groupe de types

[C26437 DONT_SLICE](C26437.md)\
Ne pas découper. Consultez [C++ Core Guidelines es. 63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md)\
N’utilisez pas `const_cast` pour effectuer un cast `const` . `const_cast` n’est pas obligatoire. cast d’ou la volatilité n’est pas supprimée par cette conversion. Consultez [C++ Core Guidelines type. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md)\
N’utilisez pas `static_cast` downcasts. Un cast à partir d’un type polymorphe doit utiliser dynamic_cast. Consultez [C++ Core Guidelines type. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md)\
N’utilisez pas `reinterpret_cast` . Un cast à partir de void * peut utiliser `static_cast` . Consultez [C++ Core Guidelines type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md)\
N’utilisez pas `static_cast` de pour les conversions arithmétiques. Utilisez l’initialisation des accolades, GSL :: narrow_cast ou GSL :: Narrow. Consultez [C++ Core Guidelines type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md)\
N’effectuez pas de cast entre les types pointeur où le type source et le type cible sont identiques. Consultez [C++ Core Guidelines type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md)\
N’effectuez pas de cast entre les types pointeur lorsque la conversion peut être implicite. Consultez [C++ Core Guidelines type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md)\
N’utilisez pas de casts de style de fonction. Consultez [C++ Core Guidelines es. 49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md)\
N’utilisez pas `reinterpret_cast` . Consultez [C++ Core Guidelines type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md)\
N’utilisez pas `static_cast` downcasts. Consultez [C++ Core Guidelines type. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md)\
N’utilisez pas `const_cast` pour effectuer un cast `const` . Consultez [C++ Core Guidelines type. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md)\
N’utilisez pas de casts de style C. Consultez [C++ Core Guidelines type. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md)\
La variable'*variable*'n’est pas initialisée. Initialisez toujours un objet. Consultez [C++ Core Guidelines type. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md)\
La variable'*variable*'n’est pas initialisée. Initialisez toujours une variable membre. Consultez [C++ Core Guidelines type. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Groupe de limites

[C26446 USE_GSL_AT](c26446.md)\
Préférez utiliser l' `gsl::at()` opérateur d’indice non vérifié. Consultez [C++ Core Guidelines : Bounds. 4 : n’utilisez pas les fonctions et les types de bibliothèque standard qui ne sont pas des limites-Checked](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md)\
N’utilisez pas l’arithmétique de pointeur. Utilisez à la place span. Consultez [C++ Core Guidelines limites. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md)\
Indexez uniquement les tableaux à l’aide d’expressions constantes. Consultez [C++ Core Guidelines limites. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md)\
La *valeur de la valeur est en* dehors des limites (0, *liées*) de la variable'*variable*'. Indexez uniquement les tableaux à l’aide d’expressions constantes situées dans les limites du tableau. Consultez [C++ Core Guidelines limites. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)\
Expression'*expr*' : dégradation de tableau à pointeur. Consultez [C++ Core Guidelines limites. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>Groupe GSL

[C26445 NO_SPAN_REF](c26445.md)\
Une référence à `gsl::span` ou `std::string_view` peut être une indication d’un problème de durée de vie.
Consultez [C++ Core Guidelines GSL. View : views](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md)\
Préférez utiliser l' `gsl::at()` opérateur d’indice non vérifié. Consultez [C++ Core Guidelines : Bounds. 4 : n’utilisez pas les fonctions et les types de bibliothèque standard qui ne sont pas des limites-Checked](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY](c26448.md)\
Envisagez d’utiliser `gsl::finally` si l’action finale est prévue. Consultez [C++ Core Guidelines : GSL. util : Utilities](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md)\
`gsl::span` ou `std::string_view` créé à partir d’un temporaire n’est pas valide lorsque le temporaire est invalidé. Consultez [C++ Core Guidelines : GSL. View : views](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).

## <a name="deprecated-warnings"></a>Avertissements déconseillés

Les avertissements suivants sont présents dans un ensemble de règles expérimentaux précoce de l’outil de vérification des recommandations de base, mais sont désormais déconseillés et peuvent être ignorés sans risque. Les avertissements sont remplacés par des avertissements de la liste ci-dessus.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>Voir aussi

[Utilisation des contrôleurs de C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
