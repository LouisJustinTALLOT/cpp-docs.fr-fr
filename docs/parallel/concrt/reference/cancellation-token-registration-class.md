---
description: 'En savoir plus sur : classe cancellation_token_registration'
title: cancellation_token_registration, classe
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration::cancellation_token_registration
helpviewer_keywords:
- cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
ms.openlocfilehash: 1901e5132a9bad6849b1b00a6be63caf9afc9170
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172139"
---
# <a name="cancellation_token_registration-class"></a>cancellation_token_registration, classe

La classe `cancellation_token_registration` représente une notification de rappel de `cancellation_token`. Quand la méthode `register` sur une classe `cancellation_token` est utilisée pour recevoir une notification relative à la date d'annulation, un objet `cancellation_token_registration` est retourné comme handle au rappel afin que l'appelant puisse demander qu'un rappel spécifique ne soit plus effectué via l'utilisation de la méthode `deregister`.

## <a name="syntax"></a>Syntaxe

```cpp
class cancellation_token_registration;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[cancellation_token_registration](#ctor)||
|[Destructeur ~ cancellation_token_registration](#dtor)||

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur ! =](#operator_neq)||
|[opérateur =](#operator_eq)||
|[opérateur = =](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`cancellation_token_registration`

## <a name="requirements"></a>Spécifications

**En-tête :** pplcancellation_token. h

**Espace de noms :** concurrence

## <a name="cancellation_token_registration"></a><a name="dtor"></a> ~ cancellation_token_registration

```cpp
~cancellation_token_registration();
```

## <a name="cancellation_token_registration"></a><a name="ctor"></a> cancellation_token_registration

```cpp
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>
`cancellation_token_registration`À copier ou à déplacer.

## <a name="operator"></a><a name="operator_neq"></a> opérateur ! =

```cpp
bool operator!= (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
`cancellation_token_registration` à comparer.

### <a name="return-value"></a>Valeur renvoyée

## <a name="operator"></a><a name="operator_eq"></a> opérateur =

```cpp
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>
`cancellation_token_registration`À assigner.

### <a name="return-value"></a>Valeur renvoyée

## <a name="operator"></a><a name="operator_eq_eq"></a> opérateur = =

```cpp
bool operator== (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
`cancellation_token_registration` à comparer.

### <a name="return-value"></a>Valeur renvoyée

## <a name="see-also"></a>Voir aussi

[Espace de noms d’accès concurrentiel](concurrency-namespace.md)
