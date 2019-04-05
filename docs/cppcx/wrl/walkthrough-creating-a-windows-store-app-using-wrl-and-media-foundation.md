---
title: 'Procédure pas à pas : Création d’une application UWP à l’aide de WRL et Media Foundation'
ms.date: 09/17/2018
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: e0254be8c6fa185f75c46898d4da51742195550a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036034"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>Procédure pas à pas : Création d’une application UWP à l’aide de WRL et Media Foundation

Découvrez comment utiliser la bibliothèque de modèles C++ (WRL) de Windows Runtime pour créer une application de plateforme universelle Windows (UWP) qui utilise [Microsoft Media Foundation](/windows/desktop/medfound/microsoft-media-foundation-sdk).

Cet exemple crée une transformation Media Fondation personnalisée qui applique un effet de nuances de gris aux images capturées par une webcam. L'application utilise C++ pour définir la transformation personnalisée et C# pour utiliser le composant afin de transformer les images capturées.

> [!NOTE]
> Au lieu de C#, vous pouvez également utiliser JavaScript, Visual Basic, ou C++ pour recourir au composant de transformation personnalisée.

Dans la plupart des cas, vous pouvez utiliser C++ / c++ / CX pour créer le Windows Runtime. Toutefois, vous devez parfois utiliser la bibliothèque WRL. Par exemple, lorsque vous créez une extension de support pour Microsoft Media Foundation, vous devez créer un composant qui implémente les interfaces COM et Windows Runtime. Étant donné que C++ / c++ / CX peut uniquement créer des objets Windows Runtime, pour créer une extension de support, vous devez utiliser la bibliothèque WRL, car il permet l’implémentation d’interfaces COM et Windows Runtime.

> [!NOTE]
> Bien que cet exemple de code soit long, il montre le minimum nécessaire pour créer une transformation Media Foundation utile. Vous pouvez l'utiliser comme point de départ pour votre propre transformation personnalisée. Cet exemple est une adaptation de la [exemple d’extensions de média](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096), les extensions de média utilise pour appliquer des effets à une vidéo, décoder une vidéo et créer des gestionnaires de schéma qui produisent des flux de données.

## <a name="prerequisites"></a>Prérequis

- Expérience avec le [Windows Runtime](https://msdn.microsoft.com/library/windows/apps/br211377.aspx).

- Expérience avec COM.

- Une webcam.

## <a name="key-points"></a>Points clés

- Pour créer un composant Media Foundation personnalisé, utilisez un fichier de définition MIDL (Microsoft Interface Definition Language) pour définir une interface, implémentez celle-ci, puis rendez-la activable à partir d'autres composants.

- Le `namespace` et `runtimeclass` attributs et le `NTDDI_WIN8` [version](/windows/desktop/Midl/version) valeur d’attribut sont des parties importantes de la définition MIDL pour un composant Media Foundation qui utilise la bibliothèque WRL.

- [Microsoft::wrl :: runtimeclass](runtimeclass-class.md) est la classe de base pour le composant Media Foundation personnalisé. Le [winrtclassiccommix](runtimeclasstype-enumeration.md) valeur enum, qui est fourni comme argument de modèle, marque la classe à utiliser comme une classe Windows Runtime et comme une classe d’exécution COM classique.

- Le [InspectableClass](inspectableclass-macro.md) macro implémente des fonctionnalités telles que le comptage de références COM de base et la `QueryInterface` (méthode) et définit l’exécution du nom de la classe et le niveau de confiance.

- Utiliser le Microsoft::WRL ::[classe de Module](module-class.md) pour implémenter des fonctions de point d’entrée DLL comme [DllGetActivationFactory](https://msdn.microsoft.com/library/br205771.aspx), [DllCanUnloadNow](/windows/desktop/api/combaseapi/nf-combaseapi-dllcanunloadnow), et [ DllGetClassObject](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject).

- Liez votre DLL de composant à runtimeobject.lib. Spécifiez également [/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md) sur la ligne de l’éditeur de liens pour générer des métadonnées de Windows.

- Utilisez les références de projet pour rendre les composants WRL accessible aux applications UWP.

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>Pour utiliser la bibliothèque WRL pour créer les nuances de gris de Media Foundation transformer le composant

1. Dans Visual Studio, créez un **nouvelle Solution** projet. Nommez le projet, par exemple, *MediaCapture*.

1. Ajouter un **DLL (Windows universel)** projet à la solution. Nommez le projet, par exemple, *GrayscaleTransform*.

1. Ajouter un **fichier Midl (.idl)** fichier au projet. Nommez le fichier, par exemple, *GrayscaleTransform.idl*.

1. Ajoutez ce code à GrayscaleTransform.idl :

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. Utilisez le code suivant pour remplacer le contenu de `pch.h`:

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. Ajoutez un nouveau fichier d’en-tête au projet, nommez-le `BufferLock.h`, puis remplacez le contenu par ce code :

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h` n’est pas utilisé dans cet exemple. Vous pouvez le supprimer du projet si vous le souhaitez.

1. Utilisez le code suivant pour remplacer le contenu de `GrayscaleTransform.cpp`:

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. Ajoutez un nouveau fichier de définition de module au projet, nommez-le `GrayscaleTransform.def`, puis ajoutez ce code :

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. Utilisez le code suivant pour remplacer le contenu de `dllmain.cpp`:

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. Dans le projet **Pages de propriétés** boîte de dialogue, définissez les éléments suivants **l’éditeur de liens** propriétés.

   1. Sous **entrée**, pour le **fichier de définition de Module**, spécifiez `GrayScaleTransform.def`.

   1. Également sous **entrée**, ajouter `runtimeobject.lib`, `mfuuid.lib`, et `mfplat.lib` à la **dépendances supplémentaires** propriété.

   1. Sous **Windows métadonnées**, affectez la valeur **générer des métadonnées Windows** à **Oui (/ WINMD)**.

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>Pour utiliser la bibliothèque WRL le composant Media Foundation personnalisé à partir d’une application c#

1. Ajouter un nouveau **c# application vide (Windows universel)** de projet pour le `MediaCapture` solution. Nommez le projet, par exemple, *MediaCapture*.

1. Dans le **MediaCapture** de projet, ajoutez une référence à la `GrayscaleTransform` projet. Pour savoir comment procéder, consultez [Comment : Ajouter ou supprimer des références à l’aide du gestionnaire de références](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).

1. Dans `Package.appxmanifest`, dans le **fonctionnalités** onglet, sélectionnez **Microphone** et **Webcam**. Les deux capacités sont nécessaires pour capturer des photos à partir de la webcam.

1. Dans `MainPage.xaml`, ajoutez ce code à la racine [grille](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx) élément :

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. Utilisez le code suivant pour remplacer le contenu de `MainPage.xaml.cs`:

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

L’illustration suivante montre le `MediaCapture app`.

![Application MediaCapture capturant une photo](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>Étapes suivantes

L'exemple montre comment capturer des photos à partir de la webcam par défaut une à la fois. Le [exemple d’extensions de média](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) ne se limite pas. Il montre comment énumérer les dispositifs de webcam et utiliser les gestionnaires de schéma locaux, et illustre des effets multimédias supplémentaires applicables aux photos et aux flux de vidéo.

## <a name="see-also"></a>Voir aussi

[Bibliothèque de modèles Windows Runtime C++ (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft Media Foundation](/windows/desktop/medfound/microsoft-media-foundation-sdk)<br/>
[Exemple d’extensions de média](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)