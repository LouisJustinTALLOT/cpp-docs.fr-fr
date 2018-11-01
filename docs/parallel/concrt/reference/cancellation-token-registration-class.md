---
title: cancellation_token_registration, classe
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration::cancellation_token_registration
helpviewer_keywords:
- cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
ms.openlocfilehash: ca664d78f80a0c335a8669454b1345955aaefcb2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644663"
---
# <a name="cancellationtokenregistration-class"></a>cancellation_token_registration, classe

La classe `cancellation_token_registration` représente une notification de rappel de `cancellation_token`. Quand la méthode `register` sur une classe `cancellation_token` est utilisée pour recevoir une notification relative à la date d'annulation, un objet `cancellation_token_registration` est retourné comme handle au rappel afin que l'appelant puisse demander qu'un rappel spécifique ne soit plus effectué via l'utilisation de la méthode `deregister`.

## <a name="syntax"></a>Syntaxe

```
class cancellation_token_registration;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[cancellation_token_registration](#ctor)||
|[~ cancellation_token_registration, destructeur](#dtor)||

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[!=, opérateur](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`cancellation_token_registration`

## <a name="requirements"></a>Configuration requise

**En-tête :** pplcancellation_token.h

**Espace de noms :** concurrency

##  <a name="dtor"></a> ~ cancellation_token_registration

```
~cancellation_token_registration();
```

##  <a name="ctor"></a> cancellation_token_registration

```
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>
Le `cancellation_token_registration` pour copier ou déplacer.

##  <a name="operator_neq"></a> opérateur ! =

```
bool operator!= (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
`cancellation_token_registration` à comparer.

### <a name="return-value"></a>Valeur de retour

##  <a name="operator_eq"></a> opérateur =

```
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>
Le `cancellation_token_registration` à affecter.

### <a name="return-value"></a>Valeur de retour

##  <a name="operator_eq_eq"></a> opérateur ==

```
bool operator== (const cancellation_token_registration& _Rhs) const;
```

### <a name="parameters"></a>Paramètres

*_Rhs*<br/>
`cancellation_token_registration` à comparer.

### <a name="return-value"></a>Valeur de retour

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
