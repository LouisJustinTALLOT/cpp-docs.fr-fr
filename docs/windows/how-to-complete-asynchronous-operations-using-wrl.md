---
title: 'Comment : terminer une opération asynchrone à l’aide de WRL | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 29b892f3e120db183082d6af97f9374f89e9e647
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643054"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>Comment : terminer une opération asynchrone à l'aide de WRL
Ce document montre comment utiliser la bibliothèque de modèles C++ (WRL) de Windows Runtime pour démarrer des opérations asynchrones et effectuer des actions lorsque les opérations se terminent.  
  
 Ce document montre deux exemples. Le premier exemple démarre un minuteur asynchrone et attend l’expiration du minuteur. Dans cet exemple, vous spécifiez l’action asynchrone lorsque vous créez l’objet de minuteur. Le deuxième exemple s’exécute un thread de travail en arrière-plan. Cet exemple montre comment utiliser une méthode Windows Runtime qui retourne un `IAsyncInfo` interface. Le [rappel](../windows/callback-function-windows-runtime-cpp-template-library.md) fonction est une partie importante de ces deux exemples, car il leur permet de spécifier un gestionnaire d’événements pour traiter les résultats des opérations asynchrones.  
  
 Pour obtenir un exemple plus simple qui crée une instance d’un composant et récupère une valeur de propriété, consultez [Comment : activer et utiliser un composant d’exécution Windows](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).  
  
