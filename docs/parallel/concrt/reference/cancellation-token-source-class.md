---
title: cancellation_token_source, classe
ms.date: 11/04/2016
f1_keywords:
- cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancellation_token_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::cancel
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::create_linked_source
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_source::get_token
helpviewer_keywords:
- cancellation_token_source class
ms.assetid: 3548b1a0-12b0-4334-95db-4bf57141c066
ms.openlocfilehash: 330473db1011af661e2cfa2c5861987bce786e40
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296785"
---
# <a name="cancellationtokensource-class"></a>cancellation_token_source, classe

La classe `cancellation_token_source` représente la capacité d'annulation d'une opération annulable.

## <a name="syntax"></a>Syntaxe

```
class cancellation_token_source;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[cancellation_token_source](#ctor)|Surchargé. Construit une nouvelle classe `cancellation_token_source`. La source peut être utilisée pour signaler l'annulation d'une opération annulable.|
|[~ cancellation_token_source, destructeur](#dtor)||

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[cancel](#cancel)|Annule le jeton. N'importe quel `task_group`, `structured_task_group` ou `task` qui utilise le jeton sera annulé lors de cet appel et lèvera une exception au point d'interruption suivant.|
|[create_linked_source](#create_linked_source)|Surchargé. Crée une classe `cancellation_token_source` qui est annulée lorsque le jeton fourni est annulé.|
|[get_token](#get_token)|Retourne un jeton d'annulation associé à cette source. Le jeton retourné peut être interrogé pour l'annulation ou fournir un rappel si et quand l'annulation se produit.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[!=, opérateur](#operator_neq)||
|[operator=](#operator_eq)||
|[operator==](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`cancellation_token_source`

## <a name="requirements"></a>Spécifications

**En-tête :** pplcancellation_token.h

**Espace de noms :** concurrency

##  <a name="dtor"></a> ~cancellation_token_source

```
~cancellation_token_source();
```

##  <a name="cancel"></a> Annuler

Annule le jeton. N'importe quel `task_group`, `structured_task_group` ou `task` qui utilise le jeton sera annulé lors de cet appel et lèvera une exception au point d'interruption suivant.

```
void cancel() const;
```

##  <a name="ctor"></a> cancellation_token_source

Construit une nouvelle classe `cancellation_token_source`. La source peut être utilisée pour signaler l'annulation d'une opération annulable.

```
cancellation_token_source();

cancellation_token_source(const cancellation_token_source& _Src);

cancellation_token_source(cancellation_token_source&& _Src);
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>
Objet à copier ou déplacer.

##  <a name="create_linked_source"></a> create_linked_source

Crée une classe `cancellation_token_source` qui est annulée lorsque le jeton fourni est annulé.

```
static cancellation_token_source create_linked_source(
    cancellation_token& _Src);

template<typename _Iter>
static cancellation_token_source create_linked_source(_Iter _Begin, _Iter _End);
```

### <a name="parameters"></a>Paramètres

*_Iter*<br/>
Type d’itérateur.

*_Src*<br/>
Jeton dont l'annulation provoque l'annulation de la source du jeton retourné. Notez que la source du jeton retourné peut également être annulée indépendamment de la source contenue dans ce paramètre.

*_Begin*<br/>
Itérateur de bibliothèque Standard C++ correspondant au début de la plage de jetons à écouter pour l’annulation.

*_End*<br/>
Itérateur de bibliothèque C++ Standard correspondant à la fin de la plage de jetons à écouter pour l’annulation.

### <a name="return-value"></a>Valeur de retour


  `cancellation_token_source` qui est annulée lorsque le jeton fourni par le paramètre `_Src` est annulé.

##  <a name="get_token"></a> get_token

Retourne un jeton d'annulation associé à cette source. Le jeton retourné peut être interrogé pour l'annulation ou fournir un rappel si et quand l'annulation se produit.

```
cancellation_token get_token() const;
```

### <a name="return-value"></a>Valeur de retour

Jeton d'annulation associé à cette source.

##  <a name="operator_neq"></a> operator!=

```
bool operator!= (const cancellation_token_source& _Src) const;
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>
Opérande.

### <a name="return-value"></a>Valeur de retour

##  <a name="operator_eq"></a> operator=

```
cancellation_token_source& operator= (const cancellation_token_source& _Src);

cancellation_token_source& operator= (cancellation_token_source&& _Src);
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>
Opérande.

### <a name="return-value"></a>Valeur de retour

##  <a name="operator_eq_eq"></a> operator==

```
bool operator== (const cancellation_token_source& _Src) const;
```

### <a name="parameters"></a>Paramètres

*_Src*<br/>
Opérande.

### <a name="return-value"></a>Valeur de retour

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
