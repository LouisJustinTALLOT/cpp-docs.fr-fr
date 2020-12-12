---
description: 'En savoir plus sur : Comment : effectuer des opérations asynchrones à l’aide de WRL'
title: "Comment : terminer une opération asynchrone à l'aide de WRL"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
ms.openlocfilehash: f8c929d737f113d995b5d171896517b3d94a6aa4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124590"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>Comment : terminer une opération asynchrone à l'aide de WRL

Ce document montre comment utiliser le Windows Runtime C++ Template Library (WRL) pour démarrer des opérations asynchrones et effectuer un travail lorsque les opérations se terminent.

Ce document présente deux exemples. Le premier exemple démarre un minuteur asynchrone et attend que le minuteur expire. Dans cet exemple, vous spécifiez l’action asynchrone quand vous créez l’objet de minuteur. Le deuxième exemple exécute un thread de travail en arrière-plan. Cet exemple montre comment utiliser une méthode Windows Runtime qui retourne une `IAsyncInfo` interface. La fonction de [rappel](callback-function-wrl.md) est une partie importante des deux exemples, car elle leur permet de spécifier un gestionnaire d’événements pour traiter les résultats des opérations asynchrones.

Pour obtenir un exemple plus simple qui crée une instance d’un composant et récupère une valeur de propriété, consultez [Comment : activer et utiliser un composant Windows Runtime](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).

> [!TIP]
> Ces exemples utilisent des expressions lambda pour définir les rappels. Vous pouvez également utiliser des objets de fonction (functors), des pointeurs de fonction ou des objets [std :: function](../../standard-library/function-class.md) . Pour plus d’informations sur les expressions lambda C++, consultez [expressions lambda](../../cpp/lambda-expressions-in-cpp.md).

## <a name="example-working-with-a-timer"></a>Exemple : utilisation d’un minuteur

Les étapes suivantes démarrent un minuteur asynchrone et attendent que le minuteur expire. L’exemple complet suit.

> [!WARNING]
> Bien que vous utilisiez généralement le Windows Runtime bibliothèque de modèles C++ dans une application plateforme Windows universelle (UWP), cet exemple utilise une application console comme illustration. Les fonctions telles que `wprintf_s` ne sont pas disponibles à partir d’une application UWP. Pour plus d’informations sur les types et les fonctions que vous pouvez utiliser dans une application UWP, consultez [fonctions CRT non prises en charge dans les applications plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) et [Win32 et com pour les applications UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

1. Include ( `#include` ) tout Windows Runtime requis, Windows Runtime bibliothèque de modèles c++ ou les en-têtes de la bibliothèque C++ standard.

   [!code-cpp[wrl-consume-async#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]

   `Windows.System.Threading.h` déclare les types qui sont requis pour utiliser un minuteur asynchrone.

   Nous vous recommandons d'utiliser la directive `using namespace` dans votre fichier .cpp pour rendre le code plus lisible.

2. Initialisez le Windows Runtime.

   [!code-cpp[wrl-consume-async#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]

3. Créez une fabrique d’activation pour l' `ABI::Windows::System::Threading::IThreadPoolTimer` interface.

   [!code-cpp[wrl-consume-async#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]

   Le Windows Runtime utilise des noms qualifiés complets pour identifier les types. Le `RuntimeClass_Windows_System_Threading_ThreadPoolTimer` paramètre est une chaîne fournie par le Windows Runtime et contient le nom de classe d’exécution requis.

4. Créez un objet d' [événement](event-class-wrl.md) qui synchronise le rappel de la minuterie avec l’application principale.

   [!code-cpp[wrl-consume-async#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]

   > [!NOTE]
   > Cet événement est destiné à une démonstration uniquement dans le cadre d’une application console. Cet exemple utilise l’événement pour s’assurer qu’une opération asynchrone se termine avant la fermeture de l’application. Dans la plupart des applications, vous n’avez généralement pas à attendre que les opérations asynchrones se terminent.

5. Créez un `IThreadPoolTimer` objet qui expire au bout de deux secondes. Utilisez la `Callback` fonction pour créer le gestionnaire d’événements (un `ABI::Windows::System::Threading::ITimerElapsedHandler` objet).

   [!code-cpp[wrl-consume-async#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]

6. Imprimez un message sur la console et attendez la fin du rappel de la minuterie. Tous les objets `ComPtr` et RAII quittent la portée et sont libérés automatiquement.

   [!code-cpp[wrl-consume-async#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]

Voici l’exemple complet :

[!code-cpp[wrl-consume-async#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]

### <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le, puis collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `wrl-consume-async.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

`cl.exe wrl-consume-async.cpp runtimeobject.lib`

## <a name="example-working-with-a-background-thread"></a>Exemple : utilisation d’un thread d’arrière-plan

Les étapes suivantes démarrent un thread de travail et définissent l’action effectuée par ce thread. L’exemple complet suit.

> [!TIP]
> Cet exemple montre comment utiliser l' `ABI::Windows::Foundation::IAsyncAction` interface. Vous pouvez appliquer ce modèle à toute interface qui implémente `IAsyncInfo` : `IAsyncAction` , `IAsyncActionWithProgress` , `IAsyncOperation` et `IAsyncOperationWithProgress` .

1. Include ( `#include` ) tout Windows Runtime requis, Windows Runtime bibliothèque de modèles c++ ou les en-têtes de la bibliothèque C++ standard.

   [!code-cpp[wrl-consume-asyncOp#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]

   Windows.SysTEM. Threading. h déclare les types qui sont requis pour utiliser un thread de travail.

   Nous vous recommandons d’utiliser la `using namespace` directive dans votre fichier. cpp pour rendre le code plus lisible.

2. Initialisez le Windows Runtime.

   [!code-cpp[wrl-consume-asyncOp#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]

3. Créez une fabrique d’activation pour l' `ABI::Windows::System::Threading::IThreadPoolStatics` interface.

   [!code-cpp[wrl-consume-asyncOp#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]

4. Créez un objet d' [événement](event-class-wrl.md) qui synchronise l’achèvement du thread de travail avec l’application principale.

   [!code-cpp[wrl-consume-asyncOp#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]

   > [!NOTE]
   > Cet événement est destiné à une démonstration uniquement dans le cadre d’une application console. Cet exemple utilise l’événement pour s’assurer qu’une opération asynchrone se termine avant la fermeture de l’application. Dans la plupart des applications, vous n’avez généralement pas à attendre que les opérations asynchrones se terminent.

5. Appelez la `IThreadPoolStatics::RunAsync` méthode pour créer un thread de travail. Utilisez la `Callback` fonction pour définir l’action.

   [!code-cpp[wrl-consume-asyncOp#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]

   La `IsPrime` fonction est définie dans l’exemple complet qui suit.

6. Imprimez un message sur la console et attendez que le thread se termine. Tous les objets `ComPtr` et RAII quittent la portée et sont libérés automatiquement.

   [!code-cpp[wrl-consume-asyncOp#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]

Voici l’exemple complet :

[!code-cpp[wrl-consume-asyncOp#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]

### <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le, puis collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `wrl-consume-asyncOp.cpp` , puis exécutez la commande suivante dans une fenêtre d' **invite de commandes Visual Studio** .

`cl.exe wrl-consume-asyncOp.cpp runtimeobject.lib`

## <a name="see-also"></a>Voir aussi

[Bibliothèque de modèles Windows Runtime C++ (WRL)](windows-runtime-cpp-template-library-wrl.md)
