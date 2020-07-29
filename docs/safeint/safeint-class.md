---
title: SafeInt, classe
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeInt
- SafeInt::SafeInt
- SafeInt.SafeInt
helpviewer_keywords:
- SafeInt class
- SafeInt class, constructor
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
ms.openlocfilehash: 97d81401cfd01d6d39457a9d63c39bc25901128e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219350"
---
# <a name="safeint-class"></a>SafeInt, classe

Étend les primitifs entiers afin d’éviter les débordements d’entiers et permet de comparer les différents types d’entiers.

> [!NOTE]
> La dernière version de la bibliothèque SafeInt se trouve à l’emplacement [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt) . Pour utiliser la bibliothèque SafeInt, Clonez les référentiel et`#include "SafeInt.hpp"`

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>
class SafeInt;
```

### <a name="parameters"></a>Paramètres

| Modèle  |  Description |
|--------|------------|
| T         |  Le type d’entier ou de paramètre booléen remplacé par `SafeInt`. |
| E         |  Un type de données énumérées qui définit la stratégie de gestion des erreurs. |
| U         |  Le type d’entier ou de paramètre booléen pour l’opérande secondaire. |

| Paramètre  |  Description |
|---------|-----------------|
| *rhs*      |  [in] Un paramètre d’entrée qui représente la valeur à droite de l’opérateur dans plusieurs fonctions autonomes. |
| *i*        |  [in] Un paramètre d’entrée qui représente la valeur à droite de l’opérateur dans plusieurs fonctions autonomes. |
| *bits*     |  [in] Un paramètre d’entrée qui représente la valeur à droite de l’opérateur dans plusieurs fonctions autonomes. |

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

| Nom                          |  Description |
|---------------------------|--------------------|
| [SafeInt :: SafeInt](#safeint)  |  Constructeur par défaut. |

### <a name="assignment-operators"></a>Opérateurs d'assignation

| Nom  |  Syntaxe |
|----|---------|
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const U& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const T& rhs) throw()` |
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()` |

### <a name="casting-operators"></a>Opérateurs de casting

| Nom              |  Syntaxe |
|------|---------------------------------|
| bool              |  `operator bool() throw()` |
| char              |  `operator char() const` |
| signed char       |  `operator signed char() const` |
| unsigned char     |  `operator unsigned char() const` |
| __int16           |  `operator __int16() const` |
| unsigned __int16  |  `operator unsigned __int16() const` |
| __int32           |  `operator __int32() const` |
| unsigned __int32  |  `operator unsigned __int32() const` |
| long              |  `operator long() const` |
| unsigned long     |  `operator unsigned long() const` |
| __int64           |  `operator __int64() const` |
| unsigned __int64  |  `operator unsigned __int64() const` |
| wchar_t           |  `operator wchar_t() const` |

### <a name="comparison-operators"></a>Opérateurs de comparaison

| Nom  |  Syntaxe |
|----|----------------|
| \<     |  `template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()` |
| \<     |  `bool operator< (SafeInt<T,E> rhs) const throw()` |
| \>=    |  `template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()` |
| \>=    |  `Bool operator>= (SafeInt<T,E> rhs) const throw()` |
| \>     |  `template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()` |
| \>     |  `Bool operator> (SafeInt<T,E> rhs) const throw()` |
| \<=    |  `template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()` |
| \<=    |  `bool operator<= (SafeInt<T,E> rhs) const throw()` |
| ==    |  `template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()` |
| ==    |  `bool operator== (bool rhs) const throw()` |
| ==    |  `bool operator== (SafeInt<T,E> rhs) const throw()` |
| !=    |  `template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()` |
| !=    |  `bool operator!= (bool b) const throw()` |
| !=    |  `bool operator!= (SafeInt<T,E> rhs) const throw()` |

### <a name="arithmetic-operators"></a>Opérateurs arithmétiques

| Nom  |  Syntaxe |
|----|--------------|
| +     |  `const SafeInt<T,E>& operator+ () const throw()` |
| -     |  `SafeInt<T,E> operator- () const` |
| ++    |  `SafeInt<T,E>& operator++ ()` |
| --    |  `SafeInt<T,E>& operator-- ()` |
| %     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const` |
| %     |  `SafeInt<T,E> operator% (SafeInt<T,E> rhs) const` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)` |
| \*     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const` |
| \*     |  `SafeInt<T,E> operator* (SafeInt<T,E> rhs) const` |
| \*=    |  `SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)` |
| /     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const` |
| /     |  `SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const` |
| /=    |  `SafeInt<T,E>& operator/= (SafeInt<T,E> i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)` |
| +     |  `SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const` |
| +     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const` |
| +=    |  `SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)` |
| -     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const` |
| -     |  `SafeInt<T,E> operator- (SafeInt<T,E> rhs) const` |
| -=    |  `SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)` |

### <a name="logical-operators"></a>Opérateurs logiques

| Nom     |  Syntaxe |
|------|--------------|
| !        |  `bool operator !() const throw()` |
| ~        |  `SafeInt<T,E> operator~ () const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()` |
| &        |  `SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()` |
| &        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()` |
| &=       |  `SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()` |
| ^        |  `SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()` |
| ^        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()` |
| ^=       |  `SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()` |
| &#124;   |  `SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()` |
| &#124;   |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()` |
| &#124;=  |  `SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()` |

