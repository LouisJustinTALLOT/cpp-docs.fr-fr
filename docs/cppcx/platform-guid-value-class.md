---
title: Classe de valeur Platform::Guid
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: f63b2bb4fd5f809861622a4f6b255ee3725564b6
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816595"
---
# <a name="platformguid-value-class"></a>Classe de valeur Platform::Guid

Représente un type [GUID](/previous-versions/cc317743(v%3dmsdn.10)) dans le système de type Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
public value struct Guid
```

### <a name="members"></a>Membres

`Platform::Guid` a les méthodes `Equals()`, `GetHashCode()`et `ToString()` dérivées de la classe [Platform :: Object](../cppcx/platform-object-class.md), et la méthode `GetTypeCode()` dérivée de la [classe Platform :: type](../cppcx/platform-type-class.md). `Platform::Guid` possède également les membres suivants.

|Membre|Description|
|------------|-----------------|
|[Guid](#ctor)|Initialise une nouvelle instance d'une classe `Platform::Guid`.|
|[operator==](#operator-equality)|Opérateur Equals.|
|[operator!=](#operator-inequality)|Opérateur Not Equals.|
|[operator&lt;](#operator-less)|Opérateur inférieur à.|
|[operator()](#operator-call)|Convertit une `Platform::Guid` en une `GUID`.|

### <a name="remarks"></a>Notes

Pour générer une nouvelle `Platform::Guid`, utilisez la méthode statique [Windows :: Foundation :: GuidHelper :: CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid#Windows_Foundation_GuidHelper_CreateNewGuid) .

### <a name="requirements"></a>Configuration requise

**Client minimal pris en charge :** Windows 8

**Serveur minimal pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** platform.winmd

## <a name="ctor"></a>GUID :: Guid, constructeurs

Initialise une nouvelle instance d'une classe `Platform::Guid`.

### <a name="syntax"></a>Syntaxe

```cpp
Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    unsigned char d,
    unsigned char e,
    unsigned char f,
    unsigned char g,
    unsigned char h,
    unsigned char i,
    unsigned char j,
    unsigned char k );

Guid(GUID m);

Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    Array<unsigned char>^ n );
```

### <a name="parameters"></a>Paramètres

*a*<br/>
Les 4 premiers octets du `GUID`.

*b*<br/>
2 octets suivants du `GUID`.

*c*<br/>
2 octets suivants du `GUID`.

*d*<br/>
Octet suivant du `GUID`.

*e*<br/>
Octet suivant du `GUID`.

*f*<br/>
Octet suivant du `GUID`.

*g*<br/>
Octet suivant du `GUID`.

*h*<br/>
Octet suivant du `GUID`.

*i*<br/>
Octet suivant du `GUID`.

*j*<br/>
Octet suivant du `GUID`.

*k*<br/>
Octet suivant du `GUID`.

*m*<br/>
Une `GUID` dans le formulaire est une [structure GUID](/previous-versions/cc317743(v%3dmsdn.10)).

*n*<br/>
8 octets restants du `GUID`.

## <a name="operator-equality"></a>GUID :: Operator = =, opérateur

Compare si deux instances `Platform::Guid` sont égales.

### <a name="syntax"></a>Syntaxe

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Paramètres

*guid1*<br/>
Premier `Platform::Guid` à comparer.

*guid2*<br/>
Deuxième `Platform::Guid` à comparer.

### <a name="return-value"></a>Valeur de retour

True si les deux instances `Platform::Guid` sont égales.

### <a name="remarks"></a>Notes

Préférez l’utilisation de l’opérateur `==` au lieu de la méthode statique [Windows :: Foundation :: GuidHelper :: Equals](/uwp/api/windows.foundation.guidhelper.equals) .

## <a name="operator-inequality"></a>GUID :: Operator ! =, opérateur

Compare l’inégalité de deux instances de `Platform::Guid`.

### <a name="syntax"></a>Syntaxe

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Paramètres

*guid1*<br/>
Premier `Platform::Guid` à comparer.

*guid2*<br/>
Deuxième `Platform::Guid` à comparer.

### <a name="return-value"></a>Valeur de retour

True si les deux instances `Platform::Guid` ne sont pas égales.

## <a name="operator-less"></a>GUID :: Operator&lt;, opérateur

Compare deux instances de `Platform::Guid` pour le classement.

### <a name="syntax"></a>Syntaxe

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Paramètres

*guid1*<br/>
Premier `Platform::Guid` à comparer.

*guid2*<br/>
Deuxième `Platform::Guid` à comparer.

### <a name="return-value"></a>Valeur de retour

True si *guid1* est ordonné avant *GUID2*. Le classement est lexicographique après le traitement de chaque `Platform::Guid` comme s’il s’agissait d’un tableau de valeurs non signées 4 32 bits. Il ne s’agit pas du classement utilisé par SQL Server ou le .NET Framework, ni du classement lexicographique par représentation sous forme de chaîne.

Cet opérateur est fourni afin que les objets `Guid` puissent être plus facilement consommés C++ par la bibliothèque standard.

## <a name="operator-call"></a>GUID :: Operator (), opérateur

Convertit implicitement un `Platform::Guid` en une [structure GUID](/previous-versions/cc317743(v%3dmsdn.10)).

### <a name="syntax"></a>Syntaxe

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>Valeur de retour

[Structure de GUID](/previous-versions/cc317743(v%3dmsdn.10)).

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](../cppcx/platform-namespace-c-cx.md)
