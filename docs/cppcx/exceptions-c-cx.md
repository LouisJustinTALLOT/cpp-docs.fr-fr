---
description: 'En savoir plus sur : exceptions (C++/CX)'
title: Exceptions (C++/CX)
ms.date: 07/02/2019
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
ms.openlocfilehash: 9bc04febf0d4b13a635ded6807e0cc77654dfdb0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341943"
---
# <a name="exceptions-ccx"></a>Exceptions (C++/CX)

La gestion des erreurs en C++/CX est basée sur les exceptions. Au niveau le plus fondamental, Windows Runtime composants signalent les erreurs en tant que valeurs HRESULT. En C++/CX, ces valeurs sont converties en exceptions fortement typées qui contiennent une valeur HRESULT et une description de chaîne à laquelle vous pouvez accéder par programme.  Les exceptions sont implémentées en tant **`ref class`** que qui dérive de `Platform::Exception` .  L'espace de noms `Platform` définit des classes d'exception distinctes pour les valeurs HRESULT les plus courantes. Toutes les autres valeurs sont indiquées via la classe `Platform::COMException` . Toutes les classes d'exceptions ont un champ de [Exception::HResult](platform-exception-class.md#hresult) qui peut être utilisé pour récupérer le HRESULT d'origine. Vous pouvez également examiner les informations de pile d’appels pour le code utilisateur dans le débogueur qui peut aider à identifier la source d’origine de l’exception, même si elle provient d’un code écrit dans un autre langage que C++.

## <a name="exceptions"></a>Exceptions

