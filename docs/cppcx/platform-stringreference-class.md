---
title: Platform::StringReference, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::StringReference::StringReference
- VCCORLIB/Platform::StringReference::Data
- VCCORLIB/Platform::StringReference::Length
- VCCORLIB/Platform::StringReference::GetHSTRING
- VCCORLIB/Platform::StringReference::GetString
ms.assetid: 2d09c7ec-0f16-458e-83ed-7225a1b9221e
ms.openlocfilehash: 09b15a1530661ce537c9d2aab333a1a17fa52ff9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498382"
---
# <a name="platformstringreference-class"></a>Platform::StringReference, classe

Type d'optimisation que vous pouvez utiliser pour passer des données de type chaîne des paramètres d'entrée `Platform::String^` à d'autres méthodes avec un minimum d'opérations de copie.

## <a name="syntax"></a>Syntaxe

```cpp
class StringReference
```

### <a name="remarks"></a>Notes

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[StringReference::StringReference](#ctor)|Deux constructeurs pour créer des instances de `StringReference`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[StringReference::Data](#data)|Retourne des données de type chaîne en tant que tableau de valeurs char16.|
|[StringReference::Length](#length)|Retourne le nombre de caractères de la chaîne.|
|[StringReference::GetHSTRING](#gethstring)|Retourne des données de type chaîne en tant que HSTRING.|
|[StringReference::GetString](#getstring)|Retourne des données de type chaîne en tant que `Platform::String^`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[StringReference::operator =](#operator-assign)|Assigne une `StringReference` à une nouvelle instance de `StringReference` .|
|[Stringreference::operator](#operator-call)|Convertit une `StringReference` en une `Platform::String^`.|

### <a name="requirements"></a>Configuration requise

**Minimum de client pris en charge :** Windows 8

**Minimum de serveur pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**En-tête :** vccorlib.h

## <a name="data"></a>  Stringreference::Data, méthode

Retourne le contenu de ce `StringReference` sous forme de tableau de valeurs char16.

### <a name="syntax"></a>Syntaxe

```cpp
const ::default::char16 * Data() const;
```

### <a name="return-value"></a>Valeur de retour

Tableau de caractères de texte UNICODE char16.

## <a name="gethstring"></a>  Stringreference::gethstring, méthode

Retourne le contenu de la chaîne en tant que `__abi_HSTRING`.

### <a name="syntax"></a>Syntaxe

```cpp
__abi_HSTRING GetHSTRING() const;
```

### <a name="return-value"></a>Valeur de retour

`__abi_HSTRING` contenant les données de type chaîne.

### <a name="remarks"></a>Notes

## <a name="getstring"></a>  Stringreference::GetString, méthode

Retourne le contenu de la chaîne en tant que `Platform::String^`.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(no_release_return) __declspec(no_refcount)
    ::Platform::String^ GetString() const;
```

### <a name="return-value"></a>Valeur de retour

`Platform::String^` contenant les données de type chaîne.

## <a name="length"></a>  Stringreference::Length, méthode

Retourne le nombre de caractères de la chaîne.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned int Length() const;
```

### <a name="return-value"></a>Valeur de retour

Entier non signé qui Spécifie le nombre de caractères de la chaîne.

### <a name="remarks"></a>Notes

## <a name="operator-assign"></a>  StringReference::operator =, opérateur

Assigne l'objet spécifié à l'objet `StringReference` actif.

### <a name="syntax"></a>Syntaxe

```cpp
StringReference& operator=(const StringReference& __fstrArg);
StringReference& operator=(const ::default::char16* __strArg);
```

### <a name="parameters"></a>Paramètres

*__fstrArg*<br/>
Adresse d'un objet `StringReference` utilisé pour initialiser l'objet `StringReference` actif.

*__strArg*<br/>
Pointeur vers un tableau de valeurs char16 utilisé pour initialiser l'objet `StringReference` actif.

### <a name="return-value"></a>Valeur de retour

Référence à un objet de type `StringReference`.

### <a name="remarks"></a>Notes

Étant donné que `StringReference` est une classe C++ standard et non une classe ref, elle n’apparaît pas dans le **Explorateur d’objets**.

## <a name="operator-call"></a>  Stringreference::operator opérateur

Convertit un objet `StringReference` en un objet `Platform::String^`.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(no_release_return) __declspec(no_refcount)
         operator ::Platform::String^() const;
```

### <a name="return-value"></a>Valeur de retour

Handle d'un objet de type `Platform::String`.

## <a name="ctor"></a>  StringReference::StringReference, constructeur

Initialise une nouvelle instance de la classe `StringReference`.

### <a name="syntax"></a>Syntaxe

```cpp
StringReference();
StringReference(const StringReference& __fstrArg);
StringReference(const ::default::char16* __strArg);
StringReference(const ::default::char16* __strArg, size_t __lenArg);
```

### <a name="parameters"></a>Paramètres

*__fstrArg*<br/>
`StringReference` dont les données sont utilisées pour initialiser la nouvelle instance.

*__strArg*<br/>
Pointeur vers un tableau de valeurs char16 utilisé pour initialiser la nouvelle instance.

*__lenArg*<br/>
Nombre d'éléments de `__strArg`.

### <a name="remarks"></a>Notes

La première version de ce constructeur est le constructeur par défaut. La deuxième version initialise une nouvelle classe d'instance `StringReference` de l'objet spécifié par le paramètre `__fstrArg`. Les troisième et quatrième surcharges initialisent une nouvelle instance de `StringReference` à partir d’un tableau de valeurs char16. char16 représente un caractère de texte UNICODE 16 bits.

## <a name="see-also"></a>Voir aussi

[Platform::StringReference, classe](../cppcx/platform-stringreference-class.md)