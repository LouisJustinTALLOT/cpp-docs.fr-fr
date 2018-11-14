---
title: 'Procédure pas à pas : connexion à l’aide de tâches et de requêtes HTTP XML'
ms.date: 11/04/2016
helpviewer_keywords:
- connecting to web services, UWP apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
ms.openlocfilehash: 36769fa531decaee81c73a4751f5c6ed24008ffc
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51525012"
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>Procédure pas à pas : connexion à l’aide de tâches et de requêtes HTTP XML

Cet exemple montre comment utiliser le [IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2) et [IXMLHTTPRequest2Callback](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2callback) interfaces avec des tâches pour envoyer des demandes HTTP GET et POST à un service web dans un Universal Windows Platform (UWP ) app. En combinant `IXMLHTTPRequest2` avec des tâches, vous pouvez écrire du code qui s’adapte à d’autres tâches. Par exemple, vous pouvez utiliser la tâche de téléchargement dans le cadre d’une chaîne des tâches. La tâche de téléchargements peut également répondre quand le travail est annulé.

> [!TIP]
>  Vous pouvez également utiliser le SDK C++ REST pour effectuer des requêtes HTTP à partir d’une application UWP à l’aide d’application C++ ou d’un application C++ de bureau. Pour plus d’informations, consultez [SDK C++ REST (nom de code « Casablanca »)](https://github.com/Microsoft/cpprestsdk).

Pour plus d’informations sur les tâches, consultez [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Pour plus d’informations sur l’utilisation des tâches dans une application UWP, consultez [programmation asynchrone en C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) et [création d’opérations asynchrones en C++ pour les applications UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

Ce document explique d'abord comment créer une `HttpRequest` et ses classes de prise en charge. Il montre ensuite comment utiliser cette classe à partir d’une application UWP qui utilise C++ et XAML.

Pour obtenir un exemple qui utilise `IXMLHTTPRequest2` mais ne pas utiliser des tâches, consultez [Guide de démarrage rapide : connexion à l’aide de XML HTTP Request (IXMLHTTPRequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\)).

> [!TIP]
>  `IXMLHTTPRequest2` et `IXMLHTTPRequest2Callback` sont les interfaces que nous recommandons d’utiliser dans une application UWP. Vous pouvez également adapter cet exemple pour l'utilisation dans une application de bureau.

## <a name="prerequisites"></a>Prérequis

## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>Définition des classes HttpRequest, HttpRequestBuffersCallback et HttpRequestStringCallback

Lorsque vous utilisez l'interface `IXMLHTTPRequest2` pour créer des requêtes Web via HTTP, vous implémentez l'interface `IXMLHTTPRequest2Callback` pour recevoir la réponse du serveur et réagir à d'autres événements. Cet exemple définit la classe `HttpRequest` pour créer des applications Web, et les classes `HttpRequestBuffersCallback` et `HttpRequestStringCallback` afin de traiter des réponses. Les classes `HttpRequestBuffersCallback` et `HttpRequestStringCallback` prennent en charge la classe `HttpRequest` ; vous travaillez uniquement avec la classe `HttpRequest` du code d'application.

Les méthodes `GetAsync`, `PostAsync` de la classe `HttpRequest` vous permettent de démarrer respectivement les opérations HTTP GET et POST. Ces méthodes utilisent la classe `HttpRequestStringCallback` pour lire la réponse du serveur comme une chaîne. Les méthodes `SendAsync` et `ReadAsync` vous permettent de transmettre un grand contenu en gros fragments. Ces méthodes retournent chaque [concurrency::task](../../parallel/concrt/reference/task-class.md) pour représenter l’opération. Les méthodes `GetAsync` et `PostAsync` produisent la valeur de `task<std::wstring>`, où la partie `wstring` représente la réponse du serveur. Les méthodes `SendAsync` et `ReadAsync` produisent des valeurs `task<void>` ; ces tâches se terminent lorsque les opérations d’envoi et de lecture se terminent.

Étant donné que le `IXMLHTTPRequest2` interfaces agissent de façon asynchrone, cet exemple utilise [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) pour créer une tâche qui se termine une fois que l’objet de rappel ou annule l’opération de téléchargement. La classe `HttpRequest` crée une continuation basée sur des tâches depuis cette tâche afin de définir le résultat final. La classe `HttpRequest` utilise une continuation basée sur des tâches pour garantir que la tâche de continuation s"exécute même si la tâche précédente génère une erreur ou est annulée. Pour plus d’informations sur les continuations basées sur des tâches, consultez [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

Pour prendre en charge l'annulation, les classes `HttpRequest`, `HttpRequestBuffersCallback`, et `HttpRequestStringCallback` utilisent des jetons d'annulation. Le `HttpRequestBuffersCallback` et `HttpRequestStringCallback` classes utilisent le [Concurrency::cancellation_token :: register_callback](reference/cancellation-token-class.md#register_callback) méthode pour permettre à l’événement d’achèvement de tâche répondre à l’annulation. Ce rappel d'annulation abandonne le téléchargement. Pour plus d’informations sur l’annulation, consultez [l’annulation](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

#### <a name="to-define-the-httprequest-class"></a>Pour définir la classe HttpRequest

1. Utiliser le Visual C++ **application vide (XAML)** modèle pour créer un projet d’application XAML vierge. Cet exemple nomme le projet `UsingIXMLHTTPRequest2`.

1. Ajoutez un fichier d'en-tête au projet qui sera nommé HttpRequest.h et un fichier source nommé HttpRequest.cpp.

1. Dans pch.h, ajoutez ce code :

   [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]

1. Dans HttpRequest.h, ajoutez ce code :

   [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]

1. Dans HttpRequest.cpp, ajoutez ce code :

   [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]

## <a name="using-the-httprequest-class-in-a-uwp-app"></a>À l’aide de la classe HttpRequest dans une application UWP

Cette section montre comment utiliser le `HttpRequest` classe dans une application UWP. L'application fournit une zone d'entrée qui définit une ressource URL, et des commandes de bouton qui effectuent des opérations GET et POST, et un bouton de commande qui annule l'opération en cours.

#### <a name="to-use-the-httprequest-class"></a>Pour utiliser la classe HttpRequest

1. Dans MainPage.xaml, définissez le [StackPanel](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx) élément comme suit.

   [!code-xml[concrt-using-ixhr2#A1](../../parallel/concrt/codesnippet/xaml/walkthrough-connecting-using-tasks-and-xml-http-requests_4.xaml)]

2. Dans MainPage.xaml.h, ajoutez la directive `#include`:

   [!code-cpp[concrt-using-ixhr2#A2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_5.h)]

3. Dans MainPage.xaml.h, ajoutez ces variables membres `private` à la classe `MainPage` :

   [!code-cpp[concrt-using-ixhr2#A3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_6.h)]

4. Dans MainPage.xaml.h, déclarez la méthode `private` `ProcessHttpRequest` :

   [!code-cpp[concrt-using-ixhr2#A4](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_7.h)]

5. Dans MainPage.xaml.cpp, ajoutez ces instructions `using` :

   [!code-cpp[concrt-using-ixhr2#A5](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_8.cpp)]

6. Dans MainPage.xaml.cpp, implémentez les méthodes `GetButton_Click`, `PostButton_Click`, et `CancelButton_Click` de la classe `MainPage`.

   [!code-cpp[concrt-using-ixhr2#A6](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_9.cpp)]

   > [!TIP]
   > Si votre application ne nécessite pas de prise en charge l’annulation, passez [concurrency::cancellation_token :: none](reference/cancellation-token-class.md#none) à la `HttpRequest::GetAsync` et `HttpRequest::PostAsync` méthodes.

1. Dans MainPage.xaml.cpp, implémentez la méthode `MainPage::ProcessHttpRequest`.

   [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]

8. Dans les propriétés du projet, sous **l’éditeur de liens**, **entrée**, spécifiez `shcore.lib` et `msxml6.lib`.

Voici l'application en cours d'exécution :

![L’application Windows Runtime en cours d’exécution](../../parallel/concrt/media/concrt_usingixhr2.png "concrt_usingixhr2")

## <a name="next-steps"></a>Étapes suivantes

[Procédures pas à pas relatives au runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-walkthroughs.md)

## <a name="see-also"></a>Voir aussi

[Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)<br/>
[Programmation asynchrone en C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)<br/>
[Création d’opérations asynchrones dans C++ pour les applications UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)<br/>
[Démarrage rapide : Connexion à l’aide de XML HTTP Request (IXMLHTTPRequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\))
[task, classe (Runtime d’accès concurrentiel)](../../parallel/concrt/reference/task-class.md)<br/>
[task_completion_event, classe](../../parallel/concrt/reference/task-completion-event-class.md)
