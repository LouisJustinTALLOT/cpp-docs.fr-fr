---
title: atomic, structure
ms.date: 04/20/2018
f1_keywords:
- atomic/std::atomic
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
ms.openlocfilehash: 8701078f8a034d80dae41eee0d842fb15fd8d3a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203934"
---
# <a name="atomic-structure"></a>atomic, structure

Décrit un objet qui effectue des opérations atomiques sur une valeur stockée de type *Ty*.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct atomic;
```

## <a name="members"></a>Membres

|Membre|Description|
|----------|-----------------|
|**Constructeur**||
|[atomique](#atomic)|Construit un objet atomique.|
|**Opérateurs**||
|[Atomic :: Operator Ty](#op_ty)|Lit et retourne la valeur stockée. ([Atomic :: Load](#load))|
|[Atomic :: Operator =](#op_eq)|Utilise une valeur spécifiée pour remplacer la valeur stockée. ([Atomic :: Store](#store))|
|[Atomic :: Operator + +](#op_inc)|Incrémente la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.|
|[Atomic :: Operator + =](#op_add_eq)|Ajoute une valeur spécifiée à la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.|
|[Atomic :: Operator--](#op_dec)|Décrémente la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.|
|[Atomic :: Operator-=](#op_sub_eq)|Soustrait une valeur spécifiée de la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.|
|[Atomic :: Operator&=](#op_and_eq)|Effectue une opération de bits and sur une valeur spécifiée et la valeur stockée. Utilisé uniquement par les spécialisations intégrales.|
|[Atomic :: Operator&#124;=](#op_or_eq)|Effectue une opération de bits or sur une valeur spécifiée et la valeur stockée. Utilisé uniquement par les spécialisations intégrales.|
|[Atomic :: Operator ^ =](#op_xor_eq)|Effectue une opération OR exclusive au niveau du bit sur une valeur spécifiée et la valeur stockée. Utilisé uniquement par les spécialisations intégrales.|
|**Fonctions**||
|[compare_exchange_strong](#compare_exchange_strong)|Effectue une opération de *atomic_compare_and_exchange* sur **`this`** et retourne le résultat.|
|[compare_exchange_weak](#compare_exchange_weak)|Effectue une opération de *weak_atomic_compare_and_exchange* sur **`this`** et retourne le résultat.|
|[fetch_add](#fetch_add)|Ajoute une valeur spécifiée à la valeur stockée.|
|[fetch_and](#fetch_and)|Effectue une opération de bits and sur une valeur spécifiée et la valeur stockée.|
|[fetch_or](#fetch_or)|Effectue une opération de bits or sur une valeur spécifiée et la valeur stockée.|
|[fetch_sub](#fetch_sub)|Soustrait une valeur spécifiée de la valeur stockée.|
|[fetch_xor](#fetch_xor)|Effectue une opération OR exclusive au niveau du bit sur une valeur spécifiée et la valeur stockée.|
|[is_lock_free](#is_lock_free)|Spécifie si les opérations atomiques sur **`this`** sont *sans verrou*. Un type atomique est *sans verrou* si aucune opération atomique sur ce type utilise un verrou.|
|[load](#load)|Lit et retourne la valeur stockée.|
|[store](#store)|Utilise une valeur spécifiée pour remplacer la valeur stockée.|

## <a name="remarks"></a>Notes

Le type *Ty* doit être *copié*de façon triviale. Autrement dit, l’utilisation de [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) pour copier ses octets doit produire un objet *Ty* valide qui correspond à l’objet d’origine. Les fonctions membres [compare_exchange_weak](#compare_exchange_weak) et [compare_exchange_strong](#compare_exchange_strong) utilisent [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) pour déterminer si deux valeurs *Ty* sont égales. Ces fonctions n’utilisent pas un *Ty*défini par Ty `operator==` . Les fonctions membres de `atomic` utilisent `memcpy` pour copier des valeurs de type *Ty*.

Une spécialisation partielle **, \<Ty \*> atomique**, existe pour tous les types pointeur. La spécialisation permet d’ajouter un décalage à la valeur de pointeur gérée ou de lui soustraire un décalage. Les opérations arithmétiques acceptent un argument de type `ptrdiff_t` et ajustent cet argument en fonction de la taille de *Ty* pour être cohérente avec l’arithmétique d’adresse ordinaire.

Une spécialisation existe pour chaque type intégral, à l’exception de **`bool`** . Chaque spécialisation fournit un ensemble complet de méthodes pour les opérations atomiques arithmétiques et logiques.

||||
|-|-|-|
|**atomique\<char>**|**atomique\<signed char>**|**atomique\<unsigned char>**|
|**atomique\<char16_t>**|**atomique\<char32_t>**|**atomique\<wchar_t>**|
|**atomique\<short>**|**atomique\<unsigned short>**|**atomique\<int>**|
|**atomique\<unsigned int>**|**atomique\<long>**|**atomique\<unsigned long>**|
|**atomique\<long long>**|**atomique\<unsigned long long>**|

Les spécialisations intégrales sont dérivées des types `atomic_integral` correspondants. Par exemple, **Atomic \<unsigned int> ** est dérivée de `atomic_uint` .

## <a name="requirements"></a>Spécifications

**En-tête :**\<atomic>

**Espace de noms :** std

## <a name="atomicatomic"></a><a name="atomic"></a>Atomic :: Atomic

Construit un objet atomique.

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ajoutée*\
Valeur d’initialisation.

### <a name="remarks"></a>Notes

Les objets atomiques ne peuvent pas être copiés ou déplacés.

Les objets qui sont des instanciations d’Atomic \<*Ty*> peuvent être initialisés uniquement par le constructeur qui accepte un argument de type *Ty* et non à l’aide de l’initialisation d’agrégats. Toutefois, les objets atomic_integral peuvent être initialisés uniquement à l’aide de l’initialisation d’agrégats.

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="atomicoperator-ty"></a><a name="op_ty"></a>Atomic :: Operator *Ty*

Opérateur pour le type spécifié pour le modèle, Atomic \<*Ty*> . Récupère la valeur stockée dans ** \* ce**.

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>Notes

Cet opérateur applique la `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="atomicoperator"></a><a name="op_eq"></a>Atomic :: Operator =

