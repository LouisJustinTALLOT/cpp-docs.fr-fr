---
title: '&lt;atomic&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <atomic>
- atomic/std::atomic_int_least32_t
- atomic/std::atomic_ullong
- atomic/std::atomic_ptrdiff_t
- atomic/std::atomic_char16_t
- atomic/std::atomic_schar
- atomic/std::atomic_ulong
- atomic/std::atomic_uint_fast32_t
- atomic/std::atomic_uint8_t
- atomic/std::atomic_int32_t
- atomic/std::atomic_uint_fast64_t
- atomic/std::atomic_uint32_t
- atomic/std::atomic_int16_t
- atomic/std::atomic_uintmax_t
- atomic/std::atomic_intmax_t
- atomic/std::atomic_long
- atomic/std::atomic_int
- atomic/std::atomic_uint_least8_t
- atomic/std::atomic_size_t
- atomic/std::atomic_uint_fast16_t
- atomic/std::atomic_wchar_t
- atomic/std::atomic_int_fast64_t
- atomic/std::atomic_uint_fast8_t
- atomic/std::atomic_int_fast8_t
- atomic/std::atomic_intptr_t
- atomic/std::atomic_uint
- atomic/std::atomic_uint16_t
- atomic/std::atomic_char32_t
- atomic/std::atomic_uint64_t
- atomic/std::atomic_ushort
- atomic/std::atomic_int_least16_t
- atomic/std::atomic_char
- atomic/std::atomic_uint_least32_t
- atomic/std::atomic_uintptr_t
- atomic/std::atomic_short
- atomic/std::atomic_llong
- atomic/std::atomic_uint_least16_t
- atomic/std::atomic_int_fast16_t
- atomic/std::atomic_int_least8_t
- atomic/std::atomic_int_least64_t
- atomic/std::atomic_int_fast32_t
- atomic/std::atomic_uchar
- atomic/std::atomic_int8_t
- atomic/std::atomic_int64_t
- atomic/std::atomic_uint_least64_t
dev_langs:
- C++
ms.assetid: e79a6b9f-52ff-48da-9554-654c4e1999f6
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 86978cd4549f0672dac7cad0e4713380ea189c27
ms.openlocfilehash: 0727a9bab67872237ffe6f747bd0be3f538eb01d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/18/2017

