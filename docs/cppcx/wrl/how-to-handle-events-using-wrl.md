---
description: 'En savoir plus sur : Comment : gérer des événements à l’aide d’WRL'
title: "Comment : gérer les événements à l'aide de WRL"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
ms.openlocfilehash: b1be04c1356594e2dc2060d031f35d836ad277bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229182"
---
# <a name="how-to-handle-events-using-wrl"></a>Comment : gérer les événements à l'aide de WRL

Ce document montre comment utiliser le Windows Runtime C++ Template Library (WRL) pour s’abonner aux événements d’un objet Windows Runtime et les gérer.

Pour obtenir un exemple plus simple qui crée une instance de ce composant et récupère une valeur de propriété, consultez [Comment : activer et utiliser un composant Windows Runtime](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).

## <a name="subscribing-to-and-handling-events"></a>Abonnement et gestion des événements

Les étapes suivantes démarrent un `ABI::Windows::System::Threading::IDeviceWatcher` objet et utilisent des gestionnaires d’événements pour surveiller la progression. L' `IDeviceWatcher` interface vous permet d’énumérer des appareils de manière asynchrone, ou en arrière-plan, et de recevoir une notification lorsque des appareils sont ajoutés, supprimés ou modifiés. La fonction de [rappel](callback-function-wrl.md) est une partie importante de cet exemple car elle lui permet de spécifier des gestionnaires d’événements qui traitent les résultats de l’opération d’arrière-plan. L’exemple complet suit.

> [!WARNING]
> Bien que vous utilisiez généralement le Windows Runtime bibliothèque de modèles C++ dans une application plateforme Windows universelle, cet exemple utilise une application console comme illustration. Les fonctions telles que `wprintf_s` ne sont pas disponibles à partir d’une application plateforme Windows universelle. Pour plus d’informations sur les types et les fonctions que vous pouvez utiliser dans une application plateforme Windows universelle, consultez [fonctions CRT non prises en charge dans les applications plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) et [Win32 et com pour les applications UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

1. Include ( `#include` ) tout Windows Runtime requis, Windows Runtime bibliothèque de modèles c++ ou les en-têtes de la bibliothèque C++ standard.

   [!code-cpp[wrl-consume-event#2](../codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]

   `Windows.Devices.Enumeration.h` déclare les types requis pour énumérer les appareils.

   Nous vous recommandons d'utiliser la directive `using namespace` dans votre fichier .cpp pour rendre le code plus lisible.

2. Déclarez les variables locales pour l’application. Cet exemple stocke le nombre de périphériques et de jetons d’enregistrement énumérés qui lui permettent de se désabonner ultérieurement des événements.

   [!code-cpp[wrl-consume-event#7](../codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]

3. Initialisez le Windows Runtime.

   [!code-cpp[wrl-consume-event#3](../codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]

4. Créez un objet d' [événement](event-class-wrl.md) qui synchronise l’achèvement du processus d’énumération avec l’application principale.

   [!code-cpp[wrl-consume-event#4](../codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]

   > [!NOTE]
   > Cet événement est destiné à une démonstration uniquement dans le cadre d’une application console. Cet exemple utilise l’événement pour s’assurer qu’une opération asynchrone se termine avant la fermeture de l’application. Dans la plupart des applications, vous n’avez généralement pas à attendre que les opérations asynchrones se terminent.

5. Créez une fabrique d’activation pour l' `IDeviceWatcher` interface.

   [!code-cpp[wrl-consume-event#5](../codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]

   Le Windows Runtime utilise des noms qualifiés complets pour identifier les types. Le `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation` paramètre est une chaîne fournie par le Windows Runtime et contient le nom de classe d’exécution requis.

6. Créer l’objet `IDeviceWatcher`.

   [!code-cpp[wrl-consume-event#6](../codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]

7. Utilisez la `Callback` fonction pour vous abonner `Added` aux `EnumerationCompleted` événements, et `Stopped` .

   [!code-cpp[wrl-consume-event#8](../codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]

   Le `Added` Gestionnaire d’événements incrémente le nombre d’appareils énumérés. Il arrête le processus d’énumération une fois que dix appareils ont été détectés.

   Le `Stopped` Gestionnaire d’événements supprime les gestionnaires d’événements et définit l’événement d’achèvement.

   Le `EnumerationCompleted` Gestionnaire d’événements arrête le processus d’énumération. Nous prenons en charge cet événement au cas où il y aurait moins de dix appareils.

   > [!TIP]
   > Cet exemple utilise une expression lambda pour définir les rappels. Vous pouvez également utiliser des objets de fonction (functors), des pointeurs de fonction ou des objets [std :: function](../../standard-library/function-class.md) . Pour plus d’informations sur les expressions lambda, consultez [expressions lambda](../../cpp/lambda-expressions-in-cpp.md).

8. Démarrez le processus d’énumération.

   [!code-cpp[wrl-consume-event#9](../codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]

9. Attendez la fin du processus d’énumération, puis imprimez un message. Tous les objets `ComPtr` et RAII quittent la portée et sont libérés automatiquement.

   [!code-cpp[wrl-consume-event#10](../codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]

Voici l’exemple complet :

[!code-cpp[wrl-consume-event#1](../codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le, puis collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `wrl-consume-events.cpp` , puis exécutez la commande suivante dans une fenêtre d' **invite de commandes Visual Studio** .

`cl.exe wrl-consume-events.cpp runtimeobject.lib`

## <a name="see-also"></a>Voir aussi

[Bibliothèque de modèles Windows Runtime C++ (WRL)](windows-runtime-cpp-template-library-wrl.md)