Stocke une valeur spécifiée.

```cpp
Ty operator=(
   Ty Value
) volatile noexcept;
Ty operator=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ajoutée*\
Objet *Ty* .

### <a name="return-value"></a>Valeur de retour

Retourne une *valeur*.

## <a name="atomicoperator"></a><a name="op_inc"></a>Atomic :: Operator + +

Incrémente la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>Valeur de retour

Les deux premiers opérateurs retournent la valeur incrémentée ; les deux derniers opérateurs retournent la valeur avant l’incrément. Les opérateurs utilisent l' `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="atomicoperator"></a><a name="op_add_eq"></a>Atomic :: Operator + =

Ajoute une valeur spécifiée à la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.

```cpp
Ty atomic<Ty>::operator+=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator+=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ajoutée*\
Valeur intégrale ou de pointeur.

### <a name="return-value"></a>Valeur de retour

Objet *Ty* qui contient le résultat de l’addition.

### <a name="remarks"></a>Notes

Cet opérateur utilise la `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="atomicoperator--"></a><a name="op_dec"></a>Atomic :: Operator--

Décrémente la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>Valeur de retour

Les deux premiers opérateurs retournent la valeur décrémentée ; les deux derniers opérateurs retournent la valeur avant la décrémentation. Les opérateurs utilisent l' `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="atomicoperator-"></a><a name="op_sub_eq"></a>Atomic :: Operator-=

Soustrait une valeur spécifiée de la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.