---
# <a name="ltatomicgt"></a>&lt;atomic&gt;
Définit les classes et les classes de modèle à utiliser pour créer des types qui prennent en charge les opérations atomiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#include <atomic>  
```  
  
## <a name="remarks"></a>Remarques  
  
> [!NOTE]
>  Dans le code est compilé à l’aide de **/CLR**, cet en-tête est bloqué.  
  
 Une opération atomique a deux propriétés clés qui vous aident à utiliser plusieurs threads pour manipuler correctement un objet sans utiliser de verrous mutex.  
  
-   Comme une opération atomique est indivisible, une deuxième opération atomique sur le même objet à partir d’un autre thread peut obtenir l’état de l’objet uniquement avant ou après la première opération atomique.  
  
-   En fonction de son argument [memory_order](../standard-library/atomic-enums.md#memory_order_enum), une opération atomique établit les contraintes d’ordre pour la visibilité des effets d’autres opérations atomiques dans le même thread. Par conséquent, elle empêche les optimisations du compilateur qui enfreignent les contraintes d’ordre.  
  
 Sur certaines plateformes, il n’est pas possible d’implémenter efficacement des opérations atomiques pour certains types sans utiliser de verrous `mutex`. Un type atomique est *sans verrou* si aucune opération atomique sur ce type utilise un verrou.  
  
 **C++11** : Dans les gestionnaires de signal, vous pouvez effectuer des opérations atomiques sur un objet `obj` si `obj.is_lock_free()` ou `atomic_is_lock_free(x)` ont la valeur true.  
  
 La classe [atomic_flag](../standard-library/atomic-flag-structure.md) fournit un type atomique minimal qui contient un indicateur `bool`. Ses opérations sont toujours sans verrou.  
  
 La classe de modèle `atomic<T>` stocke un objet de son type d’argument `T` et fournit un accès atomique à cette valeur stockée. Vous pouvez l’instancier à l’aide de tout type pouvant être copié à l’aide de [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) et dont l’égalité est vérifiée à l’aide de [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md). En particulier, vous pouvez l’utiliser avec les types définis par l’utilisateur qui répondent à ces exigences et, dans de nombreux cas, avec les types à virgule flottante.  
  
 Le modèle a également un ensemble de spécialisations pour les types intégraux et une spécialisation partielle pour les pointeurs. Ces spécialisations fournissent des opérations supplémentaires qui ne sont pas disponibles par le biais du modèle principal.  
  
## <a name="pointer-specializations"></a>Spécialisations de pointeur  
 Les spécialisations partielles `atomic<T *>` s’appliquent à tous les types de pointeur. Elles fournissent des méthodes pour l’arithmétique de pointeur.  
  
## <a name="integral-specializations"></a>Spécialisations intégrales  
 Les spécialisations `atomic<integral>` s’appliquent à tous les types intégraux. Elles fournissent des opérations supplémentaires qui ne sont pas disponibles par le biais du modèle principal.  
  
 Chaque type `atomic<integral>` a une macro correspondante que vous pouvez utiliser dans un `if directive` pour déterminer au moment de la compilation si les opérations sur ce type sont sans verrou. Si la valeur de la macro est zéro, les opérations sur le type ne sont pas sans verrou. Si la valeur est 1, les opérations peuvent être sans verrou et une vérification au moment de l’exécution est nécessaire. Si la valeur est 2, les opérations sont sans verrou. Vous pouvez utiliser la fonction `atomic_is_lock_free` pour déterminer au moment de l’exécution si les opérations sur le type sont sans verrou.  
  
 Pour chacun des types intégraux, il existe un type d’atomique nommé correspondant qui gère un objet de ce type intégral. Chaque type `atomic_integral` a le même ensemble de fonctions membres que l’instanciation correspondante de `atomic<T>` et peut être passée à toute fonction atomique non-membre.  
  
|Type de `atomic_integral`|Type intégral|Macro `atomic_is_lock_free`|  
|----------------------------|-------------------|---------------------------------|  
|`atomic_char`|`char`|`ATOMIC_CHAR_LOCK_FREE`|  
|`atomic_schar`|`signed char`|`ATOMIC_CHAR_LOCK_FREE`|  
|`atomic_uchar`|`unsigned char`|`ATOMIC_CHAR_LOCK_FREE`|  
|`atomic_char16_t`|`char16_t`|`ATOMIC_CHAR16_T_LOCK_FREE`|  
|`atomic_char32_t`|`char32_t`|`ATOMIC_CHAR32_T_LOCK_FREE`|  
|`atomic_wchar_t`|`wchar_t`|`ATOMIC_WCHAR_T_LOCK_FREE`|  
|`atomic_short`|`short`|`ATOMIC_SHORT_LOCK_FREE`|  
|`atomic_ushort`|`unsigned short`|`ATOMIC_SHORT_LOCK_FREE`|  
|`atomic_int`|`int`|`ATOMIC_INT_LOCK_FREE`|  
|`atomic_uint`|`unsigned int`|`ATOMIC_INT_LOCK_FREE`|  
|`atomic_long`|`long`|`ATOMIC_LONG_LOCK_FREE`|  
|`atomic_ulong`|`unsigned long`|`ATOMIC_LONG_LOCK_FREE`|  
|`atomic_llong`|`long long`|`ATOMIC_LLONG_LOCK_FREE`|  
|`atomic_ullong`|`unsigned long long`|`ATOMIC_LLONG_LOCK_FREE`|  
  
 Des noms typedef existent pour les spécialisations du modèle atomique pour certains types qui sont définis dans l’en-tête \<inttypes.h>.  
  
|Type atomique|Nom typedef|  
|-----------------|------------------|  
|`atomic_int8_t`|`atomic<int8_t>`|  
|`atomic_uint8_t`|`atomic<uint8_t>`|  
|`atomic_int16_t`|`atomic<int16_t>`|  
|`atomic_uint16_t`|`atomic<uint16_t>`|  
|`atomic_int32_t`|`atomic<int32_t>`|  
|`atomic_uint32_t`|`atomic<uint32_t>`|  
|`atomic_int64_t`|`atomic<int64_t>`|  
|`atomic_uint64_t`|`atomic<uint64_t>`|  
|`atomic_int_least8_t`|`atomic<int_least8_t>`|  
|`atomic_uint_least8_t`|`atomic<uint_least8_t>`|  
|`atomic_int_least16_t`|`atomic<int_least16_t>`|  
|`atomic_uint_least16_t`|`atomic<uint_least16_t>`|  
|`atomic_int_least32_t`|`atomic<int_least32_t>`|  
|`atomic_uint_least32_t`|`atomic<uint_least32_t>`|  
|`atomic_int_least64_t`|`atomic<int_least64_t>`|  
|`atomic_uint_least64_t`|`atomic<uint_least64_t>`|  
|`atomic_int_fast8_t`|`atomic<int_fast8_t>`|  
|`atomic_uint_fast8_t`|`atomic<uint_fast8_t>`|  
|`atomic_int_fast16_t`|`atomic<int_fast16_t>`|  
|`atomic_uint_fast16_`|`atomic<uint_fast16_t>`|  
|`atomic_int_fast32_t`|`atomic<int_fast32_t>`|  
|`atomic_uint_fast32_t`|`atomic<uint_fast32_t>`|  
|`atomic_int_fast64_t`|`atomic<int_fast64_t>`|  
|`atomic_uint_fast64_t`|`atomic<uint_fast64_t>`|  
|`atomic_intptr_t`|`atomic<intptr_t>`|  
|`atomic_uintptr_t`|`atomic<uintptr_t>`|  
|`atomic_size_t`|`atomic<size_t>`|  
|`atomic_ptrdiff_t`|`atomic<ptrdiff_t>`|  
|`atomic_intmax_t`|`atomic<intmax_t>`|  
|`atomic_uintmax_t`|`atomic<uintmax_t>`|  
  
## <a name="structs"></a>Structures  
  
|Nom|Description|  
|----------|-----------------|  
|[atomic, structure](../standard-library/atomic-structure.md)|Décrit un objet qui effectue des opérations atomiques sur une valeur stockée.|  
|[atomic_flag, structure](../standard-library/atomic-flag-structure.md)|Décrit un objet qui définit et efface atomiquement un indicateur `bool`.|  
  
## <a name="enums"></a>Enums  
  
|Nom|Description|  
|----------|-----------------|  
|[memory_order, énumération](../standard-library/atomic-enums.md#memory_order_enum)|Fournit les noms symboliques des opérations de synchronisation sur les emplacements de mémoire. Ces opérations affectent l’affichage des assignations d’un thread dans un autre thread.|  
  
## <a name="functions"></a>Fonctions  
 Dans la liste suivante, les fonctions qui ne se terminent pas par `_explicit` ont la sémantique du `_explicit` correspondant, sauf qu’elles ont les arguments [memory_order](../standard-library/atomic-enums.md#memory_order_enum) implicites de `memory_order_seq_cst`.  
  
|Nom|Description|  
|----------|-----------------|  
|[atomic_compare_exchange_strong](../standard-library/atomic-functions.md#atomic_compare_exchange_strong)|Effectue une opération *atomique de comparaison et d’échange*.|  
|[atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)|Effectue une opération *atomique de comparaison et d’échange*.|  
|[atomic_compare_exchange_weak](../standard-library/atomic-functions.md#atomic_compare_exchange_weak)|Effectue une opération *atomique faible de comparaison et d’échange*.|  
|[atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)|Effectue une opération *atomique faible de comparaison et d’échange*.|  
|[atomic_exchange](../standard-library/atomic-functions.md#atomic_exchange)|Remplace une valeur stockée.|  
|[atomic_exchange_explicit](../standard-library/atomic-functions.md#atomic_exchange_explicit)|Remplace une valeur stockée.|  
|[atomic_fetch_add](../standard-library/atomic-functions.md#atomic_fetch_add)|Ajoute une valeur spécifiée à la valeur stockée existante.|  
|[atomic_fetch_add_explicit](../standard-library/atomic-functions.md#atomic_fetch_add_explicit)|Ajoute une valeur spécifiée à la valeur stockée existante.|  
|[atomic_fetch_and](../standard-library/atomic-functions.md#atomic_fetch_and)|Effectue une opération `and` au niveau du bit sur une valeur spécifiée et une valeur stockée existante.|  
|[atomic_fetch_and_explicit](../standard-library/atomic-functions.md#atomic_fetch_and_explicit)|Effectue une opération `and` au niveau du bit sur une valeur spécifiée et une valeur stockée existante.|  
|[atomic_fetch_or](../standard-library/atomic-functions.md#atomic_fetch_or)|Effectue une opération `or` au niveau du bit sur une valeur spécifiée et une valeur stockée existante.|  
|[atomic_fetch_or_explicit](../standard-library/atomic-functions.md#atomic_fetch_or_explicit)|Effectue une opération `or` au niveau du bit sur une valeur spécifiée et une valeur stockée existante.|  
|[atomic_fetch_sub](../standard-library/atomic-functions.md#atomic_fetch_sub)|Soustrait une valeur spécifiée de la valeur stockée existante.|  
|[atomic_fetch_sub_explicit](../standard-library/atomic-functions.md#atomic_fetch_sub_explicit)|Soustrait une valeur spécifiée de la valeur stockée existante.|  
|[atomic_fetch_xor](../standard-library/atomic-functions.md#atomic_fetch_xor)|Effectue une opération `exclusive or` au niveau du bit sur une valeur spécifiée et une valeur stockée existante.|  
|[atomic_fetch_xor_explicit](../standard-library/atomic-functions.md#atomic_fetch_xor_explicit)|Effectue une opération `exclusive or` au niveau du bit sur une valeur spécifiée et une valeur stockée existante.|  
|[atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)|Définit l’indicateur dans un objet `atomic_flag` avec la valeur `false`.|  
|[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)|Définit l’indicateur dans un objet `atomic_flag` avec la valeur `false`.|  
|[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set)|Définit l’indicateur dans un objet `atomic_flag` avec la valeur `true`.|  
|[atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)|Définit l’indicateur dans un objet `atomic_flag` avec la valeur `true`.|  
|[atomic_init](../standard-library/atomic-functions.md#atomic_init)|Définit la valeur stockée dans un objet `atomic`.|  
|[atomic_is_lock_free](../standard-library/atomic-functions.md#atomic_is_lock_free)|Spécifie si les opérations atomiques sur un objet spécifié sont sans verrou.|  
|[atomic_load](../standard-library/atomic-functions.md#atomic_load)|Récupère une valeur de manière atomique.|  
|[atomic_load_explicit](../standard-library/atomic-functions.md#atomic_load_explicit)|Récupère une valeur de manière atomique.|  
|[atomic_signal_fence](../standard-library/atomic-functions.md#atomic_signal_fence)|Agit comme une *délimitation* qui établit les spécifications d’ordre de mémoire entre délimitations dans un thread d’appel dont les gestionnaires de signal sont exécutés dans le même thread.|  
|[atomic_store](../standard-library/atomic-functions.md#atomic_store)|Stocke une valeur de manière atomique.|  
|[atomic_store_explicit](../standard-library/atomic-functions.md#atomic_store_explicit)|Stocke une valeur de manière atomique.|  
|[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)|Agit comme une *délimitation* qui établit les spécifications d’ordre de mémoire par rapport aux autres délimitations.|  
|[kill_dependency](../standard-library/atomic-functions.md#kill_dependency)|Arrête une chaîne de dépendance possible.|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)   
 [Informations de référence sur la bibliothèque C++ Standard](../standard-library/cpp-standard-library-reference.md)






