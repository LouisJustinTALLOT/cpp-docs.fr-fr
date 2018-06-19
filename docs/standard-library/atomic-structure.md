---
title: atomic, structure | Microsoft Docs
ms.custom: ''
ms.date: 04/20/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- atomic/std::atomic
dev_langs:
- C++
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7308c127bebd2185429509315ebafb3d83a7efea
ms.sourcegitcommit: b0d5557dbb57128da560a0a4634312ec4a050a90
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2018
ms.locfileid: "34476105"
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
|[atomic::operator =](#op_sub_eq)|Soustrait une valeur spécifiée de la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.|
|[atomic::operator & =](#op_and_eq)|Effectue une opération de bits et sur une valeur spécifiée et la valeur stockée. Utilisé uniquement par les spécialisations intégrales.|
|[atomic::operator&#124;=](#op_or_eq)|Effectue une opération de bits ou sur une valeur spécifiée et la valeur stockée. Utilisé uniquement par les spécialisations intégrales.|
|[atomic::operator ^ =](#op_xor_eq)|Effectue un exclusif au niveau du bit ou sur une valeur spécifiée et la valeur stockée. Utilisé uniquement par les spécialisations intégrales.|
|**Fonctions**||
|[compare_exchange_strong](#compare_exchange_strong)|Effectue une *atomic_compare_and_exchange* opération sur **cela** et retourne le résultat.|
|[compare_exchange_weak](#compare_exchange_weak)|Effectue un *weak_atomic_compare_and_exchange* opération sur **cela** et retourne le résultat.|
|[fetch_add](#fetch_add)|Ajoute une valeur spécifiée à la valeur stockée.|
|[fetch_and](#fetch_and)|Effectue une opération de bits et sur une valeur spécifiée et la valeur stockée.|
|[fetch_or](#fetch_or)|Effectue une opération de bits ou sur une valeur spécifiée et la valeur stockée.|
|[fetch_sub](#fetch_sub)|Soustrait une valeur spécifiée de la valeur stockée.|
|[fetch_xor](#fetch_xor)|Effectue un exclusif au niveau du bit ou sur une valeur spécifiée et la valeur stockée.|
|[is_lock_free](#is_lock_free)|Spécifie si les opérations atomiques sur **cela** sont *verrou libre*. Un type atomique est *sans verrou* si aucune opération atomique sur ce type utilise un verrou.|
|[Charge](#load)|Lit et retourne la valeur stockée.|
|[store](#store)|Utilise une valeur spécifiée pour remplacer la valeur stockée.|

## <a name="remarks"></a>Notes

Le type *Ty* doit être *simplement être copiés*. Autrement dit, à l’aide de [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) pour copier ses octets doit produire une valide *Ty* objet valeur est égale à l’objet d’origine. Le [compare_exchange_weak](#compare_exchange_weak) et [compare_exchange_strong](#compare_exchange_strong) utilisation de fonctions membres [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) pour déterminer si deux *Ty* valeurs sont égales. Ces fonctions n’utilisent pas un *Ty*-défini **opérateur ==**. Les fonctions membres de **atomique** utiliser **memcpy** pour copier les valeurs de type *Ty*.

Une spécialisation partielle, **atomique\<Ty \* >** , existe pour tous les types de pointeur. La spécialisation permet d’ajouter un décalage à la valeur de pointeur gérée ou de lui soustraire un décalage. Les opérations arithmétiques prennent un argument de type **ptrdiff_t** et ajuster cet argument en fonction de la taille de *Ty* pour être cohérent avec l’adresse ordinaire arithmétique.

Une spécialisation existe pour chaque type intégral sauf **bool**. Chaque spécialisation fournit un ensemble complet de méthodes pour les opérations atomiques arithmétiques et logiques.

||||
|-|-|-|
|**atomique\<char >**|**atomique\<signé char >**|**atomique\<unsigned char >**|
|**atomique\<char16_t >**|**atomique\<char32_t >**|**atomique\<wchar_t >**|
|**atomique\<court >**|**atomique\<court non signé >**|**atomique\<int >**|
|**atomique\<int non signé >**|**atomique\<longue >**|**atomique\<long non signé >**|
|**atomique\<long >**|**atomique\<long long non signé >**|

Les spécialisations intégrale sont dérivées de correspondant **atomic_integral** types. Par exemple, **atomique\<int non signé >** est dérivée de **atomic_uint**.

## <a name="requirements"></a>Spécifications

**En-tête :** \<atomique >

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

Les objets qui sont des instanciations du atomique\<*Ty*> peut être initialisée uniquement par le constructeur qui accepte un argument de type *Ty* et ne pas à l’aide de l’initialisation d’agrégats. Toutefois, les objets atomic_integral peuvent être initialisés qu’à l’aide de l’initialisation d’agrégats.

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="op_ty"></a> atomic::operator *Ty*

L’opérateur pour le type spécifié pour le modèle, atomique\<*Ty*>. Récupère la valeur stockée dans  **\*cela**.

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>Notes

Cet opérateur s’applique le **memory_order_seq_cst** [memory_order](atomic-enums.md).

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
A *Ty* objet.

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

Les deux premiers opérateurs retournent la valeur incrémentée ; les deux derniers opérateurs retournent la valeur avant l’incrément. Les opérateurs utilisent le **memory_order_seq_cst** [memory_order](atomic-enums.md).

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

A *Ty* objet qui contient le résultat de l’addition.

### <a name="remarks"></a>Notes

Cet opérateur utilise le **memory_order_seq_cst** [memory_order](atomic-enums.md).

## <a name="op_dec"></a> atomic::operator--

Décrémente la valeur stockée. Utilisé uniquement par les spécialisations intégrales et de pointeur.

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>Valeur de retour

Les deux premiers opérateurs retournent la valeur décrémentée ; les deux derniers opérateurs retournent la valeur avant la décrémentation. Les opérateurs utilisent le **memory_order_seq_cst** [memory_order](atomic-enums.md).

## <a name="op_sub_eq"></a> atomic::operator =

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

A *Ty* objet qui contient le résultat de la soustraction.

### <a name="remarks"></a>Notes

Cet opérateur utilise le **memory_order_seq_cst** [memory_order](atomic-enums.md).

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

Cet opérateur effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*cela** avec une opération de bits et de *valeur* et la valeur actuelle qui est stockée dans  **\*cela**, dans des limites de la **memory_order_seq_cst** [memory_order](atomic-enums.md).

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

Cet opérateur effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*cela** avec au niveau du bit ou de *valeur* et la valeur actuelle qui est stockée dans  **\*cela**, dans des limites de la **memory_order_seq_cst** [memory_order](atomic-enums.md) contraintes.

## <a name="op_xor_eq"></a> atomic::operator ^ =

Effectue un exclusif au niveau du bit ou sur une valeur spécifiée et la valeur stockée de  **\*cela**. Utilisé uniquement par les spécialisations intégrales.

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

Le résultat de l’exclusif au niveau du bit ou.

### <a name="remarks"></a>Notes

Cet opérateur effectue une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*cela** avec un exclusif au niveau du bit ou de *valeur* et la valeur actuelle qui est stockée dans  **\*cela**, dans des limites de la **memory_order_seq_cst** [memory_order](atomic-enums.md) contraintes.

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
Premier argument **memory_order**.

*Order2*<br/>
Deuxième **memory_order** argument.

### <a name="return-value"></a>Valeur de retour

A **bool** qui indique le résultat de la comparaison de valeurs.

### <a name="remarks"></a>Notes

Cette opération de comparaison et d’échange atomique compare la valeur est stockée dans  **\*cela** avec *Exp*. Si les valeurs sont égales, l’opération remplace la valeur qui est stockée dans  **\*cela** avec *valeur* en utilisant une opération de lecture-modification-écriture et en appliquant des contraintes d’ordre de mémoire qui sont spécifié par *Order1*. Si les valeurs ne sont pas égales, l’opération utilise la valeur qui est stockée dans  **\*cela** remplacer *Exp* et applique les contraintes d’ordre de mémoire qui sont spécifiées par *Order2* .

Les surcharges qui n’ont pas un deuxième **memory_order** utiliser implicite *Order2* qui repose sur la valeur de *Order1*. Si *Order1* est **memory_order_acq_rel**, *Order2* est **memory_order_acquire**. Si *Order1* est **memory_order_release**, *Order2* est **memory_order_relaxed**. Dans tous les autres cas, *Order2* est égal à *Order1*.

Pour les surcharges qui acceptent deux **memory_order** paramètres, la valeur de *Order2* ne doit pas être **memory_order_release** ou **memory_order_acq_rel**et ne doit pas être supérieur à la valeur de *Order1*.

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
Premier argument **memory_order**.

*Order2*<br/>
Deuxième **memory_order** argument.

### <a name="return-value"></a>Valeur de retour

A **bool** qui indique le résultat de la comparaison de valeurs.

### <a name="remarks"></a>Notes

Cette opération de comparaison et d’échange atomique compare la valeur est stockée dans  **\*cela** avec *Exp*. Si les valeurs sont égales, l’opération remplace la valeur qui est stockée dans  **\*cela** avec*valeur* en utilisant une opération de lecture-modification-écriture et en appliquant des contraintes d’ordre de mémoire qui sont spécifié par *Order1*. Si les valeurs ne sont pas égales, l’opération utilise la valeur qui est stockée dans  **\*cela** remplacer *Exp* et applique les contraintes d’ordre de mémoire qui sont spécifiées par *Order2* .

Un faible atomique compare et opération d’échange effectue un échange si les valeurs comparées sont égales. Si les valeurs ne sont pas égales, l’opération n’est pas garantie pour effectuer un échange.

Les surcharges qui n’ont pas un deuxième **memory_order** utiliser implicite *Order2* qui repose sur la valeur de *Order1*. Si *Order1* est **memory_order_acq_rel**, *Order2* est **memory_order_acquire**. Si *Order1* est **memory_order_release**, *Order2* est **memory_order_relaxed**. Dans tous les autres cas, *Order2* est égal à *Order1*.

Pour les surcharges qui acceptent deux **memory_order** paramètres, la valeur de *Order2* ne doit pas être **memory_order_release** ou **memory_order_acq_rel**et ne doit pas être supérieur à la valeur de *Order1*.

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
Une énumération **memory_order**.

### <a name="return-value"></a>Valeur de retour

La valeur stockée de  **\*cela** avant l’échange.

### <a name="remarks"></a>Notes

Cette opération effectue une opération de lecture-modification-écriture à utiliser *valeur* pour remplacer la valeur est stockée dans  **\*cela**, aux contraintes de mémoire qui sont spécifiées par  *Commande*.

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
Une énumération **memory_order**.

### <a name="return-value"></a>Valeur de retour

A *Ty* objet qui contient la valeur stockée dans  **\*cela** avant l’ajout.

### <a name="remarks"></a>Notes

Le **fetch_add** méthode exécute une opération de lecture-modification-écriture pour ajouter de manière atomique *valeur* à la valeur stockée dans  **\*cela**et s’applique à la mémoire les contraintes sont spécifiées par *commande*.

## <a name="fetch_and"></a> atomic::fetch_and

Effectue une opération de bits et sur une valeur et une valeur existante qui est stockée dans  **\*cela**.

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
Une énumération **memory_order**.

### <a name="return-value"></a>Valeur de retour

A *Ty* objet qui contient le résultat de l’opérateur de bits et.

### <a name="remarks"></a>Notes

Le **fetch_and** méthode exécute une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*cela** avec une opération de bits et de *valeur* et en cours valeur qui est stockée dans  **\*cela**, aux contraintes de mémoire qui sont spécifiées par *commande*.

## <a name="fetch_or"></a> atomic::fetch_or

Effectue une opération de bits ou sur une valeur et une valeur existante qui est stockée dans  **\*cela**.

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
Une énumération **memory_order**.

### <a name="return-value"></a>Valeur de retour

A *Ty* objet qui contient le résultat de l’opérateur de bits ou.

### <a name="remarks"></a>Notes

Le **fetch_or** méthode exécute une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*cela** avec au niveau du bit ou de *valeur* et la valeur actuelle qui est stocké dans  **\*cela**, aux contraintes de mémoire qui sont spécifiées par *commande*.

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
Une énumération **memory_order**.

### <a name="return-value"></a>Valeur de retour

A *Ty* objet qui contient le résultat de la soustraction.

### <a name="remarks"></a>Notes

Le **fetch_sub** méthode exécute une opération de lecture-modification-écriture à soustraire de manière atomique *valeur* à partir de la valeur stockée dans  **\*cela**, au sein de la mémoire les contraintes sont spécifiées par *commande*.

## <a name="fetch_xor"></a> atomic::fetch_xor

Effectue un exclusif au niveau du bit ou sur une valeur et une valeur existante qui est stockée dans  **\*cela**.

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
Une énumération **memory_order**.

### <a name="return-value"></a>Valeur de retour

A *Ty* objet qui contient le résultat de l’exclusif au niveau du bit ou.

### <a name="remarks"></a>Notes

Le **fetch_xor** méthode exécute une opération de lecture-modification-écriture pour remplacer la valeur stockée de  **\*cela** avec un exclusif au niveau du bit ou de *valeur* et le valeur actuelle qui est stockée dans  **\*cela**et applique les contraintes de mémoire qui sont spécifiées par *commande*.

## <a name="is_lock_free"></a> atomic::is_lock_free

Spécifie si les opérations atomiques sur  **\*cela** sont libres de verrou.

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>Valeur de retour

True si atomique opérations sur  **\*cela** sont verrou libre ; sinon, false.

### <a name="remarks"></a>Notes

Un type atomique est libre de verrou si aucune des opérations atomiques sur ce type n’utilisent des verrous.

## <a name="load"></a> atomic::Load

Récupère la valeur stockée dans  **\*cela**, aux contraintes de mémoire spécifiée.

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
Une énumération **memory_order**. *Commande* ne doit pas être **memory_order_release** ou **memory_order_acq_rel**.

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
A *Ty* objet.

*Commande*<br/>
A **memory_order** contrainte.

### <a name="remarks"></a>Notes

Cette fonction membre stocke de manière atomique *valeur* dans `*this`, aux contraintes de mémoire qui sont spécifiées par *commande*.

## <a name="see-also"></a>Voir aussi

[\<atomic>](../standard-library/atomic.md)<br/>
[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
