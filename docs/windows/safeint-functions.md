---
title: SafeInt, fonctions
ms.date: 10/22/2018
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
ms.openlocfilehash: 0cf1418e3bf00c037faaa67de2bc76ad2b7cc5e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578397"
---
# <a name="safeint-functions"></a>SafeInt, fonctions

La Bibliothèque SafeInt fournit plusieurs fonctions que vous pouvez utiliser sans créer d’instance de la [classe SafeInt](../windows/safeint-class.md). Si vous souhaitez empêcher une seule opération mathématique débordements d’entiers, vous pouvez utiliser ces fonctions. Si vous souhaitez protéger plusieurs opérations mathématiques, vous devez créer `SafeInt` objets. Il est plus efficace de créer `SafeInt` objets plutôt que d’utiliser ces fonctions plusieurs fois.

Ces fonctions permettent de comparer ou effectuer des opérations mathématiques sur deux types de paramètres sans avoir à les convertir d’abord vers le même type.

Chacune de ces fonctions a deux types de modèle : `T` et `U`. Chacun de ces types peut être une valeur booléenne, un caractère ou un type intégral. Types intégraux peuvent être signés ou non signés et n’importe quelle taille allant de 8 bits à 64 bits.

> [!NOTE]
> La dernière version de cette bibliothèque se trouve dans [ https://github.com/dcleblanc/SafeInt ](https://github.com/dcleblanc/SafeInt).

## <a name="in-this-section"></a>Dans cette section

Fonction                      | Description
----------------------------- | --------------------------------------------------------------
[SafeAdd](#safeadd)           | Ajoute deux nombres et protège contre le dépassement de capacité.
[SafeCast](#safecast)         | Convertit un type de paramètre à un autre type.
[SafeDivide](#safedivide)     | Divise deux nombres et protège contre la division par zéro.
[SafeEquals](#safeequals), [SafeGreaterThan](#safegreaterthan), [SafeGreaterThanEquals](#safegreaterthanequals), [SafeLessThan](#safelessthan), [SafeLessThanEquals](#safelessthanequals), [ SafeNotEquals](#safenotequals) | Compare deux nombres. Ces fonctions permettent de comparer deux différents types de nombres sans modifier leurs types.
[SafeModulus](#safemodulus)   | Effectue l’opération modulo sur deux nombres.
[SafeMultiply](#safemultiply) | Multiplie deux nombres ensemble et protège contre le dépassement de capacité.
[SafeSubtract](#safesubtract) | Soustrait deux nombres et protège contre le dépassement de capacité.

## <a name="related-sections"></a>Rubriques connexes

Section                                                  | Description
-------------------------------------------------------- | ----------------------------------------------------
[SafeInt](../windows/safeint-class.md)                   | La classe `SafeInt`.
[SafeIntException](../windows/safeintexception-class.md) | La classe d’exception spécifique à la Bibliothèque SafeInt.

## <a name="safeadd"></a>SafeAdd

Ajoute deux nombres d’une manière qui protège contre le dépassement de capacité.

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
[in] Le premier nombre à ajouter. Il doit s’agir de type T.

*u*<br/>
[in] Le deuxième nombre à ajouter. Il doit s’agir de type U.

*Résultat*<br/>
[out] Le paramètre où `SafeAdd` stocke le résultat.

### <a name="return-value"></a>Valeur de retour

**true** si aucune erreur ne se produit ; **false** si une erreur se produit.

## <a name="safecast"></a>SafeCast

Convertit un type de nombre à un autre type.

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>Paramètres

*From*<br/>
[in] Le nombre de la source à convertir. Cela doit être de type `T`.

*To*<br/>
[out] Une référence au nouveau type de nombre. Cela doit être de type `U`.

### <a name="return-value"></a>Valeur de retour

**true** si aucune erreur ne se produit ; **false** si une erreur se produit.

## <a name="safedivide"></a>SafeDivide

Divise deux nombres d’une manière qui protège contre la division par zéro.

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
[in] Le diviseur. Il doit s’agir de type T.

*u*<br/>
[in] Le dividende. Il doit s’agir de type U.

*Résultat*<br/>
[out] Le paramètre où `SafeDivide` stocke le résultat.

### <a name="return-value"></a>Valeur de retour

**true** si aucune erreur ne se produit ; **false** si une erreur se produit.

## <a name="safeequals"></a>SafeEquals

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
[in] Le premier nombre à comparer. Il doit s’agir de type T.

*u*<br/>
[in] Le deuxième nombre à comparer. Il doit s’agir de type U.

### <a name="return-value"></a>Valeur de retour

**true** si *t* et *u* sont égales ; sinon **false**.

### <a name="remarks"></a>Notes

La méthode améliore `==` car `SafeEquals` vous permet de comparer deux différents types de nombres.

## <a name="safegreaterthan"></a>SafeGreaterThan

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
[in] Le premier nombre à comparer. Cela doit être de type `T`.

*u*<br/>
[in] Le deuxième nombre à comparer. Cela doit être de type `U`.

### <a name="return-value"></a>Valeur de retour

**true** si *t* est supérieur à *u*; sinon **false**.

### <a name="remarks"></a>Notes

`SafeGreaterThan` étend l’opérateur de comparaison standard en vous permettant de comparer deux différents types de nombres.

## <a name="safegreaterthanequals"></a>SafeGreaterThanEquals

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
[in] Le premier nombre à comparer. Cela doit être de type `T`.

*u*<br/>
[in] Le deuxième nombre à comparer. Cela doit être de type `U`.

### <a name="return-value"></a>Valeur de retour

**true** si *t* est supérieur ou égal à *u*; sinon **false**.

### <a name="remarks"></a>Notes

`SafeGreaterThanEquals` améliore l’opérateur de comparaison standard, car il vous permet de comparer deux différents types de nombres.

## <a name="safelessthan"></a>SafeLessThan

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
[in] Le premier nombre. Cela doit être de type `T`.

*u*<br/>
[in] Le deuxième nombre. Cela doit être de type `U`.

### <a name="return-value"></a>Valeur de retour

**true** si *t* est inférieure à *u*; sinon **false**.

### <a name="remarks"></a>Notes

Cette méthode améliore l’opérateur de comparaison standard, car `SafeLessThan` vous permet de comparer deux types de nombre.

## <a name="safelessthanequals"></a>SafeLessThanEquals

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
[in] Le premier nombre à comparer. Cela doit être de type `T`.

*u*<br/>
[in] Le deuxième nombre à comparer. Cela doit être de type `U`.

### <a name="return-value"></a>Valeur de retour

**true** si *t* est inférieure ou égale à *u*; sinon **false**.

### <a name="remarks"></a>Notes

`SafeLessThanEquals` étend l’opérateur de comparaison standard en vous permettant de comparer deux différents types de nombres.

## <a name="safemodulus"></a>SafeModulus

Effectue l’opération modulo sur deux nombres.

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
[in] Le diviseur. Cela doit être de type `T`.

*u*<br/>
[in] Le dividende. Cela doit être de type `U`.

*Résultat*<br/>
[out] Le paramètre où `SafeModulus` stocke le résultat.

### <a name="return-value"></a>Valeur de retour

**true** si aucune erreur ne se produit ; **false** si une erreur se produit.

## <a name="safemultiply"></a>SafeMultiply

Multiplie deux nombres ensemble d’une manière qui protège contre le dépassement de capacité.

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
[in] Le premier nombre à multiplier. Cela doit être de type `T`.

*u*<br/>
[in] Le second nombre à multiplier. Cela doit être de type `U`.

*Résultat*<br/>
[out] Le paramètre où `SafeMultiply` stocke le résultat.

### <a name="return-value"></a>Valeur de retour

`true` Si aucune erreur ne se produit ; `false` si une erreur se produit.

## <a name="safenotequals"></a>SafeNotEquals

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
[in] Le premier nombre à comparer. Cela doit être de type `T`.

*u*<br/>
[in] Le deuxième nombre à comparer. Cela doit être de type `U`.

### <a name="return-value"></a>Valeur de retour

**true** si *t* et *u* ne sont pas égales ; sinon **false**.

### <a name="remarks"></a>Notes

La méthode améliore `!=` car `SafeNotEquals` vous permet de comparer deux différents types de nombres.

## <a name="safesubtract"></a>SafeSubtract

Soustrait deux nombres d’une manière qui protège contre le dépassement de capacité.

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
[in] Le premier numéro de la soustraction. Cela doit être de type `T`.

*u*<br/>
[in] Le nombre à soustraire de *t*. Cela doit être de type `U`.

*Résultat*<br/>
[out] Le paramètre où `SafeSubtract` stocke le résultat.

### <a name="return-value"></a>Valeur de retour

**true** si aucune erreur ne se produit ; **false** si une erreur se produit.
