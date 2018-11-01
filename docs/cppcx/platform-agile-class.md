---
title: Platform::Agile, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
helpviewer_keywords:
- Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
ms.openlocfilehash: 9350d94fdff615056fca193d654b2bb001d78d72
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471199"
---
# <a name="platformagile-class"></a>Platform::Agile, classe

Représente un objet qui a MashalingBehavior=Standard en tant qu’objet agile, ce qui réduit considérablement les risques d’exception de thread d’exécution. `Agile<T>` permet à l’objet non agile d’appeler ou d’être appelé par le même thread ou un thread différent. Pour plus d’informations, consultez [thread et Marshaling](../cppcx/threading-and-marshaling-c-cx.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class Agile;
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Nom de type de la classe non agile.

### <a name="remarks"></a>Notes

La plupart des classes dans le Runtime Windows est agile. Un objet agile peut appeler, ou être appelé par, un objet intra-processus ou hors processus dans le même thread ou un autre thread. Si un objet n’est pas agile, encapsulez l’objet non agile dans un objet `Agile<T>` agile. L’objet `Agile<T>` peut ensuite être marshalé, et l’objet non agile sous-jacent peut être utilisé.

La classe `Agile<T>` est une classe C++ native standard qui nécessite `agile.h`. Elle représente l’objet non agile et le *contexte*de l’objet Agile. Le contexte spécifie le modèle de thread et le comportement de marshaling d’un objet agile. Le système d’exploitation utilise le contexte pour déterminer comment marshaler un objet.

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Agile::Agile](#ctor)|Initialise une nouvelle instance de la classe Agile.|
|[Agile::~Agile, destructeur](#dtor)|Détruit l'instance actuelle de la classe Agile.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Agile::Get](#get)|Retourne un handle vers l’objet représenté par l’objet Agile actif.|
|[Agile::GetAddressOf](#getaddressof)|Réinitialise l’objet Agile actif, puis retourne l’adresse d’un handle vers un objet de type `T`.|
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|Retourne l'adresse d'un handle vers l'objet représenté par l'objet Agile actif.|
|[Agile::Release](#release)|Ignore l'objet et le contexte sous-jacent de l'objet Agile actif.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Agile::operator->](#operator-arrow)|Récupère un handle vers l’objet représenté par l’objet Agile actif.|
|[Agile::operator=](#operator-assign)|Assigne la valeur spécifiée à l’objet Agile actif.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Object`

`Agile`

### <a name="requirements"></a>Configuration requise

**Minimum de client pris en charge :** Windows 8

**Minimum de serveur pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**En-tête :** agile.h

## <a name="ctor"></a>  Agile::Agile, constructeur

Initialise une nouvelle instance de la classe Agile.

## <a name="syntax"></a>Syntaxe

```cpp
Agile();
Agile(T^ object);
Agile(const Agile<T>& object);
Agile(Agile<T>&& object);
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type spécifié par le paramètre de nom de type de modèle.

*object*<br/>
Dans la deuxième version de ce constructeur, objet utilisé pour initialiser une nouvelle instance Agile. Dans la troisième version, l'objet qui est copié vers la nouvelle instance Agile. Dans la quatrième version, objet qui est déplacé vers la nouvelle instance Agile.

### <a name="remarks"></a>Notes

La première version de ce constructeur est le constructeur par défaut. La deuxième version initialise la classe d'instance Agile de l'objet spécifié par le paramètre `object`. La troisième version est le constructeur de copie. La quatrième version est le constructeur de déplacement. Ce constructeur ne peut pas lever d'exceptions.

## <a name="dtor"></a>  Agile :: ~ Agile, destructeur

Détruit l'instance actuelle de la classe Agile.

## <a name="syntax"></a>Syntaxe

```cpp
~Agile();
```

### <a name="remarks"></a>Notes

Ce destructeur libère aussi l’objet représenté par l’objet Agile actuel.

## <a name="get"></a>   Agile::Get, méthode

Retourne un handle vers l’objet représenté par l’objet Agile actif.

## <a name="syntax"></a>Syntaxe

```cpp
T^ Get() const;
```

### <a name="return-value"></a>Valeur de retour

Handle vers l’objet représenté par l’objet Agile actif.

Le type de la valeur de retour est en réalité un type interne non divulgué. Un moyen pratique pour contenir la valeur de retour est pour l’assigner à une variable est déclarée avec le **automatique** mot clé de déduction de type. Par exemple, `auto x = myAgileTvariable->Get();`.

## <a name="getaddressof"></a>  Agile::getaddressof, méthode

Réinitialise l’objet Agile actif, puis retourne l’adresse d’un handle vers un objet de type `T`.

## <a name="syntax"></a>Syntaxe

```cpp
T^* GetAddressOf() throw();
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type spécifié par le paramètre de nom de type de modèle.

### <a name="return-value"></a>Valeur de retour

Adresse d’un handle vers un objet de type `T`.

### <a name="remarks"></a>Notes

Cette opération libère la représentation actuelle d’un objet de type `T`, le cas échéant, réinitialise les membres de données de l’objet Agile, acquiert le contexte de thread actuel, puis retourne l’adresse d’une variable handle-to-object qui peut représenter un objet non agile. Pour provoquer une instance de la classe Agile représenter un objet, utilisez l’opérateur d’assignation ([Agile::operator =](#operator-assign)) pour assigner l’objet à l’instance de la classe Agile.

## <a name="getaddressofforinout"></a>  Agile::getaddressofforinout, méthode

Retourne l'adresse d'un handle vers l'objet représenté par l'objet Agile actif.

## <a name="syntax"></a>Syntaxe

```cpp
T^* GetAddressOfForInOut()  throw();
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type spécifié par le paramètre de nom de type de modèle.

### <a name="return-value"></a>Valeur de retour

Adresse d'un handle vers l'objet représenté par l'objet Agile actif.

### <a name="remarks"></a>Notes

Cette opération acquiert le contexte de thread actuel et retourne l'adresse d'un handle vers l'objet sous-jacent.

## <a name="release"></a>  Agile::Release, méthode

Ignore l'objet et le contexte sous-jacent de l'objet Agile actif.

## <a name="syntax"></a>Syntaxe

```cpp
void Release() throw();
```

### <a name="remarks"></a>Notes

L'objet et le contexte sous-jacent de l'objet Agile actif sont ignorés, s'ils existent, et la valeur de l'objet Agile est alors définie sur null.

## <a name="operator-arrow"></a>  Agile::operator -&gt; opérateur

Récupère un handle vers l’objet représenté par l’objet Agile actif.

## <a name="syntax"></a>Syntaxe

```cpp
T^ operator->() const throw();
```

### <a name="return-value"></a>Valeur de retour

Handle vers l’objet représenté par l’objet Agile actif.

Cet opérateur retourne un type interne non divulgué. Un moyen pratique pour contenir la valeur de retour est pour l’assigner à une variable est déclarée avec le **automatique** mot clé de déduction de type.

## <a name="operator-assign"></a>  Agile::operator =, opérateur

Assigne l'objet spécifié à l'objet Agile actuel.

## <a name="syntax"></a>Syntaxe

```cpp
Agile<T> operator=( T^ object ) throw();
Agile<T> operator=( const Agile<T>& object ) throw();
Agile<T> operator=( Agile<T>&& object ) throw();
T^ operator=( IUnknown* lp ) throw();
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type spécifié par le nom de type du modèle.

*object*<br/>
L'objet ou le handle vers un objet qui est copié ou déplacé vers l'objet Agile actuel.

*LP*<br/>
Le pointeur d'interface IUnknown d'un objet.

### <a name="return-value"></a>Valeur de retour

Handle d'un objet de type `T`

### <a name="remarks"></a>Notes

La première version de l'opérateur d'assignation copie un handle vers un type référence à l'objet Agile actuel. La deuxième version copie une référence à un type Agile dans l'objet Agile actuel. La troisième version déplace un type Agile vers l'objet Agile actuel. La quatrième version déplace un pointeur vers un objet COM de l'objet Agile actuel.

L'opération d'assignation applique automatiquement le contexte de l'objet Agile actuel.

## <a name="see-also"></a>Voir aussi

[Plateforme Namespace](platform-namespace-c-cx.md)