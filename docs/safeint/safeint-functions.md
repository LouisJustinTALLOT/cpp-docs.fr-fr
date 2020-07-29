---
title: SafeInt, fonctions
ms.date: 06/23/2020
ms.topic: reference
f1_keywords:
- SafeInt functions
- SafeAdd
- SafeCast
- SafeDivide
- SafeEquals
- SafeGreaterThan
- SafeGreaterThanEquals
- SafeLessThan
- SafeLessThanEquals
- SafeModulus
- SafeMultiply
- SafeNotEquals
- SafeSubtract
helpviewer_keywords:
- functions, SafeInt
- SafeAdd function
- SafeCast function
- SafeDivide function
- SafeEquals function
- SafeGreaterThan function
- SafeGreaterThanEquals function
- SafeLessThan function
- SafeLessThanEquals function
- SafeModulus function
- SafeMultiply function
- SafeNotEquals function
- SafeSubtract function
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
ms.openlocfilehash: c968601d95403dd63540a7a8ec2190a199fa1c5a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219337"
---
# <a name="safeint-functions"></a>SafeInt, fonctions

La bibliothèque SafeInt fournit plusieurs fonctions que vous pouvez utiliser sans créer d’instance de la [classe SafeInt](safeint-class.md). Vous pouvez utiliser ces fonctions si vous souhaitez protéger une seule opération mathématique contre les dépassements d’entiers. Si vous souhaitez protéger plusieurs opérations mathématiques, vous devez créer des objets `SafeInt`. Il est plus efficace de créer des `SafeInt` objets que d’utiliser ces fonctions plusieurs fois.

Ces fonctions permettent de comparer ou d’effectuer des opérations mathématiques sur deux types de paramètres sans avoir à les convertir vers le même type.

Chacune de ces fonctions dispose de deux types de modèle : `T` et `U`. Chacun de ces types peut être un type booléen, de caractère ou intégral. Les types de données intégral peuvent être signés ou non signés et de toutes tailles, comprises entre 8 bits et 64 bits.

> [!NOTE]
> La dernière version de cette bibliothèque se trouve à l’adresse [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt) .

## <a name="in-this-section"></a>Dans cette section