Dans votre programme C++, vous pouvez lever et intercepter une exception qui provient d’une opération Windows Runtime, d’une exception dérivée de `std::exception` ou d’un type défini par l’utilisateur. Vous devez lever une exception Windows Runtime uniquement lorsqu’elle franchira la limite ABI (application binary interface), par exemple, lorsque le code qui intercepte votre exception est écrit en JavaScript. Lorsqu’une exception C++ non Windows Runtime atteint la limite ABI, l’exception est convertie en `Platform::FailureException` exception, qui représente une E_FAIL HRESULT. Pour plus d'informations sur l'ABI, consultez [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Vous pouvez déclarer [Platform :: exception](platform-exception-class.md) en utilisant l’un des deux constructeurs qui acceptent un paramètre HRESULT ou un paramètre HRESULT et un paramètre [Platform :: String](platform-string-class.md)^ qui peut être passé sur l’Abi à n’importe quel Windows Runtime application qui le gère. Vous pouvez aussi déclarer une exception à l'aide de l'une des deux surcharges de méthode [Exception::CreateException](platform-exception-class.md#createexception) qui acceptent un paramètre HRESULT ou un paramètre HRESULT et un paramètre `Platform::String^` .

## <a name="standard-exceptions"></a>Exceptions standard

C++/CX prend en charge un ensemble d’exceptions standard qui représentent des erreurs HRESULT typiques. Chaque exception standard dérive de [Platform::COMException](platform-comexception-class.md), qui dérive à son tour de `Platform::Exception`. Lorsque vous levez une exception à travers la limite ABI, vous devez lever l'une des exceptions standard.

Vous ne pouvez pas dériver votre propre type d'exception de `Platform::Exception`. Pour lever une exception personnalisée, utilisez un HRESULT défini par l'utilisateur pour construire un objet `COMException` .

Le tableau ci-dessous répertorie les exceptions standard.

|Nom|HRESULT sous-jacent|Description|
|----------|------------------------|-----------------|
|COMException|*hresult défini par l’utilisateur*|Levée lorsqu'un HRESULT non reconnu est retourné d'un appel de méthode COM.|
|AccessDeniedException|\_ACCESSDENIED E|Levée lorsque l'accès est refusé à une ressource ou à une fonctionnalité.|
|ChangedStateException|E \_ modification de l' \_ État|Levée lorsque les méthodes d'un itérateur de collection ou d'une vue de collection sont appelées après la modification d'une collection parente, invalidant ainsi les résultats de la méthode.|
|ClassNotRegisteredException|REGDB \_ E \_ CLASSNOTREG|Levée lorsqu'une classe COM n'a pas été inscrite.|
|DisconnectedException|RPC \_ E \_ déconnecté|Levée lorsqu'un objet est déconnecté de ses clients.|
|FailureException|E \_ échec|Levée lorsqu'une opération échoue.|
|InvalidArgumentException|E \_ INVALIDARG|Levée lorsque l'un des arguments fournis à une méthode n'est pas valide.|
|InvalidCastException|E \_ NOinterface|Levée lorsqu'un type ne peut pas être casté en un autre type.|
|NotImplementedException|\_NOTIMPL E|Levée si une méthode d'interface n'a pas été implémentée pour une classe.|
|NullReferenceException|\_pointeur E|Levée lors d'une tentative de suppression de la référence à une référence d'objet null.|
|ObjectDisposedException|RO \_ E \_ fermé|Levée lorsqu'une opération est exécutée sur un objet supprimé.|
|OperationCanceledException|E \_ Abort|Levée lorsqu'une opération est abandonnée.|
|OutOfBoundsException|limites de l’E \_|Levée lorsqu'une opération tente d'accéder aux données en dehors de la plage valide.|
|OutOfMemoryException|\_OUTOFMEMORY E|Levée en cas de mémoire insuffisante pour terminer l'opération.|
|WrongThreadException|\_thread RPC E \_ incorrect \_|Levée lorsqu'un thread effectue un appel via un pointeur d'interface qui concerne un objet proxy qui n'appartient pas à l'apartment du thread.|

## <a name="hresult-and-message-properties"></a>Propriétés HRESULT et Message

Toutes les exceptions ont une propriété [HRESULT](platform-comexception-class.md#hresult) et une propriété [Message](platform-comexception-class.md#message) . La propriété [Exception::HResult](platform-exception-class.md#hresult) obtient la valeur HRESULT numérique sous-jacente de l'exception. La propriété [Exception::Message](platform-exception-class.md#message) obtient la chaîne fournie par le système qui décrit l'exception. Dans Windows 8, le message est disponible uniquement dans le débogueur et est en lecture seule. Cela signifie que vous ne pouvez pas le modifier quand vous levez de nouveau l'exception. Dans Windows 8.1, vous pouvez accéder à la chaîne de message par programmation et fournir un nouveau message si vous levez de nouveau l'exception. Des informations plus riches relatives aux piles des appels sont également disponibles dans le débogueur, notamment les piles des appels correspondant aux appels de méthode asynchrones.

### <a name="examples"></a>Exemples

Cet exemple montre comment lever une exception Windows Runtime pour les opérations synchrones :

[!code-cpp[cx_exceptions#01](codesnippet/CPP/exceptiontest/class1.cpp#01)]

L'exemple ci-dessous montre comment intercepter l'exception.

[!code-cpp[cx_exceptions#02](codesnippet/CPP/exceptiontest/class1.cpp#02)]

Pour intercepter les exceptions levées pendant une opération asynchrone, utilisez la classe de tâche et ajoutez une continuation de gestion des erreurs. La continuation de gestion des erreurs marshale les exceptions levées sur d'autres threads vers le thread appelant afin de gérer toutes les exceptions éventuelles en un seul point de votre code. Pour plus d’informations sur la programmation asynchrone, consultez [Programmation asynchrone en C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).

## <a name="unhandlederrordetected-event"></a>Événement UnhandledErrorDetected

Dans Windows 8.1 vous pouvez vous abonner à l’événement statique [Windows :: ApplicationModel :: Core :: CoreApplication :: UnhandledErrorDetected](/uwp/api/windows.applicationmodel.core.icoreapplicationunhandlederror.unhandlederrordetected) , qui permet d’accéder à des erreurs non gérées qui sont sur le paragraphe d’éteindre le processus. Indépendamment de l’origine de l’erreur, il atteint ce gestionnaire en tant qu’objet [Windows::ApplicationModel::Core::UnhandledError](/uwp/api/windows.applicationmodel.core.unhandlederror) passé avec les arguments d’événement. Lorsque vous appelez `Propagate` sur l'objet, il crée et lève une exception `Platform::*Exception` dont le type correspond au code d'erreur. Dans les blocs catch, vous pouvez enregistrer l’état utilisateur si nécessaire, puis autoriser le processus à se terminer en appelant **`throw`** , ou faire une opération pour réintégrer le programme à un état connu. L'exemple suivant illustre le modèle de base :

Dans App. Xaml. h :

```cpp
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);
```

Dans App. Xaml. cpp :

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

C++/CX n’utilise pas la **`finally`** clause.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++/CX](visual-c-language-reference-c-cx.md)<br/>
[Référence des espaces de noms](namespaces-reference-c-cx.md)