> [!TIP]
>  Ces exemples utilisent des expressions lambda pour définir les rappels. Vous pouvez également utiliser des objets de fonction (functors), des pointeurs de fonction, ou [std::function](../standard-library/function-class.md) objets. Pour plus d’informations sur les expressions lambda en C++, consultez [Expressions Lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## <a name="example-working-with-a-timer"></a>Exemple : Utilisation avec un minuteur  
 Les étapes suivantes démarre une minuterie asynchrone et attendre l’expiration du minuteur. L’exemple complet suit.  
  
> [!WARNING]
>  Bien que vous utilisez généralement la bibliothèque de modèles Windows Runtime C++ dans une application de plateforme universelle Windows (UWP), cet exemple utilise une application console à titre d’illustration. Les fonctions telles que `wprintf_s` ne sont pas disponibles à partir d’une application UWP. Pour plus d’informations sur les types et les fonctions que vous pouvez utiliser dans une application UWP, consultez [fonctions CRT non prises en charge dans les applications de plateforme Windows universelle](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) et [Win32 et COM pour les applications UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).  
  
1.  Inclure (`#include`) toute requise Windows Runtime, bibliothèque de modèles C++ Windows Runtime ou les en-têtes de bibliothèque C++ Standard.  
  
     [!code-cpp[wrl-consume-async#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]  
  
     `Windows.System.Threading.h` déclare les types qui sont requises pour utiliser un minuteur asynchrone.  
  
     Nous vous recommandons d'utiliser la directive `using namespace` dans votre fichier .cpp pour rendre le code plus lisible.  
  
2.  Initialiser le Runtime de Windows.  
  
     [!code-cpp[wrl-consume-async#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]  
  
3.  Créer une fabrique d’activation pour le `ABI::Windows::System::Threading::IThreadPoolTimer` interface.  
  
     [!code-cpp[wrl-consume-async#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]  
  
     Le Runtime Windows utilise des noms qualifiés complets pour identifier les types. Le `RuntimeClass_Windows_System_Threading_ThreadPoolTimer` paramètre est une chaîne qui est fournie par le Runtime Windows et contient le nom de classe runtime requis.  
  
4.  Créer un [événement](../windows/event-class-windows-runtime-cpp-template-library.md) objet qui synchronise le rappel de minuterie à l’application principale.  
  
     [!code-cpp[wrl-consume-async#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]  
  
    > [!NOTE]
    >  Cet événement est de démonstration uniquement dans le cadre d’une application console. Cet exemple utilise l’événement pour vous assurer qu’une opération asynchrone se termine avant l’application se ferme. Dans la plupart des applications, vous en général, n’attendez pas les opérations asynchrones se terminent.  
  
5.  Créer un `IThreadPoolTimer` objet expire au bout de deux secondes. Utilisez le `Callback` fonction permettant de créer le Gestionnaire d’événements (une `ABI::Windows::System::Threading::ITimerElapsedHandler` objet).  
  
     [!code-cpp[wrl-consume-async#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]  
  
6.  Imprimer un message à la console et attendre le rappel de minuterie à terminer. Tous les objets `ComPtr` et RAII quittent la portée et sont libérés automatiquement.  
  
     [!code-cpp[wrl-consume-async#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]  
  
 Voici un exemple complet :  
  
 [!code-cpp[wrl-consume-async#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]  
  
### <a name="compiling-the-code"></a>Compilation du code  
 Pour compiler le code, copiez-le et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `wrl-consume-async.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 `cl.exe wrl-consume-async.cpp runtimeobject.lib` 
  
## <a name="example-working-with-a-background-thread"></a>Exemple : Utilisation avec un Thread d’arrière-plan  
 Les étapes suivantes démarrer un thread de travail et définissent l’action effectuée par ce thread. L’exemple complet suit.  
  
> [!TIP]
>  Cet exemple montre comment travailler avec les `ABI::Windows::Foundation::IAsyncAction` interface. Vous pouvez appliquer ce modèle à n’importe quelle interface qui implémente `IAsyncInfo`: `IAsyncAction`, `IAsyncActionWithProgress`, `IAsyncOperation`, et `IAsyncOperationWithProgress`.  
  
1.  Inclure (`#include`) toute requise Windows Runtime, bibliothèque de modèles C++ Windows Runtime ou les en-têtes de bibliothèque C++ Standard.  
  
     [!code-cpp[wrl-consume-asyncOp#2](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]  
  
     Windows.System.Threading.h déclare les types qui sont requises pour utiliser un thread de travail.  
  
     Nous vous recommandons d’utiliser la `using namespace` directive dans votre fichier .cpp pour rendre le code plus lisible.  
  
2.  Initialiser le Runtime de Windows.  
  
     [!code-cpp[wrl-consume-asyncOp#3](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]  
  
3.  Créer une fabrique d’activation pour le `ABI::Windows::System::Threading::IThreadPoolStatics` interface.  
  
     [!code-cpp[wrl-consume-asyncOp#4](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]  
  
4.  Créer un [événement](../windows/event-class-windows-runtime-cpp-template-library.md) objet qui synchronise l’achèvement du thread de travail à l’application principale.  
  
     [!code-cpp[wrl-consume-asyncOp#5](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]  
  
    > [!NOTE]
    >  Cet événement est de démonstration uniquement dans le cadre d’une application console. Cet exemple utilise l’événement pour vous assurer qu’une opération asynchrone se termine avant l’application se ferme. Dans la plupart des applications, vous en général, n’attendez pas les opérations asynchrones se terminent.  
  
5.  Appelez le `IThreadPoolStatics::RunAsync` méthode pour créer un thread de travail. Utilisez le `Callback` fonction pour définir l’action.  
  
     [!code-cpp[wrl-consume-asyncOp#6](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]  
  
     Le `IsPrime` fonction est définie dans l’exemple complet qui suit.  
  
6.  Imprimer un message à la console et attendre que le thread terminer. Tous les objets `ComPtr` et RAII quittent la portée et sont libérés automatiquement.  
  
     [!code-cpp[wrl-consume-asyncOp#7](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]  
  
 Voici un exemple complet :  
  
 [!code-cpp[wrl-consume-asyncOp#1](../windows/codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]  
  
### <a name="compiling-the-code"></a>Compilation du code  
 Pour compiler le code, copiez-le et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `wrl-consume-asyncOp.cpp` , puis exécutez la commande suivante une **invite de commandes Visual Studio** fenêtre.  
  
 `cl.exe wrl-consume-asyncOp.cpp runtimeobject.lib`  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque de modèles Windows Runtime C++ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)