Fonction                      | Description
----------------------------- | --------------------------------------------------------------
[SafeAdd](#safeadd)           | Ajoute deux nombres et protège contre le dépassement de capacité.
[SafeCast](#safecast)         | Convertit un type de paramètre en un autre type.
[SafeDivide](#safedivide)     | Divise deux nombres et protège contre la division par zéro.
[SafeEquals](#safeequals), [SafeGreaterThan](#safegreaterthan), [SafeGreaterThanEquals](#safegreaterthanequals), [SafeLessThan](#safelessthan), [SafeLessThanEquals](#safelessthanequals), [SafeNotEquals](#safenotequals) | Compare deux nombres. Ces fonctions permettent de comparer deux types de nombres différents sans modifier leurs types.
[SafeModulus](#safemodulus)   | Effectue l’opération de modulo sur deux nombres.
[SafeMultiply](#safemultiply) | Multiplie deux nombres et protège contre le dépassement de capacité.
[SafeSubtract](#safesubtract) | Soustrait deux nombres et protège contre le dépassement de capacité.

## <a name="related-sections"></a>Sections connexes

Section                                                  | Description
-------------------------------------------------------- | ----------------------------------------------------
[SafeInt](safeint-class.md)                   | Classe `SafeInt`.
[SafeIntException](safeintexception-class.md) | La classe d’exception spécifique à la bibliothèque SafeInt.

## <a name="safeadd"></a><a name="safeadd"></a>SafeAdd

Ajoute deux nombres afin de protéger contre le dépassement de capacité.

```cpp
template<typename T, typename U>
inline bool SafeAdd (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Paramètres

*t*<br/>
[in] Premier nombre à ajouter. Il doit être de type T.

*u*<br/>
[in] Deuxième nombre à ajouter. Il doit être de type U.

*result*<br/>
[out] Le paramètre dans lequel `SafeAdd` stocke le résultat.

### <a name="return-value"></a>Valeur de retour

**`true`** Si aucune erreur ne se produit ; **`false`** si une erreur se produit.

## <a name="safecast"></a><a name="safecast"></a>SafeCast

Convertit un type de nombre en un autre type.

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>Paramètres

*From*<br/>
[in] Le nombre de la source à convertir. Il doit être de type `T`.

*To*<br/>
[out] Une référence au nouveau type du nombre. Il doit être de type `U`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si aucune erreur ne se produit ; **`false`** si une erreur se produit.

## <a name="safedivide"></a><a name="safedivide"></a>SafeDivide

Divise deux nombres afin de protéger contre la division par zéro.

```cpp
template<typename T, typename U>
inline bool SafeDivide (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Paramètres

*t*<br/>
[in] Dividende. Il doit être de type T.

*u*<br/>
[in] Diviseur. Il doit être de type U.

*result*<br/>
[out] Le paramètre dans lequel `SafeDivide` stocke le résultat.

### <a name="return-value"></a>Valeur de retour

**`true`** Si aucune erreur ne se produit ; **`false`** si une erreur se produit.

## <a name="safeequals"></a><a name="safeequals"></a>SafeEquals

Compare deux nombres pour déterminer s’ils sont égaux.

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Paramètres

*t*<br/>
[in] Premier nombre à comparer. Il doit être de type T.

*u*<br/>
[in] Deuxième nombre à comparer. Il doit être de type U.

### <a name="return-value"></a>Valeur de retour

**`true`** Si *t* et *u* sont égaux ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La méthode améliore `==` car `SafeEquals` vous permet de comparer deux types de nombres différents.

## <a name="safegreaterthan"></a><a name="safegreaterthan"></a>SafeGreaterThan

Compare deux nombres.

```cpp
template<typename T, typename U>
inline bool SafeGreaterThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Paramètres

*t*<br/>
[in] Premier nombre à comparer. Il doit être de type `T`.

*u*<br/>
[in] Deuxième nombre à comparer. Il doit être de type `U`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si *t* est supérieur à *u*; Sinon, **`false`** .

### <a name="remarks"></a>Notes

`SafeGreaterThan` étend l’opérateur de comparaison régulier en vous permettant de comparer deux types de nombres différents.

## <a name="safegreaterthanequals"></a><a name="safegreaterthanequals"></a>SafeGreaterThanEquals

Compare deux nombres.

```cpp
template <typename T, typename U>
inline bool SafeGreaterThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Paramètres

*t*<br/>
[in] Premier nombre à comparer. Il doit être de type `T`.

*u*<br/>
[in] Deuxième nombre à comparer. Il doit être de type `U`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si *t* est supérieur ou égal à *u*; Sinon, **`false`** .

### <a name="remarks"></a>Notes

`SafeGreaterThanEquals` améliore l’opérateur de comparaison standard en vous permettant de comparer deux types de nombres différents.

## <a name="safelessthan"></a><a name="safelessthan"></a>SafeLessThan

Détermine si un nombre est inférieur à un autre.

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Paramètres

*t*<br/>
[in] Premier nombre. Il doit être de type `T`.

*u*<br/>
dans Deuxième nombre. Il doit être de type `U`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si *t* est inférieur à *u*; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La méthode améliore l’opérateur de comparaison standard car `SafeLessThan` vous permet de comparer deux types de nombres différents.

## <a name="safelessthanequals"></a><a name="safelessthanequals"></a>SafeLessThanEquals

Compare deux nombres.

```cpp
template <typename T, typename U>
inline bool SafeLessThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Paramètres

*t*<br/>
[in] Premier nombre à comparer. Il doit être de type `T`.

*u*<br/>
[in] Deuxième nombre à comparer. Il doit être de type `U`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si *t* est inférieur ou égal à *u*; Sinon, **`false`** .

### <a name="remarks"></a>Notes

`SafeLessThanEquals` étend l’opérateur de comparaison régulier en vous permettant de comparer deux types de nombres différents.

## <a name="safemodulus"></a><a name="safemodulus"></a>SafeModulus

Effectue l’opération de modulo sur deux nombres.

```cpp
template<typename T, typename U>
inline bool SafeModulus (
   const T t,
   const U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Paramètres

*t*<br/>
[in] Diviseur. Il doit être de type `T`.

*u*<br/>
[in] Dividende. Il doit être de type `U`.

*result*<br/>
[out] Le paramètre dans lequel `SafeModulus` stocke le résultat.

### <a name="return-value"></a>Valeur de retour

**`true`** Si aucune erreur ne se produit ; **`false`** si une erreur se produit.

## <a name="safemultiply"></a><a name="safemultiply"></a>SafeMultiply

Multiplie deux nombres afin de protéger contre le dépassement de capacité.

```cpp
template<typename T, typename U>
inline bool SafeMultiply (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Paramètres

*t*<br/>
[in] Premier nombre à multiplier. Il doit être de type `T`.

*u*<br/>
[in] Second nombre à multiplier. Il doit être de type `U`.

*result*<br/>
[out] Le paramètre dans lequel `SafeMultiply` stocke le résultat.

### <a name="return-value"></a>Valeur de retour

**`true`** Si aucune erreur ne se produit ; **`false`** si une erreur se produit.

## <a name="safenotequals"></a><a name="safenotequals"></a>SafeNotEquals

Détermine si deux nombres ne sont pas égaux.

```cpp
template<typename T, typename U>
inline bool SafeNotEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Paramètres

*t*<br/>
[in] Premier nombre à comparer. Il doit être de type `T`.

*u*<br/>
[in] Deuxième nombre à comparer. Il doit être de type `U`.

### <a name="return-value"></a>Valeur de retour

**`true`** Si *t* et *u* ne sont pas égaux ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

La méthode améliore `!=` car `SafeNotEquals` vous permet de comparer deux types de nombres différents.

## <a name="safesubtract"></a><a name="safesubtract"></a>SafeSubtract

Soustrait deux nombres afin de protéger contre le dépassement de capacité.

```cpp
template<typename T, typename U>
inline bool SafeSubtract (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Paramètres

*t*<br/>
[in] Le premier nombre de la soustraction. Il doit être de type `T`.

*u*<br/>
[in] Le nombre à soustraire de *t*. Il doit être de type `U`.

*result*<br/>
[out] Le paramètre dans lequel `SafeSubtract` stocke le résultat.

### <a name="return-value"></a>Valeur de retour

**`true`** Si aucune erreur ne se produit ; **`false`** si une erreur se produit.
