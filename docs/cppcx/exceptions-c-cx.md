---
title: Exceptions (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2018
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c82f54a365208c247e735e467157dfd29f9f271a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613407"
---
# <a name="exceptions-ccx"></a>Exceptions (C++/CX)

Gestion des erreurs dans C++ / c++ / CX est basée sur les exceptions. Au niveau plus fondamental, composants Windows Runtime signalent les erreurs en tant que valeurs HRESULT. En C / c++ / CX, ces valeurs sont converties en exceptions fortement typées qui contiennent une valeur HRESULT et une description de chaîne que vous pouvez accéder par programmation.  Les exceptions sont implémentées sous forme de `ref class` qui dérive de `Platform::Exception`.  L'espace de noms `Platform` définit des classes d'exception distinctes pour les valeurs HRESULT les plus courantes. Toutes les autres valeurs sont indiquées via la classe `Platform::COMException` . Toutes les classes d'exceptions ont un champ de [Exception::HResult](platform-exception-class.md#hresult) qui peut être utilisé pour récupérer le HRESULT d'origine. Vous pouvez également consulter les informations de pile des appels pour le code utilisateur dans le débogueur qui peut aider à identifier la source d’origine de l’exception, même si celle-ci provient du code qui a été écrit dans une langue autre que C++.

## <a name="exceptions"></a>Exceptions

Dans votre programme C++, vous pouvez lever et intercepter une exception qui provient d’une opération d’exécution de Windows, une exception qui est dérivée de `std::exception`, ou un type défini par l’utilisateur. Vous devez lever une exception Windows Runtime uniquement lorsqu’elle traversera la limite (ABI) de l’interface binaire d’application, par exemple, lorsque le code qui intercepte votre exception est écrit en JavaScript. Lorsqu’une exception non Windows Runtime C++ atteint la limite ABI, elle est convertie en un `Platform::FailureException` exception, ce qui représente un HRESULT E_FAIL. Pour plus d’informations sur l’ABI, consultez [création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Vous pouvez déclarer un [Platform::Exception](platform-exception-class.md) en utilisant l’une des deux constructeurs qui acceptent un paramètre HRESULT ou un paramètre HRESULT et un [Platform::String](platform-string-class.md)^ paramètre qui peut être passé à travers le ABI à une application Windows Runtime qui prend en charge. Vous pouvez aussi déclarer une exception à l'aide de l'une des deux surcharges de méthode [Exception::CreateException](platform-exception-class.md#createexception) qui acceptent un paramètre HRESULT ou un paramètre HRESULT et un paramètre `Platform::String^` .

## <a name="standard-exceptions"></a>Exceptions standard

C++ / c++ / CX prend en charge un ensemble d’exceptions standard qui représentent des erreurs HRESULT courantes. Chaque exception standard dérive de [Platform::COMException](platform-comexception-class.md), qui dérive à son tour de `Platform::Exception`. Lorsque vous levez une exception à travers la limite ABI, vous devez lever l'une des exceptions standard.

Vous ne pouvez pas dériver votre propre type d'exception de `Platform::Exception`. Pour lever une exception personnalisée, utilisez un HRESULT défini par l'utilisateur pour construire un objet `COMException` .

Le tableau ci-dessous répertorie les exceptions standard.

|Name|HRESULT sous-jacent|Description|
|----------|------------------------|-----------------|
|COMException|*hresult défini par l’utilisateur*|Levée lorsqu'un HRESULT non reconnu est retourné d'un appel de méthode COM.|
|AccessDeniedException|E\_ACCESSDENIED|Levée lorsque l'accès est refusé à une ressource ou à une fonctionnalité.|
|ChangedStateException|E\_CHANGED\_ÉTAT|Levée lorsque les méthodes d'un itérateur de collection ou d'une vue de collection sont appelées après la modification d'une collection parente, invalidant ainsi les résultats de la méthode.|
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|Levée lorsqu'une classe COM n'a pas été inscrite.|
|DisconnectedException|RPC\_E\_DÉCONNECTÉ|Levée lorsqu'un objet est déconnecté de ses clients.|
|FailureException|E\_ÉCHOUER|Levée lorsqu'une opération échoue.|
|InvalidArgumentException|E\_INVALIDARG|Levée lorsque l'un des arguments fournis à une méthode n'est pas valide.|
|InvalidCastException|E\_NOINTERFACE|Levée lorsqu'un type ne peut pas être casté en un autre type.|
|NotImplementedException|E\_NOTIMPL|Levée si une méthode d'interface n'a pas été implémentée pour une classe.|
|NullReferenceException|E\_POINTEUR|Levée lors d'une tentative de suppression de la référence à une référence d'objet null.|
|ObjectDisposedException|RO\_E\_FERMÉ|Levée lorsqu'une opération est exécutée sur un objet supprimé.|
|OperationCanceledException|E\_ABANDONNER|Levée lorsqu'une opération est abandonnée.|
|OutOfBoundsException|E\_LIMITES|Levée lorsqu'une opération tente d'accéder aux données en dehors de la plage valide.|
|OutOfMemoryException|E\_OUTOFMEMORY|Levée en cas de mémoire insuffisante pour terminer l'opération.|
|WrongThreadException|RPC\_E\_INCORRECT\_THREAD|Levée lorsqu'un thread effectue un appel via un pointeur d'interface qui concerne un objet proxy qui n'appartient pas à l'apartment du thread.|

## <a name="hresult-and-message-properties"></a>Propriétés HRESULT et Message

Toutes les exceptions ont une propriété [HRESULT](platform-comexception-class.md#hresult) et une propriété [Message](platform-comexception-class.md#message) . La propriété [Exception::HResult](platform-exception-class.md#hresult) obtient la valeur HRESULT numérique sous-jacente de l'exception. La propriété [Exception::Message](platform-exception-class.md#message) obtient la chaîne fournie par le système qui décrit l'exception. Dans Windows 8, le message est uniquement disponible dans le débogueur et est en lecture seule. Cela signifie que vous ne pouvez pas le modifier quand vous levez de nouveau l'exception. Dans Windows 8.1, vous pouvez accéder à la chaîne de message par programmation et fournir un nouveau message si vous levez de nouveau l'exception. Des informations plus riches relatives aux piles des appels sont également disponibles dans le débogueur, notamment les piles des appels correspondant aux appels de méthode asynchrones.

### <a name="examples"></a>Exemples

Cet exemple montre comment lever une exception d’exécution de Windows pour les opérations synchrones :

[!code-cpp[cx_exceptions#01](codesnippet/CPP/exceptiontest/class1.cpp#01)]

L'exemple ci-dessous montre comment intercepter l'exception.

[!code-cpp[cx_exceptions#02](codesnippet/CPP/exceptiontest/class1.cpp#02)]

Pour intercepter les exceptions levées pendant une opération asynchrone, utilisez la classe de tâche et ajoutez une continuation de gestion des erreurs. La continuation de gestion des erreurs marshale les exceptions levées sur d'autres threads vers le thread appelant afin de gérer toutes les exceptions éventuelles en un seul point de votre code. Pour plus d’informations, consultez [programmation asynchrone en C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).

## <a name="unhandlederrordetected-event"></a>Événement UnhandledErrorDetected

Dans Windows 8.1 vous pouvez vous abonner à la [Windows::ApplicationModel](/uwp/api/windows.applicationmodel.core.icoreapplicationunhandlederror#Windows_ApplicationModel_Core_ICoreApplicationUnhandledError_UnhandledErrorDetected) un événement statique, ce qui permet d’accéder aux erreurs non gérées qui sont sur le point d’interrompre le processus. Quel que soit l’origine de l’erreur, il atteint ce gestionnaire en tant qu’un [Windows::ApplicationModel :: Core ::](/uwp/api/windows.applicationmodel.core.unhandlederror) objet qui est passé avec les arguments d’événement. Lorsque vous appelez `Propagate` sur l'objet, il crée et lève une exception `Platform::*Exception` dont le type correspond au code d'erreur. Dans les blocs catch, vous pouvez enregistrer l'état utilisateur, le cas échéant. Vous pouvez ensuite permettre au processus de se terminer en appelant `throw`, ou vous pouvez faire en sorte de restaurer le programme à un état connu. L'exemple suivant illustre le modèle de base :

Dans app.xaml.h :

```cpp
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);
```

Dans app.xaml.cpp :

```cpp
// Subscribe to the event, for example in the app class constructor:
Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected += ref new EventHandler<UnhandledErrorDetectedEventArgs^>(this, &App::OnUnhandledException);

// Event handler implementation:
void App::OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e)
{
    auto err = e->UnhandledError;

    if (!err->Handled) //Propagate has not been called on it yet.
{
     try
    {
        err->Propagate();
    }
    // Catch any specific exception types if you know how to handle them
    catch (AccessDeniedException^ ex)
    {
        // TODO: Log error and either take action to recover
        // or else re-throw exception to continue fail-fast
    }

}
```

### <a name="remarks"></a>Notes

C++ / c++ / CX n’utilise pas le `finally` clause.

## <a name="see-also"></a>Voir aussi

[Référence du langage Visual C++](visual-c-language-reference-c-cx.md)  
[Référence des espaces de noms](namespaces-reference-c-cx.md)  