```cpp
Ty atomic<Ty>::operator-=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator-=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ajoutée*\
Valeur intégrale ou de pointeur.

### <a name="return-value"></a>Valeur de retour

Objet *Ty* qui contient le résultat de la soustraction.

### <a name="remarks"></a>Notes

Cet opérateur utilise la `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="atomicoperator"></a><a name="op_and_eq"></a>Atomic :: Operator&=

Effectue une opération de bits and sur une valeur spécifiée et la valeur stockée de ** \* ce**. Utilisé uniquement par les spécialisations intégrales.

```cpp
atomic<Ty>::operator&= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator&= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ajoutée*\
Valeur de type *Ty*.

### <a name="return-value"></a>Valeur de retour

Résultat de l’opération de bits and.

### <a name="remarks"></a>Notes

Cet opérateur effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de ** \* ce** par *une valeur and* au niveau du bit et la valeur actuelle stockée dans ** \* ce**, dans les contraintes de l' `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="atomicoperator124"></a><a name="op_or_eq"></a>Atomic :: Operator&#124;=

Effectue une opération de bits or sur une valeur spécifiée et la valeur stockée de ** \* ce**. Utilisé uniquement par les spécialisations intégrales.

```cpp
atomic<Ty>::operator|= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator|= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ajoutée*\
Valeur de type *Ty*.

### <a name="return-value"></a>Valeur de retour

Résultat de l’opération or au niveau du bit.

### <a name="remarks"></a>Notes

Cet opérateur effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de ** \* ce** par un opérateur de bits or de *valeur* et la valeur actuelle stockée dans ** \* ce**, dans les contraintes des contraintes de `memory_order_seq_cst` [memory_order](atomic-enums.md) .

## <a name="atomicoperator"></a><a name="op_xor_eq"></a>Atomic :: Operator ^ =

Effectue une opération OR exclusive au niveau du bit sur une valeur spécifiée et la valeur stockée de ** \* ce**. Utilisé uniquement par les spécialisations intégrales.

```cpp
atomic<Ty>::operator^= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator^= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ajoutée*\
Valeur de type *Ty*.

### <a name="return-value"></a>Valeur de retour

Résultat de l’opération OR exclusive au niveau du bit.

### <a name="remarks"></a>Notes

Cet opérateur effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de ** \* ce** par une *valeur* or exclusive au niveau du bit et la valeur actuelle stockée dans ** \* ce**, dans les contraintes des contraintes de `memory_order_seq_cst` [memory_order](atomic-enums.md) .

## <a name="atomiccompare_exchange_strong"></a><a name="compare_exchange_strong"></a>Atomic :: compare_exchange_strong

Effectue une opération atomique de comparaison et d’échange sur ** \* ce**.

```cpp
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Venir*\
Valeur de type *Ty*.

*Ajoutée*\
Valeur de type *Ty*.

*Order1*\
Premier `memory_order` argument.

*Order2*\
Deuxième argument `memory_order`.

### <a name="return-value"></a>Valeur de retour

**`bool`** Qui indique le résultat de la comparaison de valeurs.

### <a name="remarks"></a>Notes

Cette opération **atomique de comparaison et d’échange \* ** compare la valeur stockée avec *exp*. Si les valeurs sont égales, l’opération remplace la valeur stockée dans ** \* cette** *valeur* par une opération de lecture-modification-écriture et en appliquant les contraintes d’ordre de mémoire spécifiées par *Order1*. Si les valeurs ne sont pas égales, l’opération utilise la valeur stockée dans ** \* ce** pour remplacer *exp* et applique les contraintes d’ordre de mémoire spécifiées par *Order2*.

Les surcharges qui n’ont pas de deuxième `memory_order` utilisent un *Order2* implicite basé sur la valeur de *Order1*. Si *Order1* est `memory_order_acq_rel` , *Order2* est `memory_order_acquire` . Si *Order1* est `memory_order_release` , *Order2* est `memory_order_relaxed` . Dans tous les autres cas, *Order2* est égal à *Order1*.

Pour les surcharges qui acceptent deux `memory_order` paramètres, la valeur de *Order2* ne doit pas être `memory_order_release` ou `memory_order_acq_rel` , et ne doit pas être supérieure à la valeur de *Order1*.

## <a name="atomiccompare_exchange_weak"></a><a name="compare_exchange_weak"></a>Atomic :: compare_exchange_weak

Effectue une opération de comparaison atomique et d’échange faible sur ** \* ce**.

```cpp
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Venir*\
Valeur de type *Ty*.

