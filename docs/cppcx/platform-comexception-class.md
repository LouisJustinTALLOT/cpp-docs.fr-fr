---
description: 'En savoir plus sur : plateforme :: COMException, classe'
title: Platform::COMException (classe)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::COMException
- VCCORLIB/Platform::COMException::HResult
- VCCORLIB/Platform::COMException::Message
helpviewer_keywords:
- Platform::COMException Class
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
ms.openlocfilehash: 71f6c3fa6d29a884627f2bf5aae07fbc0349ec9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176117"
---
# <a name="platformcomexception-class"></a>Platform::COMException (classe)

Représente les erreurs COM qui se produisent lors de l'exécution de l'application. COMException est la classe de base pour un jeu d'exceptions prédéfinies et standard.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>Membres

La classe COMException hérite de la classe d'objets et des interfaces IException, IPrintable et IEquatable.

COMException a également les types de membre suivants.

**Constructeurs**

|Membre|Description|
|------------|-----------------|
|[COMException](#ctor)|Initialise une nouvelle instance de la classe COMException.|

**Méthodes**

La classe COMException hérite des méthodes Equals(), Finalize(), GetHashCode(), GetType(), MemberwiseClose() et ToString() de [Platform::Object Class](../cppcx/platform-object-class.md).

**Propriétés**

La classe COMException a les propriétés ci-dessous.

|Membre|Description|
|------------|-----------------|
|[Exception :: HResult](#hresult)|HRESULT qui correspond à l'exception.|
|[Exception :: message](#message)|Message décrivant l'exception.|

## <a name="derived-exceptions"></a>Exceptions dérivées

Les exceptions prédéfinies suivantes sont dérivées de COMException. Elles diffèrent de COMException uniquement au niveau de leur nom, du nom de leur constructeur et de leur valeur HRESULT sous-jacente.

|Nom|HRESULT sous-jacent|Description|
|----------|------------------------|-----------------|
|COMException|*hresult défini par l’utilisateur*|Levée lorsqu'un HRESULT non reconnu est retourné d'un appel de méthode COM.|
|AccessDeniedException|E_ACCESSDENIED|Levée lorsque l'accès est refusé à une ressource ou à une fonctionnalité.|
|ChangedStateException|E_CHANGED_STATE|Levée lorsque les méthodes d'un itérateur de collection ou d'une vue de collection sont appelées après la modification d'une collection parente, invalidant les résultats de la méthode.|
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|Levée lorsqu'une classe COM n'a pas été inscrite.|
|DisconnectedException|RPC_E_DISCONNECTED|Levée lorsqu'un objet est déconnecté de ses clients.|
|FailureException|E_FAIL|Levée lorsqu'une opération échoue.|
|InvalidArgumentException|E_INVALIDARG|Levée lorsque l'un des arguments fournis à une méthode n'est pas valide.|
|InvalidCastException|E_NOINTERFACE|Levée lorsqu'un type ne peut pas être casté en un autre type.|
|NotImplementedException|E_NOTIMPL|Levée si une méthode d'interface n'a pas été implémentée pour une classe.|
|NullReferenceException|E_POINTER|Levée lors d'une tentative de suppression de la référence à une référence d'objet null.|
|OperationCanceledException|E_ABORT|Levée lorsqu'une opération est abandonnée.|
|OutOfBoundsException|E_BOUNDS|Levée lorsqu'une opération tente d'accéder aux données en dehors de la plage valide.|
|OutOfMemoryException|E_OUTOFMEMORY|Levée en cas de mémoire insuffisante pour terminer l'opération.|

### <a name="requirements"></a>Spécifications

**Client minimal pris en charge :** Windows 8

**Serveur minimal pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** Platform. winmd

## <a name="comexceptioncomexception-constructor"></a><a name="ctor"></a> COMException :: COMException, constructeur

Initialise une nouvelle instance de la classe COMException.

### <a name="syntax"></a>Syntaxe

```cpp
COMException( int hresult )
```

### <a name="parameters"></a>Paramètres

*signé*<br/>
Erreur HRESULT qui est représentée par l'exception.

## <a name="comexceptionhresult-property"></a><a name="hresult"></a> COMException :: HResult, propriété

HRESULT qui correspond à l'exception.

### <a name="syntax"></a>Syntaxe

```cpp
public:
    property int HResult { int get();}
```

## <a name="property-value"></a>Valeur de propriété

Valeur HRESULT qui spécifie l'erreur.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la façon d’interpréter la valeur HRESULT, consultez [structure of com Error Codes](/windows/win32/com/structure-of-com-error-codes).

## <a name="comexceptionmessage-property"></a><a name="message"></a> COMException :: message, propriété

Message décrivant l'exception.

### <a name="syntax"></a>Syntaxe

```cpp
public:property String^ Message {    String^ get();}
```

### <a name="property-value"></a>Valeur de propriété

Description de l'exception.

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](../cppcx/platform-namespace-c-cx.md)
