---
title: SafeInt, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 75c5e4df92cf23198d7225dfe337a5c82ecf5596
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609202"
---
# <a name="safeint-class"></a>SafeInt, classe

Étend les primitives entières afin d’éviter les débordements d’entiers et vous permet de comparer les différents types d’entiers.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>
class SafeInt;
```

### <a name="parameters"></a>Paramètres

|Modèle|Description|
|--------------|-----------------|
|T|Le type d’entier ou un paramètre booléen qui **SafeInt** remplace.|
|E|Type de données énuméré qui définit la stratégie de gestion d’erreur.|
|U|Le type d’entier ou un paramètre booléen pour l’opérande secondaire.|

|Paramètre|Description|
|---------------|-----------------|
|[in] *rhs*|Un paramètre d’entrée qui représente la valeur sur le côté droit de l’opérateur dans plusieurs fonctions autonomes.|
|[in] *je*|Un paramètre d’entrée qui représente la valeur sur le côté droit de l’opérateur dans plusieurs fonctions autonomes.|
|[in] *bits*|Un paramètre d’entrée qui représente la valeur sur le côté droit de l’opérateur dans plusieurs fonctions autonomes.|

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[SafeInt::SafeInt](../windows/safeint-safeint.md)|Constructeur par défaut.|

### <a name="assignment-operators"></a>Opérateurs d'assignation

|Name|Syntaxe|
|----------|------------|
|=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const U& rhs)`|
|=|`SafeInt<T,E>& operator= (const T& rhs) throw()`|
|=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)`|
|=|`SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()`|

### <a name="casting-operators"></a>Opérateurs de casting

|Name|Syntaxe|
|----------|------------|
|bool|`operator bool() throw()`|
|char|`operator char() const`|
|signed char|`operator signed char() const`|
|unsigned char|`operator unsigned char() const`|
|__int16|`operator __int16() const`|
|unsigned __int16|`operator unsigned __int16() const`|
|__int32|`operator __int32() const`|
|unsigned __int32|`operator unsigned __int32() const`|
|long|`operator long() const`|
|unsigned long|`operator unsigned long() const`|
|__int64|`operator __int64() const`|
|unsigned __int64|`operator unsigned __int64() const`|
|wchar_t|`operator wchar_t() const`|

### <a name="comparison-operators"></a>Opérateurs de comparaison

|Name|Syntaxe|
|----------|------------|
|<|`template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()`|
|<|`bool operator< (SafeInt<T,E> rhs) const throw()`|
|>=|`template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()`|
|>=|`Bool operator>= (SafeInt<T,E> rhs) const throw()`|
|>|`template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()`|
|>|`Bool operator> (SafeInt<T,E> rhs) const throw()`|
|<=|`template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()`|
|<=|`bool operator<= (SafeInt<T,E> rhs) const throw()`|
|==|`template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()`|
|==|`bool operator== (bool rhs) const throw()`|
|==|`bool operator== (SafeInt<T,E> rhs) const throw()`|
|!=|`template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()`|
|!=|`bool operator!= (bool b) const throw()`|
|!=|`bool operator!= (SafeInt<T,E> rhs) const throw()`|

### <a name="arithmetic-operators"></a>Opérateurs arithmétiques

|Name|Syntaxe|
|----------|------------|
|+|`const SafeInt<T,E>& operator+ () const throw()`|
|-|`SafeInt<T,E> operator- () const`|
|++|`SafeInt<T,E>& operator++ ()`|
|--|`SafeInt<T,E>& operator-- ()`|
|%|`template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const`|
|%|`SafeInt<T,E> operator% (SafeInt<T,E> rhs) const`|
|%=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)`|
|%=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)`|
|*|`template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const`|
|*|`SafeInt<T,E> operator* (SafeInt<T,E> rhs) const`|
|*=|`SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)`|
|*=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)`|
|*=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)`|
|/|`template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const`|
|/|`SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const`|
|/=|`SafeInt<T,E>& operator/= (SafeInt<T,E> i)`|
|/=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)`|
|/=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)`|
|+|`SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const`|
|+|`template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const`|
|+=|`SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)`|
|+=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)`|
|+=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)`|
|-|`template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const`|
|-|`SafeInt<T,E> operator- (SafeInt<T,E> rhs) const`|
|-=|`SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)`|
|-=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)`|
|-=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)`|

### <a name="logical-operators"></a>Opérateurs logiques

|Name|Syntaxe|
|----------|------------|
|!|`bool operator !() const throw()`|
|~|`SafeInt<T,E> operator~ () const throw()`|
|<<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()`|
|<<|`template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()`|
|<<=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()`|
|<<=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()`|
|>>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()`|
|>>|`template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()`|
|>>=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()`|
|>>=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()`|
|&|`SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()`|
|&|`template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()`|
|&=|`SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()`|
|&=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()`|
|&=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()`|
|^|`SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()`|
|^|`template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()`|
|^=|`SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()`|
|^=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()`|
|^=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()`|
|&#124;|`SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()`|
|&#124;|`template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()`|
|&#124;=|`SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()`|
|&#124;=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()`|
|&#124;=|`template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()`|

## <a name="remarks"></a>Notes

Le **SafeInt** classe protège contre le dépassement d’entier dans des opérations mathématiques. Par exemple, envisagez d’ajouter deux entiers 8 bits : une a une valeur de 200 et la deuxième a une valeur de 100. L’opération mathématique correcte serait 100 + 200 = 300. Toutefois, en raison de la limite de l’entier 8 bits, le bit supérieur seront perdu et le compilateur renverra une 44 (300-2<sup>8</sup>) comme résultat. Toute opération qui dépend de cette équation mathématique générera un comportement inattendu.

