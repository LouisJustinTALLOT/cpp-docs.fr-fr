---
description: 'En savoir plus sur : classe de valeur Platform :: GUID'
title: Classe de valeur Platform::Guid
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 4c2ffc5096e6b40266fef0934acc562edf721c24
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195188"
---
# <a name="platformguid-value-class"></a>Classe de valeur Platform::Guid

Représente un [GUID] (/Windows/Win32/API/guiddef/NS-guiddef-GUID type dans le système de type Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
public value struct Guid
```

### <a name="members"></a>Membres

`Platform::Guid` a les `Equals()` `GetHashCode()` méthodes, et `ToString()` dérivées de la classe [Platform :: Object](../cppcx/platform-object-class.md), et la `GetTypeCode()` méthode dérivée de la [classe Platform :: type](../cppcx/platform-type-class.md). `Platform::Guid` possède également les membres suivants.

|Membre|Description|
|------------|-----------------|
|[Guid](#ctor)|Initialise une nouvelle instance d'un objet `Platform::Guid`.|
|[opérateur = =](#operator-equality)|Opérateur Égal à.|
|[opérateur ! =](#operator-inequality)|Opérateur Différent de.|
|[operator&lt;](#operator-less)|Opérateur inférieur à.|
|[, opérateur ()](#operator-call)|Convertit une `Platform::Guid` en une `GUID`.|

### <a name="remarks"></a>Notes

Pour générer un nouveau `Platform::Guid` , utilisez la méthode statique [Windows :: Foundation :: GuidHelper :: CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid) .

### <a name="requirements"></a>Spécifications

**Client minimal pris en charge :** Windows 8

**Serveur minimal pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** Platform. winmd

## <a name="guidguid-constructors"></a><a name="ctor"></a> GUID :: Guid, constructeurs

Initialise une nouvelle instance d'un objet `Platform::Guid`.

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

*un*<br/>
Les 4 premiers octets du `GUID` .

*b*<br/>
2 octets suivants de `GUID` .

*c*<br/>
2 octets suivants de `GUID` .

*d*<br/>
Octet suivant de `GUID`.

*Envoyer*<br/>
Octet suivant de `GUID`.

*f*<br/>
Octet suivant de `GUID`.

*activée*<br/>
Octet suivant de `GUID`.

*h*<br/>
Octet suivant de `GUID`.

*i*<br/>
Octet suivant de `GUID`.

*j*<br/>
Octet suivant de `GUID`.

*DK*<br/>
Octet suivant de `GUID`.

*m*<br/>
`GUID`Dans le formulaire, une [structure GUID](/windows/win32/api/guiddef/ns-guiddef-guid).

*n*<br/>
8 octets restants de `GUID` .

## <a name="guidoperator-operator"></a><a name="operator-equality"></a> GUID :: Operator = =, opérateur

Compare si deux instances `Platform::Guid` sont égales.

### <a name="syntax"></a>Syntaxe

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Paramètres

*GUID1*<br/>
Premier `Platform::Guid` à comparer.

*GUID2*<br/>
Deuxième `Platform::Guid` à comparer.

### <a name="return-value"></a>Valeur renvoyée

True si les deux `Platform::Guid` instances sont égales.

### <a name="remarks"></a>Notes

Préférez l’utilisation `==` de l’opérateur au lieu de la méthode statique [Windows :: Foundation :: GuidHelper :: Equals](/uwp/api/windows.foundation.guidhelper.equals) .

## <a name="guidoperator-operator"></a><a name="operator-inequality"></a> GUID :: Operator ! =, opérateur

Compare deux instances `Platform::Guid` pour vérifier leur inégalité.

### <a name="syntax"></a>Syntaxe

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Paramètres

*GUID1*<br/>
Premier `Platform::Guid` à comparer.

*GUID2*<br/>
Deuxième `Platform::Guid` à comparer.

### <a name="return-value"></a>Valeur renvoyée

True si les deux `Platform::Guid` instances ne sont pas égales.

## <a name="guidoperatorlt-operator"></a><a name="operator-less"></a> GUID :: Operator, &lt; opérateur

Compare deux `Platform::Guid` instances pour le classement.

### <a name="syntax"></a>Syntaxe

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Paramètres

*GUID1*<br/>
Premier `Platform::Guid` à comparer.

*GUID2*<br/>
Deuxième `Platform::Guid` à comparer.

### <a name="return-value"></a>Valeur renvoyée

True si *guid1* est ordonné avant *GUID2*. Le classement est lexicographique après avoir traité chaque `Platform::Guid` comme s’il s’agissait d’un tableau de valeurs non signées 4 32 bits. Il ne s’agit pas du classement utilisé par SQL Server ou le .NET Framework, ni du classement lexicographique par représentation sous forme de chaîne.

Cet opérateur est fourni afin que `Guid` les objets puissent être plus facilement consommés par la bibliothèque C++ standard.

## <a name="guidoperator-operator"></a><a name="operator-call"></a> GUID :: Operator (), opérateur

Convertit implicitement un `Platform::Guid` en une [structure GUID](/windows/win32/api/guiddef/ns-guiddef-guid).

### <a name="syntax"></a>Syntaxe

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>Valeur de retour

[Structure de GUID](/windows/win32/api/guiddef/ns-guiddef-guid).

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)