## <a name="remarks"></a>Notes

La classe `SafeInt` protège contre les dépassements sur les entiers dans les opérations mathématiques. Par exemple, vous pouvez ajouter deux entiers 8 bits, l’un avec une valeur de 200 et l’autre avec une valeur de 100. L’opération mathématique correcte serait 100 + 200 = 300. Toutefois, en raison de la limitation de l’entier 8 bits, le bit supérieur sera perdu et le compilateur retournera 44 (300 - 2<sup>8</sup>) comme résultat. Toute opération dépendant de cette équation mathématique générera un comportement inattendu.

La classe `SafeInt` vérifie si un débordement arithmétique se produit ou si le code tente de diviser par zéro. Dans les deux cas, la classe appelle le gestionnaire d’erreurs pour avertir le programme de ce problème potentiel.

Cette classe vous permet également de comparer deux différents types d’entiers, dès lors qu’il s’agit d’objets `SafeInt`. En règle générale, lorsque vous effectuez une comparaison, vous devez d’abord convertir les nombres pour qu’ils soient du même type. La conversion d’un nombre à un autre type requiert généralement des vérifications pour s’assurer qu’aucune perte de données ne s’est produite.

La table des opérateurs dans cette rubrique répertorie les opérateurs mathématiques et de comparaison pris en charge par la classe `SafeInt`. La plupart des opérateurs mathématiques retournent un objet `SafeInt` de type `T`.

Des opérations de comparaison entre un `SafeInt` et un type intégral peuvent être réalisées dans les deux sens. Par exemple, `SafeInt<int>(x) < y` et `y> SafeInt<int>(x)` sont valides et retournent le même résultat.

De nombreux opérateurs binaires ne prennent pas en charge l’utilisation de deux `SafeInt` types différents. L’opérateur `&` en est un exemple. `SafeInt<T, E> & int`est pris en charge, mais `SafeInt<T, E> & SafeInt<U, E>` n’est pas. Dans ce dernier exemple, le compilateur ne sait pas quel type de paramètre retourner. L’une des solutions à ce problème consiste à effectuer un cast en retour du deuxième paramètre vers le type de base. En utilisant les mêmes paramètres, cela peut être effectué avec `SafeInt<T, E> & (U)SafeInt<U, E>`.