*Ajoutée*\
Valeur de type *Ty*.

*Order1*\
Premier `memory_order` argument.

*Order2*\
Deuxième argument `memory_order`.

### <a name="return-value"></a>Valeur de retour

**`bool`** Qui indique le résultat de la comparaison de valeurs.

### <a name="remarks"></a>Notes

Cette opération **atomique de comparaison et d’échange \* ** compare la valeur stockée avec *exp*. Si les valeurs sont égales, l’opération remplace la valeur stockée dans ** \* cette** *valeur* par une opération de lecture-modification-écriture et en appliquant les contraintes d’ordre de mémoire spécifiées par *Order1*. Si les valeurs ne sont pas égales, l’opération utilise la valeur stockée dans ** \* ce** pour remplacer *exp* et applique les contraintes d’ordre de mémoire spécifiées par *Order2*.

Une opération atomique faible de comparaison et d’échange effectue un échange si les valeurs comparées sont égales. Si les valeurs ne sont pas égales, l’opération n’est pas garantie pour effectuer un échange.

Les surcharges qui n’ont pas de deuxième `memory_order` utilisent un *Order2* implicite basé sur la valeur de *Order1*. Si *Order1* est `memory_order_acq_rel` , *Order2* est `memory_order_acquire` . Si *Order1* est `memory_order_release` , *Order2* est `memory_order_relaxed` . Dans tous les autres cas, *Order2* est égal à *Order1*.

Pour les surcharges qui acceptent deux `memory_order` paramètres, la valeur de *Order2* ne doit pas être `memory_order_release` ou `memory_order_acq_rel` , et ne doit pas être supérieure à la valeur de *Order1*.

## <a name="atomicexchange"></a><a name="exchange"></a>Atomic :: Exchange

Utilise une valeur spécifiée pour remplacer la valeur stockée de ** \* ce**.

```cpp
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ajoutée*\
Valeur de type *Ty*.

*Ordre*\
`memory_order`

### <a name="return-value"></a>Valeur de retour

Valeur stockée de ** \* ce** avant l’échange.

### <a name="remarks"></a>Notes

Cette opération effectue une opération de lecture-modification-écriture pour utiliser *value* afin de remplacer la valeur stockée dans ** \* ce**, dans les contraintes de mémoire spécifiées par l' *ordre*.

## <a name="atomicfetch_add"></a><a name="fetch_add"></a>Atomic :: fetch_add

Extrait la valeur stockée dans ** \* ce**, puis ajoute une valeur spécifiée à la valeur stockée.

```cpp
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ajoutée*\
Valeur de type *Ty*.

*Ordre*\
`memory_order`

### <a name="return-value"></a>Valeur de retour

Objet *Ty* qui contient la valeur stockée dans ** \* ce** avant l’ajout.

### <a name="remarks"></a>Notes

La `fetch_add` méthode effectue une opération de lecture-modification-écriture pour ajouter atomiquement la *valeur* à la valeur stockée dans ** \* ce**et applique les contraintes de mémoire spécifiées par *ordre*.

## <a name="atomicfetch_and"></a><a name="fetch_and"></a>Atomic :: fetch_and

Effectue une opération de bits and sur une valeur et une valeur existante stockée dans ** \* ce**.

