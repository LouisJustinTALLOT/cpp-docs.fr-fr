---
title: Applications de plateforme Windows universelle (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.topic: overview
ms.openlocfilehash: 25b89d2d9cb99e05145e60f9c9b1a6324fbbeb39
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404598"
---
# <a name="universal-windows-apps-c"></a>Applications de plateforme Windows universelle (C++)

La plateforme Windows universelle (UWP) est l’interface de programmation moderne pour Windows. Avec UWP, vous écrivez une application ou un composant une fois et vous la déployez sur n’importe quel appareil Windows 10. Vous pouvez écrire un composant en C++ et les applications écrites dans tout autre langage compatible UWP peuvent l’utiliser.

La plus grande partie de la documentation UWP se trouve dans l’arborescence de contenu Windows dans [plateforme Windows universelle documentation](/windows/uwp/). Vous y trouverez des didacticiels de démarrage, ainsi que de la documentation de référence.

Pour les nouveaux composants et applications UWP, nous vous recommandons d’utiliser [c++/WinRT](/windows/uwp/cpp-and-winrt-apis/), une nouvelle projection de langage c++ 17 standard pour les API Windows Runtime. C++/WinRT est disponible dans le kit de développement logiciel (SDK) Windows 10 à partir de la version 1803. C++/WinRT est implémenté entièrement dans les fichiers d’en-tête et est conçu pour vous fournir un accès de première classe à l’API Windows moderne. Contrairement à l’implémentation C++/CX, C++/WinRT n’utilise pas de syntaxe non standard ou d’extensions de langage Microsoft, et il tire pleinement parti du compilateur C++ pour créer une sortie hautement optimisée. Pour plus d’informations, consultez [Introduction à C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

Vous pouvez utiliser le convertisseur d’application Desktop Bridge pour empaqueter votre application de bureau existante en vue d’un déploiement via le Microsoft Store. Pour plus d’informations, consultez [utilisation du Runtime Visual C++ dans Centennial Project](https://devblogs.microsoft.com/cppblog/using-visual-c-runtime-in-centennial-project/) et [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-ccx"></a>Applications UWP utilisant C++/CX

|||
|-|-|
|[Informations de référence sur le langage C++/CX](visual-c-language-reference-c-cx.md)|Décrit l’ensemble des extensions qui simplifient la consommation C++ des API Windows Runtime et activent la gestion des erreurs basée sur les exceptions.|
|[Génération d’applications et de bibliothèques (C++/CX)](building-apps-and-libraries-c-cx.md)|Décrit comment créer des DLL et des bibliothèques statiques qui sont accessibles à partir d’une application ou d’un composant C++/CX.|
|[Didacticiel : créer une application UWP « Hello, World » en C++/CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Une procédure pas à pas qui présente les concepts de base du développement d’applications UWP en C++/CX. |
|[Création de composants Windows Runtime en C++/CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Décrit comment créer des dll que d’autres applications et composants UWP peuvent consommer.|
|[Programmation de jeux UWP](/windows/uwp/gaming/)|Décrit comment utiliser DirectX et C++/CX pour créer des jeux.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Applications UWP qui utilisent la bibliothèque de modèles C++ Windows Runtime (WRL)

La bibliothèque de modèles C++ Windows Runtime fournit les interfaces COM de bas niveau par lesquelles le code C++ ISO peut accéder aux Windows Runtime dans un environnement sans exception. Dans la plupart des cas, nous vous recommandons d’utiliser C++/WinRT ou C++/CX au lieu de la bibliothèque de modèles C++ Windows Runtime pour le développement d’applications UWP. Pour plus d’informations sur la bibliothèque de modèles C++ Windows Runtime, consultez [Windows Runtime C++ Template Library (WRL)](wrl/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Voir aussi

[C++ dans Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Vue d’ensemble de la programmation Windows en C++](../windows/overview-of-windows-programming-in-cpp.md)<br/>
