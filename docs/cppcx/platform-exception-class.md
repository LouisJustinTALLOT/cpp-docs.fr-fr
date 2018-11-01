---
title: Platform::Exception (classe)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception::Exception
- VCCORLIB/Platform::Exception::CreateException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: ca1d5a67-3a5a-48fe-8099-f9c38a2d2dce
ms.openlocfilehash: 8579b3506d727f5c4faeb56a9c1f3ea88b7a4b6a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464959"
---
# <a name="platformexception-class"></a>Platform::Exception (classe)

Représente les erreurs qui se produisent lors de l'exécution de l'application. Les classes d'exception personnalisées ne peuvent pas être dérivées d' `Platform::Exception`. Si vous avez besoin d'une exception personnalisée, vous pouvez utiliser `Platform::COMException` et spécifier un HRESULT propre à l'application.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class Exception : Object,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>Membres

La classe `Exception` hérite de la classe `Object` et des interfaces `IException`, `IPrintable`et `IEquatable` .

La classe `Exception` comporte également les types de membres ci-dessous.

### <a name="constructors"></a>Constructeurs

|Membre|Description|
|------------|-----------------|
|[Exception::exception](#ctor)|Initialise une nouvelle instance de la classe `Exception`.|

### <a name="methods"></a>Méthodes

La classe `Exception` hérite des méthodes `Equals()`, `Finalize()`,`GetHashCode()`,`GetType()`,`MemberwiseClose()`et `ToString()` de la [Platform::Object Class](../cppcx/platform-object-class.md). La classe `Exception` comporte aussi la méthode ci-dessous.

|Membre|Description|
|------------|-----------------|
|[Exception::CreateException](#createexception)|Crée une exception qui représente la valeur HRESULT spécifiée.|

### <a name="properties"></a>Properties

La classe Exception comporte aussi les propriétés ci-dessous.

|Membre|Description|
|------------|-----------------|
|[Exception::HRESULT](#hresult)|HRESULT qui correspond à l'exception.|
|[Exception::Message](#message)|Message qui décrit l'exception. Cette valeur est en lecture seule et ne peut pas être modifiée après la construction d' `Exception` .|

### <a name="requirements"></a>Configuration requise

**Minimum de client pris en charge :** Windows 8

**Minimum de serveur pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** platform.winmd

## <a name="createexception"></a> Exception::CreateException (méthode)

Crée Platform::Exception^ à partir d'une valeur HRESULT spécifique.

### <a name="syntax"></a>Syntaxe

```cpp
Exception^ CreateException(int32 hr);
Exception^ CreateException(int32 hr, Platform::String^ message);
```

### <a name="parameters"></a>Paramètres

*ressources humaines*<br/>
Valeur HRESULT que vous obtenez généralement à partir d'un appel à une méthode COM. Si la valeur est 0, ce qui est égal à S_OK, cette méthode lève [Platform::InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md) , car les méthodes COM qui réussissent ne doivent pas lever d’exceptions.

*message*<br/>
Chaîne qui décrit l'erreur.

### <a name="return-value"></a>Valeur de retour

Exception qui représente l'erreur HRESULT.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour créer une exception à partir d'une valeur HRESULT retournée, par exemple, à partir d'un appel à une méthode d'interface COM. Utilisez la surcharge qui accepte un paramètre String^ pour fournir un message personnalisé.

Il est fortement recommandé d’utiliser CreateException pour créer une exception fortement typée au lieu de créer un [Platform::COMException](../cppcx/platform-comexception-class.md) qui contient uniquement la valeur HRESULT.

## <a name="ctor"></a>  Exception::exception, constructeur

Initialise une nouvelle instance de la classe Exception.

### <a name="syntax"></a>Syntaxe

```cpp
Exception(int32 hresult);
Exception(int32 hresult, ::Platform::String^ message);
```

### <a name="parameters"></a>Paramètres

*HRESULT*<br/>
Erreur HRESULT qui est représentée par l'exception.

*message*<br/>
Message spécifié par l'utilisateur, tel que le texte normatif, qui est associé à l'exception. En général, préférez la deuxième surcharge afin de fournir un message descriptif aussi précis que possible en indiquant comment et pourquoi l'erreur s'est produite.

## <a name="hresult"></a>  Propriété exception::HRESULT

HRESULT qui correspond à l'exception.

### <a name="syntax"></a>Syntaxe

```cpp
public:
    property int HResult { int get(); }
```

## <a name="property-value"></a>Valeur de propriété

Valeur HRESULT.

### <a name="remarks"></a>Notes

La plupart des exceptions démarrent sous forme d'erreurs COM, qui sont retournées en tant que valeurs HRESULT. C++/CX convertit ces valeurs en objets Platform::Exception^, et cette propriété stocke la valeur du code d'erreur d'origine.

## <a name="message"></a> Exception::message (propriété)

Message qui décrit l'erreur.

### <a name="syntax"></a>Syntaxe

```cpp
public:property String^ Message;
```

## <a name="property-value"></a>Valeur de propriété

Dans les exceptions qui proviennent de Windows Runtime, il s'agit d'une description de l'erreur fournie par le système.

### <a name="remarks"></a>Notes

Dans Windows 8, cette propriété est en lecture seule, car les exceptions dans cette version du Runtime Windows sont traversent ABI uniquement sous forme de HRESULTS. Dans Windows 8.1, les informations sur l'exception traversent ABI. Par ailleurs, vous pouvez fournir un message personnalisé accessible par programmation à d'autres composants. Pour plus d’informations, consultez [Exceptions (C++ / c++ / CX)](../cppcx/exceptions-c-cx.md).

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)