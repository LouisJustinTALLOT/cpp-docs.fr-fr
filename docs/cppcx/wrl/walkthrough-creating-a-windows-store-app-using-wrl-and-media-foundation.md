---
title: 'Procédure pas à pas : Création d’une application UWP à l’aide de WRL et Media Foundation'
ms.date: 04/23/2019
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: ac2c16fb94646af7445d41010253967be126636a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498306"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>Procédure pas à pas : Création d’une application UWP à l’aide de WRL et Media Foundation

> [!NOTE]
> Pour les nouveaux composants et applications UWP, nous vous recommandons d’utiliser [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), une nouvelle projection de langage c++ 17 standard pour les API Windows Runtime. C++/WinRT est disponible dans le kit de développement logiciel (SDK) Windows 10 à partir de la version 1803. C++/WinRT est entièrement implémenté dans les fichiers d’en-tête et est conçu pour vous fournir un accès de première classe à l’API Windows moderne.

Dans ce didacticiel, vous allez apprendre à utiliser la bibliothèque de C++ modèles Windows Runtime (WRL) pour créer une application plateforme Windows universelle (UWP) qui utilise [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk).

Cet exemple crée une transformation Media Fondation personnalisée qui applique un effet de nuances de gris aux images capturées par une webcam. L'application utilise C++ pour définir la transformation personnalisée et C# pour utiliser le composant afin de transformer les images capturées.

> [!NOTE]
> Au lieu de C#, vous pouvez également utiliser JavaScript, Visual Basic, ou C++ pour recourir au composant de transformation personnalisée.

Dans la plupart des cas, vous C++pouvez utiliser/CX pour créer des Windows Runtime. Toutefois, vous devez parfois utiliser le WRL. Par exemple, lorsque vous créez une extension de média pour Microsoft Media Foundation, vous devez créer un composant qui implémente à la fois les interfaces COM et Windows Runtime. Étant C++donné que/CX peut uniquement créer des objets Windows Runtime, pour créer une extension de média, vous devez utiliser WRL, car cela permet l’implémentation des interfaces COM et Windows Runtime.

> [!NOTE]
> Bien que cet exemple de code soit long, il montre le minimum nécessaire pour créer une transformation Media Foundation utile. Vous pouvez l'utiliser comme point de départ pour votre propre transformation personnalisée. Cet exemple est adapté de l' [exemple Media extensions](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096), qui utilise des extensions multimédias pour appliquer des effets à la vidéo, décoder la vidéo et créer des gestionnaires de schémas qui produisent des flux multimédias.

## <a name="prerequisites"></a>Prérequis

- Dans Visual Studio 2017 et versions ultérieures, la prise en charge UWP est un composant facultatif. Pour l’installer, ouvrez le Visual Studio Installer à partir du menu Démarrer de Windows et recherchez votre version de Visual Studio. Choisissez **modifier** , puis vérifiez que la vignette **développement plateforme Windows universelle** est cochée. Sous **composants facultatifs** , activez la case à cocher  **C++ outils pour UWP (V141)** pour Visual Studio 2017 ou  **C++ outils pour UWP (V142)** pour Visual Studio 2019. Vérifiez ensuite la version du SDK Windows que vous souhaitez utiliser. 

- Expérience du [Windows Runtime](/uwp/api/).

- Expérience avec COM.

- Une webcam.

## <a name="key-points"></a>Points clés

- Pour créer un composant Media Foundation personnalisé, utilisez un fichier de définition MIDL (Microsoft Interface Definition Language) pour définir une interface, implémentez celle-ci, puis rendez-la activable à partir d'autres composants.

- Les `namespace` attributs `runtimeclass` et et la valeur `NTDDI_WIN8`de l’attribut [version](/windows/win32/Midl/version) sont des parties importantes de la définition MIDL pour un composant Media Foundation qui utilise WRL.

- [Microsoft:: WRL:: RuntimeClass](runtimeclass-class.md) est la classe de base du composant Media Foundation personnalisé. La valeur d’énumération [Microsoft:: WRL:: RuntimeClassType:: WinRtClassicComMix](runtimeclasstype-enumeration.md) , fournie comme argument de modèle, marque la classe comme étant utilisée en tant que classe Windows Runtime et en tant que classe de Runtime com classique.

