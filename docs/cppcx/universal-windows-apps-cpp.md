---
title: Applications de plateforme Windows universelle (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.topic: landing-page
ms.openlocfilehash: 68952e93e4f91ac3653a9991802ad42854d9d25a
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741028"
---
# <a name="universal-windows-apps-c"></a>Applications de plateforme Windows universelle (C++)

La plateforme Windows universelle (UWP) est l’interface de programmation moderne pour Windows. Avec UWP, vous écrivez une application ou un composant une fois et vous la déployez sur n’importe quel appareil Windows 10. Vous pouvez écrire un composant dans C++ et les applications écrites dans n’importe quel autre langage compatible UWP peuvent l’utiliser.

La plus grande partie de la documentation UWP se trouve dans l’arborescence de contenu Windows dans [plateforme Windows universelle documentation](/windows/uwp/). Vous y trouverez des didacticiels de démarrage, ainsi que de la documentation de référence. 

Pour les nouveaux composants et applications UWP, nous vous recommandons d’utiliser [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), une nouvelle projection de langage c++ 17 standard pour les API Windows Runtime. C++/WinRT est disponible dans le kit de développement logiciel (SDK) Windows 10 à partir de la version 1803. C++/WinRT est entièrement implémenté dans les fichiers d’en-tête et est conçu pour vous fournir un accès de première classe à l’API Windows moderne. Contrairement à C++l’implémentation de/CX. C++/WinRT n’utilise pas de syntaxe non standard ou d’extensions de langage Microsoft, et il tire pleinement C++ parti du compilateur pour créer une sortie hautement optimisée. Pour plus d’informations, consultez [présentation C++de/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

Vous pouvez utiliser le convertisseur d’application Desktop Bridge pour empaqueter votre application de bureau existante en vue d’un déploiement via le Microsoft Store. Pour plus d’informations, consultez [utilisation C++ de Visual Runtime dans Centennial Project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) et [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-ccx"></a>Applications UWP utilisant C++/CX

|||
|-|-|
|[C++Référence du langage/CX](visual-c-language-reference-c-cx.md)|Décrit l’ensemble des extensions qui simplifient C++ la consommation des API Windows Runtime et activent la gestion des erreurs basée sur les exceptions.|
|[Génération d’applications et de bibliothèques (C++/CX)](building-apps-and-libraries-c-cx.md)|Décrit comment créer des DLL et des bibliothèques statiques qui sont accessibles à partir d’une application ou d’un composant C++/CX.|
|[Tutoriel : Créer une application UWP « Hello, World » dans C++/CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Une procédure pas à pas qui présente les concepts de base du C++développement d’applications UWP dans/CX. |
|[Création de composants Windows Runtime C++dans/CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Décrit comment créer des dll que d’autres applications et composants UWP peuvent consommer.|
|[Programmation de jeux UWP](/windows/uwp/gaming/)|Décrit comment utiliser DirectX et/CX C++pour créer des jeux.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Applications UWP qui utilisent la bibliothèque C++ de modèles Windows Runtime (WRL)

La bibliothèque C++ de modèles Windows Runtime fournit les interfaces COM de bas niveau par lesquelles C++ le code ISO peut accéder aux Windows Runtime dans un environnement sans exception. Dans la plupart des cas, nous vous recommandons C++d’utiliser C++/WinRT ou/CX au lieu C++ de la bibliothèque de modèles Windows Runtime pour le développement d’applications UWP. Pour plus d’informations sur C++ la bibliothèque de modèles Windows Runtime, consultez [bibliothèque de modèles Windows Runtime C++ (WRL)](wrl/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Voir aussi

[C++ dans Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Vue d’ensemble de la programmation Windows en C++](../windows/overview-of-windows-programming-in-cpp.md)<br/>