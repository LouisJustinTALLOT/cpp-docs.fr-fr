---
description: 'En savoir plus sur : Platform, espace de noms (C++/CX)'
title: Platform (espace de noms) (C++/CX)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- Platform/Platform
helpviewer_keywords:
- Platform Namespace (C++/CX)
ms.assetid: b160e822-d424-43d2-ba60-57b0e81f259c
ms.openlocfilehash: 80f1b82ed39212812c8d316d4b7de09bf20ccad8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308313"
---
# <a name="platform-namespace-ccx"></a>Platform (espace de noms) (C++/CX)

Contient les types intégrés compatibles avec Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
using namespace Platform;
```

### <a name="members"></a>Membres

**Attributs**

L'espace de noms Platform contient des attributs, des classes, des énumérations, des interfaces et des structures. Platform contient également des espaces de noms imbriqués.

|Attribut|Description|
|---------------|-----------------|
|Indicateurs|Indique qu'une énumération peut être traitée comme un champ de bits, c'est-à-dire un ensemble d'indicateurs.|
|MTAThread|Indique que le modèle de thread d'une application est un modèle MTA (MultiThreaded Apartment).|
|STAThread|Indique que le modèle de thread d'une application est un modèle STA (Single-Threaded Apartment).|

**Classes**

L'espace de noms Platform contient les classes ci-dessous.

|Classe|Description|
|-----------|-----------------|
|[Classe Platform :: AccessDeniedException](../cppcx/platform-accessdeniedexception-class.md)|Levée lorsque l'accès est refusé à une ressource ou une fonctionnalité.|
|[Platform :: agile, classe](../cppcx/platform-agile-class.md)|Représente un objet non agile comme un objet agile.|
|[Platform :: Array, classe](../cppcx/platform-array-class.md)|Représente un tableau unidimensionnel modifiable.|
|[Classe Platform :: ArrayReference](../cppcx/platform-arrayreference-class.md)|Représente un tableau dont l'initialisation est optimisée pour réduire les opérations de copie.|
|[Classe Platform :: Box](../cppcx/platform-box-class.md)|Utilisée pour déclarer un type boxed qui encapsule un type valeur tel que Windows::Foundation::DateTime ou int64 lorsque ce type est passé via l'interface binaire d'application (ABI) ou stocké dans une variable de type [Platform::Object^](../cppcx/platform-object-class.md).|
|[Classe Platform :: ChangedStateException](../cppcx/platform-changedstateexception-class.md)|Levée lorsque les méthodes d'un itérateur de collection ou d'une vue de collection sont appelées après la modification d'une collection parente, invalidant les résultats de la méthode.|
|[Classe Platform :: ClassNotRegisteredException](../cppcx/platform-classnotregisteredexception-class.md)|Levée lorsqu'une classe COM n'a pas été inscrite.|
|[Platform :: COMException, classe](../cppcx/platform-comexception-class.md)|Représente l'exception qui est levée lorsqu'une valeur non identifiée est retournée par un appel de méthode COM.|
|[Plateforme ::D classe délégué](../cppcx/platform-delegate-class.md)|Représente la signature d'une fonction de rappel.|
|[Plateforme ::D classe isconnectedException](../cppcx/platform-disconnectedexception-class.md)|L'objet s'est déconnecté de ses clients.|
|[Platform :: exception, classe](../cppcx/platform-exception-class.md)|Représente les erreurs qui se produisent pendant l'exécution de l'application. Classe de base des exceptions.|
|[Classe Platform :: FailureException](../cppcx/platform-failureexception-class.md)|Levée lorsque l'opération a échoué. Il s'agit de l'équivalent de E_FAIL HRESULT.|
|[Classe de valeur Platform::Guid](../cppcx/platform-guid-value-class.md)|Représente un GUID dans le système de type Windows Runtime.|
|[Classe Platform :: InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md)|Levée lorsque l'un des arguments fournis à une méthode n'est pas valide.|
|[Platform :: InvalidCastException, classe](../cppcx/platform-invalidcastexception-class.md)|Levée en cas de conversion non valide ou de conversion explicite.|
|[Platform :: MTAThreadAttribute (classe)](../cppcx/platform-mtathreadattribute-class.md)|Indique que le modèle de thread d'une application est un modèle MTA (MultiThreaded Apartment).|
|[Platform :: NotImplementedException, classe](../cppcx/platform-notimplementedexception-class.md)|Levée si une méthode d'interface n'a pas été implémentée pour une classe.|
|[Platform :: NullReferenceException, classe](../cppcx/platform-nullreferenceexception-class.md)|Levée lors d'une tentative de suppression de la référence à une référence d'objet null.|
|[Platform :: Object, classe](../cppcx/platform-object-class.md)|Classe de base qui fournit le comportement courant.|
|[Platform :: ObjectDisposedException, classe](../cppcx/platform-objectdisposedexception-class.md)|Levée lorsqu'une opération est exécutée sur un objet supprimé.|
|[Classe Platform :: OperationCanceledException](../cppcx/platform-operationcanceledexception-class.md)|Levée lorsqu'une opération est abandonnée.|
|[Classe Platform :: OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md)|Levée lorsqu'une opération tente d'accéder aux données en dehors de la plage valide.|
|[Platform :: OutOfMemoryException, classe](../cppcx/platform-outofmemoryexception-class.md)|Levée en cas de mémoire insuffisante pour terminer l'opération.|
|[Classe Platform :: STAThreadAttribute](../cppcx/platform-stathreadattribute-class.md)|Indique que le modèle de thread d'une application est un modèle STA (Single-Threaded Apartment).|
|[Platform :: String, classe](../cppcx/platform-string-class.md)|Collection séquentielle de caractères Unicode utilisée pour représenter du texte.|
|[Classe Platform :: StringReference](../cppcx/platform-stringreference-class.md)|Permet d'accéder aux mémoires tampon de chaîne avec un minimum d'opérations de copie.|
|[Classe Platform :: type](../cppcx/platform-type-class.md)|Identifie un type intégré par une énumération de catégorie.|
|[Platform :: ValueType, classe](../cppcx/platform-valuetype-class.md)|Classe de base pour les instances de types de valeur.|
|[Platform :: WeakReference, classe](../cppcx/platform-weakreference-class.md)|Fournit une référence faible aux objets de classe ref qui n'incrémente pas le nombre de références.|
|[Classe Platform :: WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md)|Représente un tableau en écriture seule unidimensionnel qui est utilisé comme paramètre d'entrée sur les méthodes qui implémentent le modèle FillArray.|
|[Classe Platform :: WrongThreadException](../cppcx/platform-wrongthreadexception-class.md)|Levée lorsqu'un thread effectue un appel via un pointeur d'interface qui concerne un objet proxy qui n'appartient pas à l'apartment du thread.|

**Implémentations d'interfaces**

L'espace de noms Platform définit les interfaces ci-dessous.

|Interface|Description|
|---------------|-----------------|
|[Platform :: IBox, interface](../cppcx/platform-ibox-interface.md)|Utilisée pour passer des types valeur aux fonctions dont les paramètres sont de type Platform::Object^.|
|[Platform :: IBoxArray, interface](../cppcx/platform-iboxarray-interface.md)|Interface utilisée pour passer des tableaux de types valeur aux fonctions dont les paramètres sont de type Platform::Array.|
|[Platform :: IDisposable, interface](../cppcx/platform-idisposable-interface.md)|Utilisée pour libérer des ressources non managées.|

**Énumérations**

L'espace de noms Platform contient les énumérations ci-dessous.

|Interface|Description|
|---------------|-----------------|
|[Platform::CallbackContext, énumération](../cppcx/platform-callbackcontext-enumeration.md)|Énumération utilisée comme paramètre du constructeur délégué. Elle détermine si le rappel doit être marshalé au thread d'origine ou au thread de l'appelant.|
|[Platform::TypeCode, énumération](../cppcx/platform-typecode-enumeration.md)|Spécifie une catégorie numérique qui représente un type intégré.|

**Structures**

L'espace de noms Platform contient les structures ci-dessous.

|Structure|Description|
|---------------|-----------------|
|[Platform :: enum, classe](../cppcx/platform-enum-class.md)|Représente une constante nommée.|
|[Classe de valeur Platform::Guid](../cppcx/platform-guid-value-class.md)|Représente un GUID.|
|[Classe de valeur Platform::IntPtr](../cppcx/platform-intptr-value-class.md)|Pointeur signé dont la taille est appropriée pour la plateforme (32 bits ou 64 bits).|
|[Classe de valeur Platform::SizeT](../cppcx/platform-sizet-value-class.md)|Type de données non signé utilisé pour représenter la taille d'un objet.|
|[Classe de valeur Platform::UIntPtr](../cppcx/platform-uintptr-value-class.md)|Pointeur non signé dont la taille est appropriée pour la plateforme (32 bits ou 64 bits).|

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform :: Collections](../cppcx/platform-collections-namespace.md)<br/>
[Platform :: Runtime :: CompilerServices, espace de noms](../cppcx/platform-runtime-compilerservices-namespace.md)<br/>
[Platform :: Runtime :: InteropServices, espace de noms](../cppcx/platform-runtime-interopservices-namespace.md)<br/>
[Platform :: Metadata (espace de noms)](../cppcx/platform-metadata-namespace.md)