- La macro [inspectableclass,](inspectableclass-macro.md) implémente des fonctionnalités com de base telles que le décompte de références et la `QueryInterface` méthode, et définit le nom de la classe d’exécution et le niveau de confiance.

- Utilisez la classe Microsoft:: WRL::[module](module-class.md) pour implémenter des fonctions de point d’entrée dll telles que [DllGetActivationFactory](/windows/win32/winrt/functions), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)et [DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject).

- Liez votre DLL de composant à runtimeobject.lib. Spécifiez également [/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md) sur la ligne de l’éditeur de liens pour générer des métadonnées Windows.

- Utilisez des références de projet pour rendre les composants WRL accessibles aux applications UWP.

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>Pour utiliser WRL pour créer le composant de transformation Media Foundation nuances de gris

1. Dans Visual Studio, créez un projet de **solution vide** . Nommez le projet, par exemple, *MediaCapture*.

1. Ajoutez un projet **dll (Windows universel)** à la solution. Nommez le projet, par exemple, *GrayscaleTransform*.

1. Ajoutez un fichier **MIDL (. idl)** au projet. Nommez le fichier, par exemple, *GrayscaleTransform. idl*.

1. Ajoutez ce code à GrayscaleTransform. idl:

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. Utilisez le code suivant pour remplacer le contenu de `pch.h`:

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. Ajoutez un nouveau fichier d’en-tête au projet, `BufferLock.h`nommez-le, puis remplacez le contenu par le code suivant:

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h`n’est pas utilisé dans cet exemple. Vous pouvez le supprimer du projet si vous le souhaitez.

1. Utilisez le code suivant pour remplacer le contenu de `GrayscaleTransform.cpp`:

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. Ajoutez un nouveau fichier de définition de module au projet, nommez `GrayscaleTransform.def`-le, puis ajoutez le code suivant:

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. Utilisez le code suivant pour remplacer le contenu de `dllmain.cpp`:

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. Dans la boîte de dialogue **pages de propriétés** du projet, définissez les propriétés suivantes de l’éditeur de **liens** .

   1. Sous **entrée**, pour le **fichier de définition**de module `GrayScaleTransform.def`, spécifiez.

   1. En outre, sous entrée `runtimeobject.lib`, `mfuuid.lib`ajoutez, `mfplat.lib` et à la propriété **dépendances supplémentaires** .

   1. Sous **métadonnées Windows**, définissez **générer les métadonnées Windows** sur **Oui (/WINMD)** .

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>Pour utiliser le composant Media Foundation personnalisé à partir d’une C# application

1. Ajoutez un nouveau  **C# projet application vide (Windows universel)** à la `MediaCapture` solution. Nommez le projet, par exemple, *MediaCapture*.

1. Dans le projet **MediaCapture** , ajoutez une référence au `GrayscaleTransform` projet. Pour en savoir plus, [consultez Procédure: Ajouter ou supprimer des références à l’aide du gestionnaire de références](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).

1. Dans `Package.appxmanifest`, sous l’onglet **fonctionnalités** , sélectionnez **microphone** et **webcam**. Les deux capacités sont nécessaires pour capturer des photos à partir de la webcam.

1. Dans `MainPage.xaml`, ajoutez le code suivant à l’élément de [grille](/uwp/api/Windows.UI.Xaml.Controls.Grid) racine:

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. Utilisez le code suivant pour remplacer le contenu de `MainPage.xaml.cs`:

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

L’illustration suivante montre le `MediaCapture app`.

![Application MediaCapture capturant une photo](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>Étapes suivantes

L'exemple montre comment capturer des photos à partir de la webcam par défaut une à la fois. L' [exemple Media extensions](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) est plus. Il montre comment énumérer les dispositifs de webcam et utiliser les gestionnaires de schéma locaux, et illustre des effets multimédias supplémentaires applicables aux photos et aux flux de vidéo.

## <a name="see-also"></a>Voir aussi

[Bibliothèque de modèles Windows Runtime C++ (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)<br/>
[Media extensions, exemple](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)
