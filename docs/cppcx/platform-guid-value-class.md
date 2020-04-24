---
title: Classe de valeur Platform::Guid
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 3849074f93424912b1dc5b93883482a6cb55892a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750655"
---
# <a name="platformguid-value-class"></a>Classe de valeur Platform::Guid

Représente un [GUID] (/windows/win32/api/guiddef/ns-guiddef-guidd-guid type dans le système de type Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
public value struct Guid
```

### <a name="members"></a>Membres

`Platform::Guid`a `Equals()`le `GetHashCode()`, `ToString()` , et les méthodes dérivées `GetTypeCode()` de la [plate-forme::Classe d’objet](../cppcx/platform-object-class.md), et la méthode dérivée de la [plate-forme::Classe de type](../cppcx/platform-type-class.md). `Platform::Guid`a également les membres suivants.

|Membre|Description|
|------------|-----------------|
|[Guid](#ctor)|Initialise une nouvelle instance d'un objet `Platform::Guid`.|
|[opérateur](#operator-equality)|Opérateur Égal à.|
|[opérateur!](#operator-inequality)|Opérateur Différent de.|
|[Opérateur&lt;](#operator-less)|Opérateur inférieur à.|
|[opérateur()](#operator-call)|Convertit une `Platform::Guid` en une `GUID`.|

### <a name="remarks"></a>Notes

Pour générer `Platform::Guid`une nouvelle , utilisez [windows::Foundation::GuidHelper::CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid#Windows_Foundation_GuidHelper_CreateNewGuid) méthode statique.

### <a name="requirements"></a>Spécifications

**Client pris en charge au minimum :** Windows 8

**Serveur pris en charge minimum :** Serveur Windows 2012

**Espace de noms :** Platform

**Métadonnées:** platform.winmd

## <a name="guidguid-constructors"></a><a name="ctor"></a>Guid::Constructeurs Guid

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

*Un*<br/>
Les 4 premiers octets de la `GUID`.

*B*<br/>
Les 2 octets `GUID`suivants de la .

*C*<br/>
Les 2 octets `GUID`suivants de la .

*d*<br/>
Octet suivant de `GUID`.

*E*<br/>
Octet suivant de `GUID`.

*F*<br/>
Octet suivant de `GUID`.

*G*<br/>
Octet suivant de `GUID`.

*h*<br/>
Octet suivant de `GUID`.

*Ⅰ*<br/>
Octet suivant de `GUID`.

*J*<br/>
Octet suivant de `GUID`.

*K*<br/>
Octet suivant de `GUID`.

*M*<br/>
A `GUID` sous la forme d’une [structure GUID](/windows/win32/api/guiddef/ns-guiddef-guid).

*n*<br/>
Les 8 octets `GUID`restants de la .

## <a name="guidoperator-operator"></a><a name="operator-equality"></a>Guid::opérateur OPÉRATEUR

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

C’est `Platform::Guid` vrai si les deux instances sont égales.

### <a name="remarks"></a>Notes

Préférez utiliser `==` l’opérateur au lieu de la [Windows::Foundation::GuidHelper:Equals](/uwp/api/windows.foundation.guidhelper.equals) méthode statique.

## <a name="guidoperator-operator"></a><a name="operator-inequality"></a>Guid::opérateur!

Compare deux instances `Platform::Guid` pour vérifier leur inégalité.

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

C’est `Platform::Guid` vrai si les deux instances ne sont pas égales.

## <a name="guidoperatorlt-operator"></a><a name="operator-less"></a>Guid::opérateur&lt; opérateur

Compare deux `Platform::Guid` instances pour commander.

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

Vrai si *guid1* est commandé avant *guid2*. La commande est lexicographique `Platform::Guid` après avoir traité chacun comme s’il s’identifait d’un tableau de quatre valeurs non signées 32 bits. Ce n’est pas la commande utilisée par SQL Server ou le cadre .NET, ni la même chose que la commande lexicographique par représentation des cordes.

Cet opérateur est `Guid` fourni afin que les objets puissent être plus facilement consommés par la bibliothèque standard de C.

## <a name="guidoperator-operator"></a><a name="operator-call"></a>Guid::opérateur () Opérateur

Convertit implicitement `Platform::Guid` une [structure GUID](/windows/win32/api/guiddef/ns-guiddef-guid).

### <a name="syntax"></a>Syntaxe

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>Valeur de retour

Une [structure GUID](/windows/win32/api/guiddef/ns-guiddef-guid).

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](../cppcx/platform-namespace-c-cx.md)