> [!NOTE]
> Pour toutes les opérations au niveau du bit, les deux paramètres doivent être de la même taille. Si les tailles sont différentes, le compilateur générera une exception [ASSERT](../mfc/reference/diagnostic-services.md#assert). Il n’est pas garanti que les résultats de cette opération soient exacts. Pour résoudre ce problème, effectuez un cast du plus petit paramètre jusqu’à ce qu’il ait la même taille que le paramètre de plus grande taille.

Pour les opérateurs de décalage, le décalage d’un plus grand nombre de bits qu’il en existe pour le type de modèle lève une exception ASSERT. Cela n’aura aucun effet en mode Release. Les opérateurs de décalage peuvent mélanger deux types de paramètres SafeInt, car le type de retour est identique au type d’origine. Le nombre situé à droite de l’opérateur indique uniquement le nombre de bits à décaler.

Lorsque vous effectuez une comparaison logique avec un objet SafeInt, la comparaison est strictement arithmétique. Prenons par exemple ces expressions :

- `SafeInt<uint>((uint)~0) > -1`

- `((uint)~0) > -1`

La première instruction correspond à **`true`** , mais la deuxième instruction correspond à **`false`** . La négation d’opération de bits de 0 est 0xFFFFFFFF. Dans la deuxième instruction, l’opérateur de comparaison par défaut compare 0xFFFFFFFF à 0xFFFFFFFF et les considère comme égaux. L’opérateur de comparaison de la classe `SafeInt` se rend compte que le deuxième paramètre est négatif, tandis que le premier paramètre n’est pas signé. Par conséquent, bien que la représentation binaire soit identique, l’opérateur logique `SafeInt` se rend compte que l’entier non signé est supérieur à -1.

Soyez prudent lorsque vous utilisez la classe `SafeInt` avec l’opérateur ternaire `?:`. Examinez la ligne de code suivante.

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : -1;
```

Le compilateur la convertit ainsi :

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);
```

Si `flag` est **`false`** , le compilateur lève une exception au lieu d’assigner la valeur de-1 à `x` . Par conséquent, pour éviter ce comportement, le code approprié à utiliser est la ligne suivante.

```cpp
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;
```

`T` et `U` peuvent avoir un type booléen, un type de caractère ou un type entier. Les types d’entier peuvent être signés ou non signés et de toutes tailles, comprises entre 8 bits et 64 bits.

> [!NOTE]
> Bien que la classe `SafeInt` accepte tous les types d’entier, elle effectue ses tâches plus efficacement avec les types non signés.

`E` est le mécanisme de gestion des erreurs utilisé par `SafeInt`. Deux mécanismes de gestion des erreurs sont fournis avec la bibliothèque SafeInt. La stratégie par défaut est `SafeIntErrorPolicy_SafeIntException`, qui lève une exception [SafeIntException Class](safeintexception-class.md) lorsqu’une erreur se produit. L’autre stratégie est `SafeIntErrorPolicy_InvalidParameter`, qui arrête le programme si une erreur se produit.

Deux options sont disponibles pour personnaliser la stratégie d’erreur. La première option consiste à définir le paramètre `E` lorsque vous créez un `SafeInt`. Utilisez cette option lorsque vous souhaitez modifier la stratégie de gestion des erreurs pour un seul `SafeInt`. L’autre option consiste à définir _SAFEINT_DEFAULT_ERROR_POLICY comme votre classe de gestion des erreurs personnalisée avant d’inclure la bibliothèque `SafeInt`. Utilisez cette option pour modifier la stratégie par défaut de gestion des erreurs pour toutes les instances de la classe `SafeInt` de votre code.

> [!NOTE]
> Une classe personnalisée qui gère les erreurs à partir de la bibliothèque SafeInt ne doit pas retourner le contrôle au code qui a appelé le gestionnaire d’erreurs. Une fois le gestionnaire d’erreurs appelé, le résultat de l' `SafeInt` opération ne peut pas être approuvé.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SafeInt`

## <a name="requirements"></a>Spécifications

**En-tête :** SafeInt. HPP
> [!NOTE]
> La dernière version de cette bibliothèque se trouve à l’adresse [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt) . Clonez la bibliothèque et incluez SafeInt. hpp pour utiliser la bibliothèque SafeInt.
> Préférez ce référentiel GitHub à <SafeInt. h>. Il s’agit d’une version moderne de <SafeInt. h> qui comprend un petit nombre de correctifs de bogues, utilise des fonctionnalités modernes de C++, ce qui se traduit par un code plus efficace et est portable sur n’importe quelle plateforme utilisant les compilateurs GCC, Clang ou Intel.

### <a name="example"></a>Exemple

```c
#include "SafeInt.hpp" // set path to your clone of the SafeInt GitHub repo (https://github.com/dcleblanc/SafeInt)

int main()
{
    int divisor = 3;
    int dividend = 6;
    int result;

    bool success = SafeDivide(dividend, divisor, result); // result = 2
    success = SafeDivide(dividend, 0, result); // expect fail. result isn't modified.
}
```

**Espace de noms :** aucun

## <a name="safeintsafeint"></a><a name="safeint"></a>SafeInt :: SafeInt

Construit un objet `SafeInt`.

```cpp
SafeInt() throw

SafeInt (const T& i) throw ()

SafeInt (bool b) throw ()

template <typename U>
SafeInt (const SafeInt <U, E>& u)

I template <typename U>
SafeInt (const U& i)
```

### <a name="parameters"></a>Paramètres

`i`<br/>
[in] La valeur du nouvel objet `SafeInt`. Il doit s’agir d’un paramètre de type T ou U, en fonction du constructeur.

`b`<br/>
[in] La valeur booléenne du nouvel objet `SafeInt`.

`u`<br/>
[in] Un `SafeInt` de type U. Le nouvel objet `SafeInt` aura la même valeur que le type *U*, mais sera de type T.

`U`Type des données stockées dans le `SafeInt` . Il peut s’agit d’un type booléen, d’un type de caractère ou d’un type entier. S’il s’agit d’un type entier, il peut être signé ou non signé et être compris entre 8 et 64 bits.

### <a name="remarks"></a>Notes

Le paramètre d’entrée pour le constructeur, *i* ou *u*, doit être un type booléen, de caractère ou entier. S’il s’agit d’un autre type de paramètre, la `SafeInt` classe appelle [static_assert](../cpp/static-assert.md) pour indiquer un paramètre d’entrée non valide.

Les constructeurs qui utilisent le type de modèle `U` convertissent automatiquement le paramètre d’entrée du type spécifié par `T`. La classe `SafeInt` convertit les données sans aucune perte de données. Il signale au gestionnaire d’erreurs `E` s’il ne peut pas convertir les données en type `T` sans perte de données.

Si vous créez un `SafeInt` à partir d’un paramètre booléen, vous devez initialiser la valeur immédiatement. Vous ne pouvez pas construire un `SafeInt` à l’aide du code `SafeInt<bool> sb;` . Cela générera une erreur de compilation.
