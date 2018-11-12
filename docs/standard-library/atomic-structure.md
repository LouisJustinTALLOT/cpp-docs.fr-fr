---
title: atomic, structure
ms.date: 04/20/2018
f1_keywords:
- atomic/std::atomic
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
ms.openlocfilehash: 258812f033d34f040d96847581d6f51692a933b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590058"
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
|[atomic::operator Ty](#op_ty)|Lit et retourne la valeur stockée. ([atomic::load](#load))|
|[atomic::operator =](#op_eq)|Utilise une valeur spécifiée pour remplacer la valeur stockée. ([atomic::store](#store))|
|[atomic::operator ++](#op_inc)|Incrémente la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.|
|[atomic::operator +=](#op_add_eq)|Ajoute une valeur spécifiée à la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.|
|[atomic::operator--](#op_dec)|Décrémente la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.|
|[atomic::operator-=](#op_sub_eq)|Soustrait une valeur spécifiée de la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.|
|[atomic::operator & =](#op_and_eq)|Effectue une opération de bits et sur une valeur spécifiée et la valeur stockée. Utilisé uniquement par les spécialisations intégrales.|
|[atomic::operator&#124;=](#op_or_eq)|Effectue une opération de bits ou sur une valeur spécifiée et la valeur stockée. Utilisé uniquement par les spécialisations intégrales.|
|[atomic::operator ^ =](#op_xor_eq)|Exécute un OR exclusif ou sur une valeur spécifiée et la valeur stockée. Utilisé uniquement par les spécialisations intégrales.|
|**Fonctions**||
|[compare_exchange_strong](#compare_exchange_strong)|Effectue une *atomic_compare_and_exchange* opération sur **cela** et retourne le résultat.|
|[compare_exchange_weak](#compare_exchange_weak)|Effectue un *weak_atomic_compare_and_exchange* opération sur **cela** et retourne le résultat.|
|[fetch_add](#fetch_add)|Ajoute une valeur spécifiée à la valeur stockée.|
|[fetch_and](#fetch_and)|Effectue une opération de bits et sur une valeur spécifiée et la valeur stockée.|
|[fetch_or](#fetch_or)|Effectue une opération de bits ou sur une valeur spécifiée et la valeur stockée.|
|[fetch_sub](#fetch_sub)|Soustrait une valeur spécifiée de la valeur stockée.|
|[fetch_xor](#fetch_xor)|Exécute un OR exclusif ou sur une valeur spécifiée et la valeur stockée.|
|[is_lock_free](#is_lock_free)|Spécifie si les opérations atomiques sur **cela** sont *sans verrouillage*. Un type atomique est *sans verrou* si aucune opération atomique sur ce type utilise un verrou.|
|[Charge](#load)|Lit et retourne la valeur stockée.|
|[store](#store)|Utilise une valeur spécifiée pour remplacer la valeur stockée.|

## <a name="remarks"></a>Notes

Le type *Ty* doit être *COPIABLE*. Autrement dit, à l’aide de [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) pour copier ses octets doit produire une valide *Ty* objet dont la valeur est égale à l’objet d’origine. Le [compare_exchange_weak](#compare_exchange_weak) et [compare_exchange_strong](#compare_exchange_strong) utilisation de fonctions membres [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) pour déterminer si deux *Ty* valeurs sont égaux. Ces fonctions n’utilisera pas un *Ty*-défini `operator==`. Les fonctions membres de `atomic` utiliser `memcpy` pour copier les valeurs de type *Ty*.

Une spécialisation partielle, **atomique\<Ty \* >** , existe pour tous les types de pointeur. La spécialisation permet d’ajouter un décalage à la valeur de pointeur gérée ou de lui soustraire un décalage. Les opérations arithmétiques prennent un argument de type `ptrdiff_t` et ajustent cet argument en fonction de la taille de *Ty* pour être cohérent avec l’arithmétique d’adresse ordinaire.

Une spécialisation existe pour chaque type intégral sauf **bool**. Chaque spécialisation fournit un ensemble complet de méthodes pour les opérations atomiques arithmétiques et logiques.

||||
|-|-|-|
|**atomique\<char >**|**atomique\<signé char >**|**atomique\<unsigned char >**|
|**atomique\<char16_t >**|**atomique\<char32_t >**|**atomique\<wchar_t >**|
|**atomique\<court >**|**atomique\<unsigned short >**|**atomique\<int >**|
|**atomique\<unsigned int >**|**atomique\<long >**|**atomique\<unsigned long >**|
|**atomique\<longue >**|**atomique\<unsigned long long >**|

Les spécialisations intégrales sont dérivées des types `atomic_integral` correspondants. Par exemple, **atomique\<unsigned int >** est dérivée de `atomic_uint`.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<atomic >

**Espace de noms :** std

## <a name="atomic"></a> atomic::atomic

Construit un objet atomique.

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>Paramètres

*Valeur*<br/>
Valeur d’initialisation.

### <a name="remarks"></a>Notes

Objets atomiques ne peut pas être copiés ou déplacés.

Les objets qui sont des instanciations du atomique\<*Ty*> peut être initialisé uniquement par le constructeur qui prend un argument de type *Ty* et ne pas à l’aide de l’initialisation d’agrégat. Toutefois, les objets atomic_integral peuvent être initialisés qu’à l’aide de l’initialisation d’agrégat.

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="op_ty"></a> atomic::operator *Ty*

L’opérateur pour le type spécifié au modèle atomique\<*Ty*>. Récupère la valeur stockée dans  **\*cela**.

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>Notes

Cet opérateur s’applique le `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_eq"></a> atomic::operator =

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

*Valeur*<br/>
Un *Ty* objet.

### <a name="return-value"></a>Valeur de retour

Retourne *valeur*.

## <a name="op_inc"></a> atomic::operator ++

Incrémente la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>Valeur de retour

Les deux premiers opérateurs retournent la valeur incrémentée ; les deux derniers opérateurs retournent la valeur avant l’incrémentation. Les opérateurs utilisent le `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_add_eq"></a> atomic::operator +=

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

*Valeur*<br/>
Une valeur de type intégral ou pointeur.

### <a name="return-value"></a>Valeur de retour

Un *Ty* objet qui contient le résultat de l’addition.

### <a name="remarks"></a>Notes

Cet opérateur utilise le `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_dec"></a> atomic::operator--

Décrémente la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>Valeur de retour

Les deux premiers opérateurs retournent la valeur décrémentée ; les deux derniers opérateurs retournent la valeur avant la décrémentation. Les opérateurs utilisent le `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_sub_eq"></a> atomic::operator-=

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

*Valeur*<br/>
Une valeur de type intégral ou pointeur.

### <a name="return-value"></a>Valeur de retour

Un *Ty* objet qui contient le résultat de la soustraction.

### <a name="remarks"></a>Notes

Cet opérateur utilise le `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_and_eq"></a> atomic::operator & =

Effectue une opération de bits et sur une valeur spécifiée et la valeur stockée de  **\*cela**. Utilisé uniquement par les spécialisations intégrales.

```cpp
atomic<Ty>::operator&= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator&= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Valeur*<br/>
Une valeur de type *Ty*.

### <a name="return-value"></a>Valeur de retour

Le résultat de l’opérateur de bits et.

### <a name="remarks"></a>Notes

Cet opérateur effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*cela** avec une opération de bits et de *valeur* et la valeur actuelle qui est stockée dans  **\*cela**, aux contraintes de la `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_or_eq"></a> atomic::operator&#124;=

Effectue une opération de bits ou sur une valeur spécifiée et la valeur stockée de  **\*cela**. Utilisé uniquement par les spécialisations intégrales.

```cpp
atomic<Ty>::operator|= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator|= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Valeur*<br/>
Une valeur de type *Ty*.

### <a name="return-value"></a>Valeur de retour

Le résultat de l’opérateur de bits ou.

### <a name="remarks"></a>Notes

Cet opérateur effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*cela** avec une opération de bits or *valeur* et la valeur actuelle qui est stockée dans  **\*cela**, aux contraintes de la `memory_order_seq_cst` [memory_order](atomic-enums.md) contraintes.

## <a name="op_xor_eq"></a> atomic::operator ^ =

Exécute un OR exclusif ou selon une valeur spécifiée et la valeur stockée de  **\*cela**. Utilisé uniquement par les spécialisations intégrales.

```cpp
atomic<Ty>::operator^= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator^= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Paramètres

*Valeur*<br/>
Une valeur de type *Ty*.

### <a name="return-value"></a>Valeur de retour

Le résultat de l’OR exclusif ou.

### <a name="remarks"></a>Notes

Cet opérateur effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*cela** avec un exclusif au niveau du bit ou de *valeur* et la valeur actuelle qui est stockée dans  **\*cela**, aux contraintes de la `memory_order_seq_cst` [memory_order](atomic-enums.md) contraintes.

## <a name="compare_exchange_strong"></a> atomic::compare_exchange_strong

Effectue une opération de comparaison et d’échange atomique sur  **\*cela**.

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

*Exp*<br/>
Une valeur de type *Ty*.

*Valeur*<br/>
Une valeur de type *Ty*.

*Order1*<br/>
Première `memory_order` argument.

*Order2*<br/>
Deuxième argument `memory_order`.

### <a name="return-value"></a>Valeur de retour

Un **bool** qui indique le résultat de la comparaison de valeur.

### <a name="remarks"></a>Notes

Cette opération de comparaison et d’échange atomique compare la valeur qui est stockée dans  **\*cela** avec *Exp*. Si les valeurs sont égales, l’opération remplace la valeur qui est stockée dans  **\*cela** avec *valeur* en utilisant une opération de lecture-modification-écriture et en appliquant les contraintes d’ordre de mémoire qui sont spécifié par *Order1*. Si les valeurs ne sont pas égales, l’opération utilise la valeur qui est stockée dans  **\*cela** pour remplacer *Exp* et applique les contraintes d’ordre de mémoire qui sont spécifiées par *Order2* .

Les surcharges qui n’ont pas une seconde `memory_order` utiliser implicite *Order2* qui repose sur la valeur de *Order1*. Si *Order1* est `memory_order_acq_rel`, *Order2* est `memory_order_acquire`. Si *Order1* est `memory_order_release`, *Order2* est `memory_order_relaxed`. Dans tous les autres cas, *Order2* est égal à *Order1*.

Pour les surcharges qui acceptent deux `memory_order` paramètres, la valeur de *Order2* ne doit pas être `memory_order_release` ou `memory_order_acq_rel`et ne doit pas être supérieure à la valeur de *Order1*.

## <a name="compare_exchange_weak"></a> atomic::compare_exchange_weak

Effectue une opération de comparaison et d’échange atomique faible sur  **\*cela**.

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

*Exp*<br/>
Une valeur de type *Ty*.

*Valeur*<br/>
Une valeur de type *Ty*.

*Order1*<br/>
Première `memory_order` argument.

*Order2*<br/>
Deuxième argument `memory_order`.

### <a name="return-value"></a>Valeur de retour

Un **bool** qui indique le résultat de la comparaison de valeur.

### <a name="remarks"></a>Notes

Cette opération de comparaison et d’échange atomique compare la valeur qui est stockée dans  **\*cela** avec *Exp*. Si les valeurs sont égales, l’opération remplace la valeur qui est stockée dans  **\*cela** avec*valeur* en utilisant une opération de lecture-modification-écriture et en appliquant les contraintes d’ordre de mémoire qui sont spécifié par *Order1*. Si les valeurs ne sont pas égales, l’opération utilise la valeur qui est stockée dans  **\*cela** pour remplacer *Exp* et applique les contraintes d’ordre de mémoire qui sont spécifiées par *Order2* .

Compare un faible atomique et opération d’échange effectue un échange si les valeurs comparées sont égales. Si les valeurs ne sont pas égales, l’opération n’est pas garantie d’échange.

Les surcharges qui n’ont pas une seconde `memory_order` utiliser implicite *Order2* qui repose sur la valeur de *Order1*. Si *Order1* est `memory_order_acq_rel`, *Order2* est `memory_order_acquire`. Si *Order1* est `memory_order_release`, *Order2* est `memory_order_relaxed`. Dans tous les autres cas, *Order2* est égal à *Order1*.

Pour les surcharges qui acceptent deux `memory_order` paramètres, la valeur de *Order2* ne doit pas être `memory_order_release` ou `memory_order_acq_rel`et ne doit pas être supérieure à la valeur de *Order1*.

## <a name="exchange"></a> atomic::Exchange

Utilise une valeur spécifiée pour remplacer la valeur stockée de  **\*cela**.

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

*Valeur*<br/>
Une valeur de type *Ty*.

*Commande*<br/>
`memory_order`

### <a name="return-value"></a>Valeur de retour

La valeur stockée de  **\*cela** avant l’échange.

### <a name="remarks"></a>Notes

Cette opération effectue une opération de lecture-modification-écriture à utiliser *valeur* pour remplacer la valeur est stockée dans  **\*cela**, respectant les contraintes de mémoire qui sont spécifiées par  *Commande*.

## <a name="fetch_add"></a> atomic::fetch_add

Extrait la valeur stockée dans  **\*cela**, puis ajoute une valeur spécifiée à la valeur stockée.

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

*Valeur*<br/>
Une valeur de type *Ty*.

*Commande*<br/>
`memory_order`

### <a name="return-value"></a>Valeur de retour

Un *Ty* objet qui contient la valeur stockée dans  **\*cela** avant l’ajout.

### <a name="remarks"></a>Notes

Le `fetch_add` méthode effectue une opération de lecture-modification-écriture à ajouter de manière atomique *valeur* à la valeur stockée dans  **\*cela**et applique les contraintes de mémoire qui sont spécifiées par *Ordre*.

## <a name="fetch_and"></a> atomic::fetch_and

Effectue une opération de bits et sur une valeur et une valeur existante stockée dans  **\*cela**.

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

*Valeur*<br/>
Une valeur de type *Ty*.

*Commande*<br/>
`memory_order`

### <a name="return-value"></a>Valeur de retour

Un *Ty* objet qui contient le résultat de l’opérateur de bits et.

### <a name="remarks"></a>Notes

Le `fetch_and` méthode effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*cela** avec une opération de bits et de *valeur* et la valeur actuelle qui est stockée dans  **\*cela**, respectant les contraintes de mémoire qui sont spécifiées par *ordre*.

## <a name="fetch_or"></a> atomic::fetch_or

Effectue une opération de bits ou sur une valeur et une valeur existante stockée dans  **\*cela**.

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

*Valeur*<br/>
Une valeur de type *Ty*.

*Commande*<br/>
`memory_order`

### <a name="return-value"></a>Valeur de retour

Un *Ty* objet qui contient le résultat de l’opérateur de bits ou.

### <a name="remarks"></a>Notes

Le `fetch_or` méthode effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*cela** avec une opération de bits or *valeur* et la valeur actuelle qui est stockée dans  **\*cela**, respectant les contraintes de mémoire qui sont spécifiées par *ordre*.

## <a name="fetch_sub"></a> atomic::fetch_sub

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

*Valeur*<br/>
Une valeur de type *Ty*.

*Commande*<br/>
`memory_order`

### <a name="return-value"></a>Valeur de retour

Un *Ty* objet qui contient le résultat de la soustraction.

### <a name="remarks"></a>Notes

Le `fetch_sub` méthode effectue une opération de lecture-modification-écriture à soustraire de manière atomique *valeur* à partir de la valeur stockée dans  **\*cela**, respectant les contraintes de mémoire qui sont spécifiées par *Ordre*.

## <a name="fetch_xor"></a> atomic::fetch_xor

Exécute un OR exclusif ou selon une valeur et une valeur existante stockée dans  **\*cela**.

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

*Valeur*<br/>
Une valeur de type *Ty*.

*Commande*<br/>
`memory_order`

### <a name="return-value"></a>Valeur de retour

Un *Ty* objet qui contient le résultat de l’OR exclusif ou.

### <a name="remarks"></a>Notes

Le `fetch_xor` méthode effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*cela** avec un exclusif au niveau du bit ou de *valeur* et la valeur actuelle stockée dans  **\*cela**et applique les contraintes de mémoire qui sont spécifiées par *ordre*.

## <a name="is_lock_free"></a> atomic::is_lock_free

Spécifie si les opérations atomiques sur  **\*cela** sont sans verrou.

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>Valeur de retour

True si atomique opérations sur  **\*cela** sont verrou libre ; sinon, false.

### <a name="remarks"></a>Notes

Un type atomique est sans verrou si aucune opération atomique sur ce type n’utilise un verrou.

## <a name="load"></a> atomic::Load

Récupère la valeur stockée dans  **\*cela**, respectant les contraintes de mémoire spécifié.

```cpp
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const volatile noexcept;
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const noexcept;
```

### <a name="parameters"></a>Paramètres

*Commande*<br/>
`memory_order` *Commande* ne doit pas être `memory_order_release` ou `memory_order_acq_rel`.

### <a name="return-value"></a>Valeur de retour

La valeur récupérée qui est stockée dans  **\*cela**.

## <a name="store"></a> atomic::Store

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

*Valeur*<br/>
Un *Ty* objet.

*Commande*<br/>
Un `memory_order` contrainte.

### <a name="remarks"></a>Notes

Cette fonction membre stocke atomiquement *valeur* dans `*this`, respectant les contraintes de mémoire qui sont spécifiées par *ordre*.

## <a name="see-also"></a>Voir aussi

[\<atomic>](../standard-library/atomic.md)<br/>
[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
