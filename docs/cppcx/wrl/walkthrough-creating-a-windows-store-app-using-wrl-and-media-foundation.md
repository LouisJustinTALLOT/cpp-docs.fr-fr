---
title: 'Procédure pas à pas : création d’une application UWP à l’aide de WRL et Media Foundation'
ms.date: 04/23/2019
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: 272092982c5e9cc57f52043e08c8bd384c43ea96
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031509"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>Procédure pas à pas : création d’une application UWP à l’aide de WRL et Media Foundation

> [!NOTE]
> Pour les nouvelles applications et composants UWP, nous vous recommandons [d’utiliser la CMD/WinRT](/windows/uwp/cpp-and-winrt-apis/), une nouvelle projection en langue standard de C-17 pour les API Windows Runtime. CMD/WinRT est disponible dans windows 10 SDK à partir de la version 1803. Le CMD/WinRT est entièrement implémenté dans des fichiers d’en-tête et est conçu pour vous fournir un accès de première classe à l’API Windows moderne.

Dans ce tutoriel, vous apprendrez comment utiliser la bibliothèque Windows Runtime CMd Template (WRL) pour créer une plate-forme universelle De Windows (UWP) application qui utilise [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk).

Cet exemple crée une transformation Media Fondation personnalisée qui applique un effet de nuances de gris aux images capturées par une webcam. L'application utilise C++ pour définir la transformation personnalisée et C# pour utiliser le composant afin de transformer les images capturées.

> [!NOTE]
> Au lieu de C#, vous pouvez également utiliser JavaScript, Visual Basic, ou C++ pour recourir au composant de transformation personnalisée.

Dans la plupart des cas, vous pouvez utiliser CMD/CX pour créer Windows Runtime. Cependant, parfois vous devez utiliser le WRL. Par exemple, lorsque vous créez une extension multimédia pour Microsoft Media Foundation, vous devez créer un composant qui implémente à la fois les interfaces COM et Windows Runtime. Étant donné que le CMD/CX ne peut créer que des objets Windows Runtime, pour créer une extension multimédia, vous devez utiliser le WRL car il permet la mise en œuvre des interfaces COM et Windows Runtime.

> [!NOTE]
> Bien que cet exemple de code soit long, il montre le minimum nécessaire pour créer une transformation Media Foundation utile. Vous pouvez l'utiliser comme point de départ pour votre propre transformation personnalisée. Cet exemple est adapté de [l’échantillon d’extensions de médias](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096), qui utilise des extensions multimédias pour appliquer des effets à la vidéo, décoder la vidéo et créer des gestionnaires de schémas qui produisent des flux multimédias.

## <a name="prerequisites"></a>Prérequis

- Dans Visual Studio 2017 et plus tard, le support UWP est un composant optionnel. Pour l’installer, ouvrez l’installateur Visual Studio à partir du menu Windows Start et trouvez votre version de Visual Studio. Choisissez **Modifier** et assurez-vous que la vignette **de développement de la plate-forme Windows universelle** est vérifiée. Sous **les composants facultatifs,** vérifiez **les outils CMD pour UWP (v141)** pour Visual Studio 2017, ou **outils CMD pour UWP (v142)** pour Visual Studio 2019. Ensuite, vérifiez la version du SDK Windows que vous souhaitez utiliser.

- Expérience avec le [Windows Runtime](/uwp/api/).

- Expérience avec COM.

- Une webcam.

## <a name="key-points"></a>Points clés

- Pour créer un composant Media Foundation personnalisé, utilisez un fichier de définition MIDL (Microsoft Interface Definition Language) pour définir une interface, implémentez celle-ci, puis rendez-la activable à partir d'autres composants.

- La `namespace` `runtimeclass` valeur et les `NTDDI_WIN8`attributs de la version, ainsi que la valeur d’attribut de [la version,](/windows/win32/Midl/version) sont des éléments importants de la définition MIDL pour un composant de la Fondation des médias qui utilise WRL.

- [Microsoft:WRL::RuntimeClass](runtimeclass-class.md) est la classe de base pour le composant personnalisé Media Foundation. Le [Microsoft::WRL::RuntimeClassType::WinRtClassicComMix](runtimeclasstype-enumeration.md) enum value, qui est fourni comme un argument modèle, marque la classe pour une utilisation à la fois comme une classe Windows Runtime et comme une classe classique DE temps d’exécution COM.

