---
title: atomic, structure
ms.date: 04/20/2018
f1_keywords:
- atomic/std::atomic
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
ms.openlocfilehash: 1b3b60d71fcdf68fdf215820535c3bfb3d4dfb2b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456733"
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
|[atomic](#atomic)|Construit un objet atomique.|
|**Opérateurs**||
|[Atomic:: Operator Ty](#op_ty)|Lit et retourne la valeur stockée. ([atomic::load](#load))|
|[atomic::operator=](#op_eq)|Utilise une valeur spécifiée pour remplacer la valeur stockée. ([atomic::store](#store))|
|[atomic::operator++](#op_inc)|Incrémente la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.|
|[atomic::operator+=](#op_add_eq)|Ajoute une valeur spécifiée à la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.|
|[atomic::operator--](#op_dec)|Décrémente la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.|
|[atomic::operator-=](#op_sub_eq)|Soustrait une valeur spécifiée de la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.|
|[atomic::operator&=](#op_and_eq)|Effectue une opération de bits and sur une valeur spécifiée et la valeur stockée. Utilisé uniquement par les spécialisations intégrales.|
|[atomic::operator&#124;=](#op_or_eq)|Effectue une opération de bits or sur une valeur spécifiée et la valeur stockée. Utilisé uniquement par les spécialisations intégrales.|
|[atomic::operator^=](#op_xor_eq)|Effectue une opération OR exclusive au niveau du bit sur une valeur spécifiée et la valeur stockée. Utilisé uniquement par les spécialisations intégrales.|
|**Fonctions**||
|[compare_exchange_strong](#compare_exchange_strong)|Effectue une opération *atomic_compare_and_exchange* sur **ce** et retourne le résultat.|
|[compare_exchange_weak](#compare_exchange_weak)|Effectue une opération *weak_atomic_compare_and_exchange* sur **ce** et retourne le résultat.|
|[fetch_add](#fetch_add)|Ajoute une valeur spécifiée à la valeur stockée.|
|[fetch_and](#fetch_and)|Effectue une opération de bits and sur une valeur spécifiée et la valeur stockée.|
|[fetch_or](#fetch_or)|Effectue une opération de bits or sur une valeur spécifiée et la valeur stockée.|
|[fetch_sub](#fetch_sub)|Soustrait une valeur spécifiée de la valeur stockée.|
|[fetch_xor](#fetch_xor)|Effectue une opération OR exclusive au niveau du bit sur une valeur spécifiée et la valeur stockée.|
|[is_lock_free](#is_lock_free)|Spécifie si les opérations atomiques sur **ce** sont *sans verrou*. Un type atomique est *sans verrou* si aucune opération atomique sur ce type utilise un verrou.|
|[load](#load)|Lit et retourne la valeur stockée.|
|[store](#store)|Utilise une valeur spécifiée pour remplacer la valeur stockée.|

## <a name="remarks"></a>Notes

Le type *Ty* doit être *copié*de façon triviale. Autrement dit, l’utilisation de [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) pour copier ses octets doit produire un objet *Ty* valide qui correspond à l’objet d’origine. Les fonctions membres [compare_exchange_weak](#compare_exchange_weak) et [compare_exchange_strong](#compare_exchange_strong) utilisent [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) pour déterminer si deux valeurs *Ty* sont égales. Ces fonctions n’utilisent pas un défini par `operator==`Ty. Les fonctions membres de `atomic` utilisent `memcpy` pour copier des valeurs de type *Ty*.

Une spécialisation partielle **,\<Atomic \*TY >** , existe pour tous les types pointeur. La spécialisation permet d’ajouter un décalage à la valeur de pointeur gérée ou de lui soustraire un décalage. Les opérations arithmétiques acceptent un argument de `ptrdiff_t` type et ajustent cet argument en fonction de la taille de *Ty* pour être cohérente avec l’arithmétique d’adresse ordinaire.

Une spécialisation existe pour chaque type intégral, à l’exception de **bool**. Chaque spécialisation fournit un ensemble complet de méthodes pour les opérations atomiques arithmétiques et logiques.

||||
|-|-|-|
|**atomic\<char>**|**>\<char signé atomique**|**>\<de caractères non signés atomiques**|
|**atomic\<char16_t>**|**atomic\<char32_t>**|**atomic\<wchar_t>**|
|**atomic\<short>**|**>\<de Short non signé atomique**|**atomic\<int>**|
|**>\<de type int non signé atomique**|**atomic\<long>**|**>\<long non signé atomique**|
|**>\<de longue durée atomique**|**>\<de long long non signé atomique**|

Les spécialisations intégrales sont dérivées des types `atomic_integral` correspondants. Par exemple, **le\<> atomique unsigned int** est dérivé `atomic_uint`de.

## <a name="requirements"></a>Configuration requise

**En-tête:** \<> atomiques

**Espace de noms :** std

## <a name="atomic"></a>Atomic:: Atomic

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

Les objets qui sont des instanciations de la > Atomic\<*Ty*peuvent être initialisés uniquement par le constructeur qui accepte un argument de type *Ty* et non à l’aide de l’initialisation d’agrégats. Toutefois, les objets atomic_integral peuvent être initialisés uniquement à l’aide de l’initialisation d’agrégats.

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="op_ty"></a>Atomic:: Operator *Ty*

Opérateur pour le type spécifié pour le modèle, Atomic\<*Ty*>. Récupère la valeur stockée dans  **\*ce**.

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>Notes

Cet opérateur applique `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_eq"></a>Atomic:: Operator =

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

## <a name="op_inc"></a>Atomic:: Operator + +

Incrémente la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>Valeur de retour

Les deux premiers opérateurs retournent la valeur incrémentée; les deux derniers opérateurs retournent la valeur avant l’incrément. Les opérateurs utilisent `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_add_eq"></a>Atomic:: Operator + =

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

Cet opérateur utilise `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_dec"></a>Atomic:: Operator--

Décrémente la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>Valeur de retour

Les deux premiers opérateurs retournent la valeur décrémentée; les deux derniers opérateurs retournent la valeur avant la décrémentation. Les opérateurs utilisent `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_sub_eq"></a>Atomic:: Operator-=

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

Cet opérateur utilise `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_and_eq"></a>Atomic:: operator & =

Effectue une opération de bits and sur une valeur spécifiée et la valeur stockée de  **\*ce**. Utilisé uniquement par les spécialisations intégrales.

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

Cet opérateur effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*ce** par une valeur and au niveau du *bit et la* valeur actuelle stockée dans  **\*ce**, dans les contraintes de l' `memory_order_seq_cst`objet [memory_order](atomic-enums.md).

## <a name="op_or_eq"></a>Atomic:: Operator&#124;=

Effectue une opération de bits or sur une valeur spécifiée et la valeur stockée de  **\*ce**. Utilisé uniquement par les spécialisations intégrales.

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

Cet opérateur effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*ce** par un opérateur de bits or de *valeur* et la valeur actuelle stockée dans  **\*ce**, dans les contraintes de l' `memory_order_seq_cst`objetcontraintes [memory_order](atomic-enums.md) .

## <a name="op_xor_eq"></a>Atomic:: Operator ^ =

Effectue une opération OR exclusive au niveau du bit sur une valeur spécifiée et la valeur stockée de  **\*ce**. Utilisé uniquement par les spécialisations intégrales.

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

Cet opérateur effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*ce** par une *valeur* or exclusive au niveau du bit et par la valeur actuelle stockée dans  **\*ce**, dans les contraintes de l’objet `memory_order_seq_cst` contraintes [memory_order](atomic-enums.md) .

## <a name="compare_exchange_strong"></a>Atomic:: compare_exchange_strong

Effectue une opération atomique de comparaison et d’échange sur  **\*ce**.

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

Valeur **booléenne** qui indique le résultat de la comparaison de valeurs.

### <a name="remarks"></a>Notes

Cette opération atomique de comparaison  **\*et d’échange** compare la valeur stockée avec *exp*. Si les valeurs sont égales, l’opération remplace la valeur stockée dans  **\*cette** *valeur* par une opération de lecture-modification-écriture et en appliquant les contraintes d’ordre de mémoire spécifiées par *Order1*. Si les valeurs ne sont pas égales, l’opération utilise la valeur stockée dans  **\*ce** pour remplacer *exp* et applique les contraintes d’ordre de mémoire spécifiées par *Order2*.

Les surcharges qui n’ont pas de `memory_order` deuxième utilisent un *Order2* implicite basé sur la valeur de *Order1*. Si *Order1* est `memory_order_acq_rel`, *Order2* est `memory_order_acquire`. Si *Order1* est `memory_order_release`, *Order2* est `memory_order_relaxed`. Dans tous les autres cas, *Order2* est égal à *Order1*.

Pour les surcharges qui acceptent `memory_order` deux paramètres, la valeur de *Order2* ne doit `memory_order_release` pas `memory_order_acq_rel`être ou, et ne doit pas être supérieure à la valeur de *Order1*.

## <a name="compare_exchange_weak"></a>Atomic:: compare_exchange_weak

Effectue une opération de comparaison atomique et d’échange faible sur  **\*ce**.

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

Valeur **booléenne** qui indique le résultat de la comparaison de valeurs.

### <a name="remarks"></a>Notes

Cette opération atomique de comparaison  **\*et d’échange** compare la valeur stockée avec *exp*. Si les valeurs sont égales, l’opération remplace la valeur stockée dans  **\*cette** *valeur* par une opération de lecture-modification-écriture et en appliquant les contraintes d’ordre de mémoire spécifiées par *Order1*. Si les valeurs ne sont pas égales, l’opération utilise la valeur stockée dans  **\*ce** pour remplacer *exp* et applique les contraintes d’ordre de mémoire spécifiées par *Order2*.

Une opération faible de comparaison atomique et d’échange effectue un échange si les valeurs comparées sont égales. Si les valeurs ne sont pas égales, l’opération n’est pas garantie pour effectuer un échange.

Les surcharges qui n’ont pas de `memory_order` deuxième utilisent un *Order2* implicite basé sur la valeur de *Order1*. Si *Order1* est `memory_order_acq_rel`, *Order2* est `memory_order_acquire`. Si *Order1* est `memory_order_release`, *Order2* est `memory_order_relaxed`. Dans tous les autres cas, *Order2* est égal à *Order1*.

Pour les surcharges qui acceptent `memory_order` deux paramètres, la valeur de *Order2* ne doit `memory_order_release` pas `memory_order_acq_rel`être ou, et ne doit pas être supérieure à la valeur de *Order1*.

## <a name="exchange"></a>Atomic:: Exchange

Utilise une valeur spécifiée pour remplacer la valeur stockée de  **\*ce**.

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

Valeur stockée de  **\*ce** avant l’échange.

### <a name="remarks"></a>Notes

Cette opération effectue une opération de lecture-modification-écriture pour utiliser *value* afin de remplacer la valeur stockée dans  **\*ce**, dans les contraintes de mémoire spécifiées par l' *ordre*.

## <a name="fetch_add"></a>Atomic:: fetch_add

Extrait la valeur stockée dans  **\*ce**, puis ajoute une valeur spécifiée à la valeur stockée.

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

Objet *Ty* qui contient la valeur stockée dans  **\*ce** avant l’ajout.

### <a name="remarks"></a>Notes

La `fetch_add` méthode effectue une opération de lecture-modification-écriture pour ajouter atomiquement la *valeur* à la valeur stockée dans  **\*ce**et applique les contraintes de mémoire spécifiées par *ordre*.

## <a name="fetch_and"></a>Atomic:: fetch_and

Effectue une opération de bits and sur une valeur et une valeur existante stockée dans  **\*ce**.

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

La `fetch_and` méthode effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*ce** par une *valeur* and au niveau du bit et la valeur actuelle stockée dans  **\*ce**, dans la mémoire. contraintes spécifiées par *ordre*.

## <a name="fetch_or"></a>Atomic:: fetch_or

Effectue une opération de bits or sur une valeur et une valeur existante stockée dans  **\*ce**.

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

La `fetch_or` méthode effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*ce** par un opérateur de bits or de *valeur* et la valeur actuelle stockée dans  **\*ce**, dans la mémoire. contraintes spécifiées par *ordre*.

## <a name="fetch_sub"></a>Atomic:: fetch_sub

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

La `fetch_sub` méthode effectue une opération de lecture-modification-écriture pour soustraire de manière atomique la *valeur* de la valeur stockée dans  **\*ce**, dans les contraintes de mémoire spécifiées par l' *ordre*.

## <a name="fetch_xor"></a>Atomic:: fetch_xor

Effectue une opération OR exclusive au niveau du bit sur une valeur et une valeur existante stockée dans  **\*ce**.

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

La `fetch_xor` méthode effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*ce** par une *valeur* or exclusive au niveau du bit et la valeur actuelle stockée dans  **\*ce**et applique le contraintes de mémoire spécifiées par *ordre*.

## <a name="is_lock_free"></a>Atomic:: is_lock_free

Spécifie si les opérations atomiques sur  **\*ce** sont sans verrou.

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>Valeur de retour

true si les opérations atomiques sur  **\*ce** sont sans verrou; sinon, false.

### <a name="remarks"></a>Notes

Un type atomique est sans verrou si aucune opération atomique sur ce type n’utilise de verrous.

## <a name="load"></a>Atomic:: Load

Récupère la valeur stockée dans  **\*ce**, dans les contraintes de mémoire spécifiées.

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
`memory_order` La *commande* ne doit `memory_order_release` pas `memory_order_acq_rel`être ou.

### <a name="return-value"></a>Valeur de retour

Valeur récupérée qui est stockée dans  **\*ce**.

## <a name="store"></a>Atomic:: Store

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
`memory_order` Contrainte.

### <a name="remarks"></a>Notes

Cette fonction membre stocke atomiquement la `*this` *valeur* dans, dans les contraintes de mémoire spécifiées par l' *ordre*.

## <a name="see-also"></a>Voir aussi

[\<atomic>](../standard-library/atomic.md)\
[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
