---
title: Classe de valeur Platform::Guid
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: ad71ed4965a3dd4846c9ba5d8ed2627ed8f7e056
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334649"
---
# <a name="platformguid-value-class"></a>Classe de valeur Platform::Guid

Représente un type [GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931) dans le système de type Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
public value struct Guid
```

### <a name="members"></a>Membres

`Platform::Guid` a la `Equals()`, `GetHashCode()`, et `ToString()` méthodes dérivées de la [Platform::Object Class](../cppcx/platform-object-class.md)et le `GetTypeCode()` méthode dérivée la [classe Platform::Type](../cppcx/platform-type-class.md). `Platform::Guid` possède également les membres suivants.

|Membre|Description|
|------------|-----------------|
|[Guid](#ctor)|Initialise une nouvelle instance d'une classe `Platform::Guid`.|
|[operator==](#operator-equality)|Opérateur Equals.|
|[!=, opérateur](#operator-inequality)|Opérateur Not Equals.|
|[operator&lt;](#operator-less)|Opérateur d’infériorité.|
|[operator()](#operator-call)|Convertit une `Platform::Guid` en une `GUID`.|

### <a name="remarks"></a>Notes

Pour obtenir un exemple montrant comment générer un nouveau `Platform::Guid` à l’aide de la fonction Windows [CoCreateGuid](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateguid), consultez [les composant WinRT : Comment générer un GUID ?](https://www.eternalcoding.com/?p=383)

### <a name="requirements"></a>Spécifications

**Prise en charge minimale du client :** Windows 8

**Serveur pris en charge minimale :** Windows Server 2012

**Espace de noms :** Plateforme

**Métadonnées :** platform.winmd

## <a name="ctor"></a> GUID::GUID, constructeurs

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
Les 4 premiers octets de la `GUID`.

*b*<br/>
Les 2 octets suivants de la `GUID`.

*c*<br/>
Les 2 octets suivants de la `GUID`.

*d*<br/>
L’octet suivant de la `GUID`.

*e*<br/>
L’octet suivant de la `GUID`.

*f*<br/>
L’octet suivant de la `GUID`.

*g*<br/>
L’octet suivant de la `GUID`.

*h*<br/>
L’octet suivant de la `GUID`.

*i*<br/>
L’octet suivant de la `GUID`.

*j*<br/>
L’octet suivant de la `GUID`.

*k*<br/>
L’octet suivant de la `GUID`.

*m*<br/>
Un `GUID` sous la forme un [structure GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931).

*n*<br/>
Les 8 octets restants de la `GUID`.

## <a name="operator-equality"></a> GUID::operator ==, opérateur

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

True si les deux `Platform::Guid` instances sont égales.

## <a name="operator-inequality"></a> GUID::operator ! =, opérateur

Compare deux `Platform::Guid` instances pour vérifier leur inégalité.

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

True si les deux `Platform::Guid` instances ne sont pas égales.

## <a name="operator-less"></a> GUID::operator&lt; opérateur

Compare deux `Platform::Guid` instances pour le classement.

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

True si *guid1* est classé avant *guid2*. Le classement est lexicographique après chaque traitement `Platform::Guid` comme s’il est un tableau de quatre valeurs non signées de 32 bits. Cela n’est pas le classement utilisé par SQL Server ou le .NET Framework, ni est identique à l’ordre lexicographique en représentation sous forme de chaîne.

Cet opérateur est fourni afin que `Guid` objets peuvent être plus facilement utilisées par la bibliothèque C++ standard.

## <a name="operator-call"></a> Opérateur de GUID::operator

Convertit implicitement un `Platform::Guid` à un [structure GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931).

### <a name="syntax"></a>Syntaxe

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>Valeur de retour

Un [structure GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931).

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)