- La macro [InspectableClass](inspectableclass-macro.md) implémente les fonctionnalités `QueryInterface` COM de base telles que le comptage des références et la méthode, et définit le nom de classe d’exécution et le niveau de confiance.

- Utilisez le Microsoft::WRL::[Module classe](module-class.md) pour implémenter DLL fonctions d’entrée-point tels que [DllGetActivationFactory](/windows/win32/winrt/functions), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow), et [DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject).

- Liez votre DLL de composant à runtimeobject.lib. Spécifiez également [/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md) sur la ligne de liaison pour générer des métadonnées Windows.

- Utilisez les références de projet pour rendre les composants WRL accessibles aux applications UWP.

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>Utiliser le WRL pour créer le composant de transformation à échelle grise de la Fondation des médias

1. Dans Visual Studio, créez un projet **Blank Solution.** Nommez le projet, par exemple, *MediaCapture*.

1. Ajoutez un projet **DLL (Universal Windows)** à la solution. Nommez le projet, par exemple *GrayscaleTransform*.

1. Ajoutez un fichier **Midl File (.idl)** au projet. Nommez le fichier, par exemple, *GrayscaleTransform.idl*.

1. Ajoutez ce code à GrayscaleTransform.idl :

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. Utilisez le code suivant pour `pch.h`remplacer le contenu de :

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. Ajoutez un nouveau fichier d’en-tête au projet, nommez-le, `BufferLock.h`puis remplacez le contenu par ce code :

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h`n’est pas utilisé dans cet exemple. Vous pouvez le supprimer du projet si vous le souhaitez.

1. Utilisez le code suivant pour `GrayscaleTransform.cpp`remplacer le contenu de :

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. Ajoutez un nouveau fichier de définition du `GrayscaleTransform.def`module au projet, nommez-le, puis ajoutez ce code :

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. Utilisez le code suivant pour `dllmain.cpp`remplacer le contenu de :

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. Dans la boîte de dialogue **property Pages** du projet, définissez les propriétés **Linker** suivantes.

   1. Sous **entrée**, pour le `GrayScaleTransform.def`fichier de définition du **module**, spécifier .

   1. Aussi **Input**sous Entrée `runtimeobject.lib` `mfuuid.lib`, `mfplat.lib` ajouter , , et à la propriété **de dépendances supplémentaires.**

   1. Sous **Windows Metadata**, définir **Générer des métadonnées Windows** à Oui **(/WINMD)**.

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>Pour utiliser le WRL, le composant personnalisé media Foundation à partir d’une application C

1. Ajoutez un nouveau projet **d’application CMd Blank (Universal Windows)** à la `MediaCapture` solution. Nommez le projet, par exemple, *MediaCapture*.

1. Dans le projet **MediaCapture,** ajoutez `GrayscaleTransform` une référence au projet. Pour savoir comment, voir [comment : Ajouter ou supprimer les références en utilisant le gestionnaire de référence](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).

1. Dans `Package.appxmanifest`, sur l’onglet **Capacités,** sélectionnez **Microphone** et **Webcam**. Les deux capacités sont nécessaires pour capturer des photos à partir de la webcam.

1. Dans `MainPage.xaml`, ajouter ce code à l’élément [de grille](/uwp/api/windows.ui.xaml.controls.grid) racine:

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. Utilisez le code suivant pour `MainPage.xaml.cs`remplacer le contenu de :

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

L’illustration suivante `MediaCapture app`montre le .

![Application MediaCapture capturant une photo](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>Étapes suivantes

L'exemple montre comment capturer des photos à partir de la webcam par défaut une à la fois. [L’échantillon d’extensions de médias](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) fait plus. Il montre comment énumérer les dispositifs de webcam et utiliser les gestionnaires de schéma locaux, et illustre des effets multimédias supplémentaires applicables aux photos et aux flux de vidéo.

## <a name="see-also"></a>Voir aussi

[Bibliothèque de modèles Windows Runtime C++ (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Fondation Microsoft Media](/windows/win32/medfound/microsoft-media-foundation-sdk)<br/>
[Échantillon d’extensions de médias](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)
