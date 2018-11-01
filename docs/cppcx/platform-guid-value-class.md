---
title: Classe de valeur Platform::Guid
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 0a339de3aec14b6bd1dc461f53c1a7417db738ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482925"
---
# <a name="platformguid-value-class"></a>Classe de valeur Platform::Guid

Représente un type [GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931) dans le système de type Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
public value struct Guid
```

### <a name="members"></a>Membres

Le Guid contient les méthodes Equals(), GetHashCode(), et ToString() dérivées de la [Platform::Object Class](../cppcx/platform-object-class.md), et la méthode GetTypeCode() dérivée de la [Platform::Type Class](../cppcx/platform-type-class.md). Le GUID comporte également les membres suivants.

|Membre|Description|
|------------|-----------------|
|[Guid](#ctor)|Initialise une nouvelle instance du struct GUID.|
|[operator==](#operator-equality)|Opérateur Equals.|
|[!=, opérateur](#operator-not-equal)|Opérateur Not Equals.|
|[operator()](#operator-call)|Convertit un Guid en GUID.|

### <a name="remarks"></a>Notes

Pour un exemple de génération d'un nouveau Platform::Guid à l'aide de la fonction Windows [CoCreateGuid](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateguid), consultez [Composant WinRT : comment générer un GUID ?](http://blogs.msdn.com/b/eternalcoding/archive/2013/03/25/winrt-component-how-to-generate-a-guid.aspx)

### <a name="requirements"></a>Configuration requise

**Minimum de client pris en charge :** Windows 8

**Minimum de serveur pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** platform.winmd

## <a name="ctor"></a> GUID::GUID, constructeurs

Initialise une nouvelle instance d'une structure de Guid.

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
Quatre premiers octets du GUID.

*b*<br/>
Deux octets suivants du GUID.

*c*<br/>
Deux octets suivants du GUID.

*d*<br/>
Octet suivant du GUID.

*e*<br/>
Octet suivant du GUID.

*f*<br/>
Octet suivant du GUID.

*g*<br/>
Octet suivant du GUID.

*h*<br/>
Octet suivant du GUID.

*i*<br/>
Octet suivant du GUID.

*J*<br/>
Octet suivant du GUID.

*k*<br/>
Octet suivant du GUID.

*m*<br/>
GUID défini.

*n*<br/>
Huit octets restants du GUID.

## <a name="operator-equality"></a> GUID::operator ==, opérateur

Compare deux GUID.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::Guid::operator==
```

### <a name="return-value"></a>Valeur de retour

True si les deux GUID sont égaux.

## <a name="operator-inequality"></a> GUID::operator ! =, opérateur

Compare deux GUID.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::Guid::operator!=
```

### <a name="return-value"></a>Valeur de retour

True si les deux GUID ne sont pas égaux.

## <a name="operator-call"></a> Opérateur de GUID::operator

Convertit implicitement un [structure GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931)en un Platform::Guid.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::Guid operator();
```

### <a name="return-value"></a>Valeur de retour

Structure de GUID.

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)