```cpp
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ajoutée*\
Valeur de type *Ty*.

*Ordre*\
`memory_order`

### <a name="return-value"></a>Valeur de retour

Objet *Ty* qui contient le résultat de l’opération de bits and.

### <a name="remarks"></a>Notes

La `fetch_and` méthode effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de ** \* ce** par un opérateur de bits and de *valeur* et la valeur actuelle stockée dans ** \* ce**, dans les contraintes de mémoire spécifiées par l' *ordre*.

## <a name="atomicfetch_or"></a><a name="fetch_or"></a>Atomic :: fetch_or

Effectue une opération de bits or sur une valeur et une valeur existante stockée dans ** \* ce**.

```cpp
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ajoutée*\
Valeur de type *Ty*.

*Ordre*\
`memory_order`

### <a name="return-value"></a>Valeur de retour

Objet *Ty* qui contient le résultat de l’opération or au niveau du bit.

### <a name="remarks"></a>Notes

La `fetch_or` méthode effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de ** \* ce** par un opérateur de bits or de *valeur* et la valeur actuelle stockée dans ** \* ce**, dans les contraintes de mémoire spécifiées par l' *ordre*.

## <a name="atomicfetch_sub"></a><a name="fetch_sub"></a>Atomic :: fetch_sub

Soustrait une valeur spécifiée de la valeur stockée.

```cpp
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ajoutée*\
Valeur de type *Ty*.

*Ordre*\
`memory_order`

### <a name="return-value"></a>Valeur de retour

Objet *Ty* qui contient le résultat de la soustraction.

### <a name="remarks"></a>Notes

La `fetch_sub` méthode effectue une opération de lecture-modification-écriture pour soustraire de *manière*atomique la *valeur* de la valeur stockée dans ** \* ce**, dans les contraintes de mémoire spécifiées par l’ordre.

## <a name="atomicfetch_xor"></a><a name="fetch_xor"></a>Atomic :: fetch_xor

Effectue une opération OR exclusive au niveau du bit sur une valeur et une valeur existante stockée dans ** \* ce**.

```cpp
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ajoutée*\
Valeur de type *Ty*.

*Ordre*\
`memory_order`

### <a name="return-value"></a>Valeur de retour

Objet *Ty* qui contient le résultat de l’opération OR exclusive au niveau du bit.

### <a name="remarks"></a>Notes

La `fetch_xor` méthode effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de ** \* ce** par une *valeur* or exclusive au niveau du bit et la valeur actuelle stockée dans ** \* ce**et applique les contraintes de mémoire spécifiées par l' *ordre*.

## <a name="atomicis_lock_free"></a><a name="is_lock_free"></a>Atomic :: is_lock_free

Spécifie si les opérations atomiques sur ** \* ce** sont sans verrou.

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>Valeur de retour

true si les opérations atomiques sur ** \* ce** sont sans verrou ; sinon, false.

### <a name="remarks"></a>Notes

Un type atomique est sans verrou si aucune opération atomique sur ce type utilise un verrou.

## <a name="atomicload"></a><a name="load"></a>Atomic :: Load

Récupère la valeur stockée dans ** \* ce**, dans les contraintes de mémoire spécifiées.

```cpp
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const volatile noexcept;
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const noexcept;
```

### <a name="parameters"></a>Paramètres

*Ordre*\
`memory_order` La *commande* ne doit pas être `memory_order_release` ou `memory_order_acq_rel` .

### <a name="return-value"></a>Valeur de retour

Valeur récupérée qui est stockée dans ** \* ce**.

## <a name="atomicstore"></a><a name="store"></a>Atomic :: Store

Stocke une valeur spécifiée.

```cpp
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ajoutée*\
Objet *Ty* .

*Ordre*\
`memory_order`Contrainte.

### <a name="remarks"></a>Notes

Cette fonction membre stocke atomiquement la *valeur* dans **`*this`** , dans les contraintes de mémoire spécifiées par l' *ordre*.

## <a name="see-also"></a>Voir aussi

[\<atomic>](../standard-library/atomic.md)\
[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