Le **SafeInt** classe vérifie si un débordement arithmétique se produit ou si le code tente de diviser par zéro. Dans les deux cas, la classe appelle le Gestionnaire d’erreurs pour avertir le programme de ce problème.

Cette classe vous permet également de comparer deux différents types d’entiers, qu’elles sont **SafeInt** objets. En règle générale, lorsque vous effectuez une comparaison, vous devez d’abord convertir les nombres pour être du même type. Conversion d’un nombre à un autre type souvent requiert des vérifications pour vous assurer qu’il n’existe aucune perte de données.

La table des opérateurs dans cette rubrique répertorie les opérateurs mathématiques et de comparaison pris en charge par le **SafeInt** classe. Opérateurs mathématiques plus retournent un **SafeInt** objet de type `T`.

Opérations de comparaison entre une **SafeInt** et un type intégral peut être effectué dans les deux sens. Par exemple, les deux `SafeInt<int>(x) < y` et `y> SafeInt<int>(x)` sont valides et retournera le même résultat.

De nombreux opérateurs binaires ne prennent pas en charge l’aide de deux **SafeInt** types. Un exemple de ceci est le `&` opérateur. `SafeInt<T, E> & int` est pris en charge, mais `SafeInt<T, E> & SafeInt<U, E>` n’est pas. Dans ce dernier exemple, le compilateur ne sait pas quel type de paramètre à retourner. Une solution à ce problème consiste à effectuer un cast de la deuxième paramètre vers le type de base. En utilisant les mêmes paramètres, cela est possible avec `SafeInt<T, E> & (U)SafeInt<U, E>`.

> [!NOTE]
> Pour toutes les opérations au niveau du bit, les deux paramètres doivent être la même taille. Si les tailles sont différentes, le compilateur générera un [ASSERT](../mfc/reference/diagnostic-services.md#assert) exception. Les résultats de cette opération ne peut pas être garanties exacte. Pour résoudre ce problème, effectuez un cast du plus petit paramètre jusqu'à ce qu’il est la même taille que le paramètre supérieure.

Pour les opérateurs de décalage, le décalage de bits plus qu’il en existe pour le type de modèle lèvera une exception de ASSERT. Cela n’aura aucun effet en mode release. Il est possible pour les opérateurs de décalage de mélange des deux types de paramètres de SafeInt, car le type de retour est le même que le type d’origine. Le nombre situé à droite de l’opérateur indique uniquement le nombre de bits de décalage.

Lorsque vous effectuez une comparaison logique avec un objet SafeInt, la comparaison est strictement arithmétique. Par exemple, considérez ces expressions :

- `SafeInt<uint>((uint)~0) > -1`

- `((uint)~0) > -1`

La première instruction se résout en **true**, mais la deuxième instruction correspond à **false**. La négation au niveau du bit 0 est 0xFFFFFFFF. Dans la deuxième instruction, l’opérateur de comparaison par défaut compare 0xFFFFFFFF à 0xFFFFFFFF et les considère comme égales. L’opérateur de comparaison pour le **SafeInt** classe se rend compte que le deuxième paramètre est négatif, tandis que le premier paramètre n’est pas signé. Par conséquent, bien que la représentation binaire est identique, la **SafeInt** opérateur logique se rend compte que l’entier non signé est supérieur à -1.

Soyez prudent lorsque vous utilisez le **SafeInt** classe avec le `?:` opérateur ternaire. Envisagez la ligne de code suivante.

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : -1;
```

Le compilateur convertit à ceci :

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);
```

Si `flag` est **false**, le compilateur lève une exception au lieu d’affecter la valeur -1 à `x`. Par conséquent, pour éviter ce comportement, le code approprié à utiliser est la ligne suivante.

```cpp
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;
```

`T` et `U` peut avoir un type booléen, type de caractère ou type entier. L’entier types peuvent être signés ou non signés et n’importe quelle taille allant de 8 bits à 64 bits.

> [!NOTE]
> Bien que le **SafeInt** classe accepte n’importe quel type d’entier, il effectue plus efficacement avec les types non signés.

`E` est le mécanisme de gestion des erreurs qui **SafeInt** utilise. Deux mécanismes de gestion des erreurs sont fournis avec la Bibliothèque SafeInt. La stratégie par défaut est `SafeIntErrorPolicy_SafeIntException`, qui lève une [SafeIntException, classe](../windows/safeintexception-class.md) exception lorsqu’une erreur se produit. L’autre stratégie est `SafeIntErrorPolicy_InvalidParameter`, ce qui arrête le programme si une erreur se produit.

Il existe deux options pour personnaliser la stratégie d’erreur. La première option consiste à définir le paramètre `E` lorsque vous créez un **SafeInt**. Utilisez cette option lorsque vous souhaitez modifier la gestion de stratégie pour un seul d’erreur **SafeInt**. L’autre option consiste à définir _SAFEINT_DEFAULT_ERROR_POLICY à votre classe de gestion des erreurs personnalisée avant d’inclure le **SafeInt** bibliothèque. Utilisez cette option lorsque vous souhaitez modifier la stratégie pour toutes les instances de gestion d’erreur par défaut le **SafeInt** classe dans votre code.

> [!NOTE]
> Une classe personnalisée qui gère les erreurs à partir de la Bibliothèque SafeInt ne doit pas retourner de contrôle au code qui a appelé le Gestionnaire d’erreurs. Une fois que le Gestionnaire d’erreurs est appelée, le résultat de la **SafeInt** opération ne peut pas être approuvée.

## <a name="requirements"></a>Configuration requise

**En-tête :** safeint.h

**Namespace :** msl::utilities

## <a name="see-also"></a>Voir aussi

[Bibliothèque SafeInt](../windows/safeint-library.md)  
[SafeIntException Class](../windows/safeintexception-class.md)