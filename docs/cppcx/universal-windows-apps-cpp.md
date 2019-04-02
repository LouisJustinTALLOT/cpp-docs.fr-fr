---
title: Applications de plateforme Windows universelle (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.openlocfilehash: fbd5366ee52dfe32baef9458a82c16914666699e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784269"
---
# <a name="universal-windows-apps-c"></a>Applications de plateforme Windows universelle (C++)

La plateforme universelle Windows (UWP) est l’interface de programmation moderne pour Windows. Avec UWP vous écrivez une application ou composant fois et déployez sur n’importe quel appareil Windows 10. Vous pouvez écrire un composant en C++ et les applications écrites dans n’importe quel autre langage compatible avec UWP peuvent l’utiliser.

La plupart de la documentation UWP est dans l’arborescence de contenu de Windows sur [documentation de la plateforme Windows universelle](/windows/uwp/). Vous y trouverez des didacticiels de début également comme documentation de référence. 

Pour les nouvelles applications UWP et des composants, nous vous recommandons d’utiliser [C++ / c++ / WinRT](/windows/uwp/cpp-and-winrt-apis/), une nouveau standard C ++ 17 projection de langage pour Windows Runtime APIs. C++ / c++ / WinRT est disponible dans le SDK Windows 10 à partir de la version 1803 qui interviennent. C++ / c++ / WinRT est entièrement implémentée dans les fichiers d’en-tête et est conçu pour vous permettre d’accès idéal à l’API Windows moderne. Contrairement à C++ / c++ / implémentation de CX. C++ / c++ / WinRT n’utilise pas une syntaxe non standard ou des extensions de langage de Microsoft, et il tire pleinement parti du compilateur C++ pour créer une sortie hautement optimisée. Pour plus d’informations, consultez [présentation de C++ / c++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

Vous pouvez utiliser le convertisseur d’application de pont du bureau pour empaqueter votre application de bureau existante pour le déploiement via le Microsoft Store. Pour plus d’informations, consultez [à l’aide de Visual C++ Runtime dans Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) et [pont du bureau](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-ccx"></a>Les applications UWP qui utilisent C++ / c++ / CX

|||
|-|-|
|[Informations de référence du langage Visual C++ (C++/CX)](visual-c-language-reference-c-cx.md)|Décrit l’ensemble des extensions qui simplifient la consommation C++ Windows Runtime APIs et activer la gestion des erreurs qui sont basée sur les exceptions.|
|[Génération d’applications et de bibliothèques (C++/CX)](building-apps-and-libraries-c-cx.md)|Décrit comment créer des DLL et des bibliothèques statiques qui sont accessibles à partir d’une application ou d’un composant C++/CX.|
|[Tutoriel : Créer une UWP application « Hello, World » en C / c++ / CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Une procédure pas à pas qui présente les concepts de base du développement d’applications UWP en C++ / c++ / CX. |
|[Création de composants Windows Runtime en C / c++ / CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Décrit comment créer des DLL autres composants et les applications UWP peuvent consommer.|
|[Programmation de jeux UWP](/windows/uwp/gaming/)|Décrit comment utiliser DirectX et C++ / c++ / CX pour créer des jeux.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Applications UWP qui utilisent la bibliothèque de modèle C++ Windows Runtime (WRL)

La bibliothèque de modèles Windows Runtime C++ fournit les interfaces COM de bas niveau par lequel code C++ ISO peut accéder à l’exécution de Windows dans un environnement sans exception. Dans la plupart des cas, nous vous recommandons d’utiliser C++ / c++ / WinRT ou C / c++ / CX au lieu de la bibliothèque de modèles Windows Runtime C++ pour le développement d’applications UWP. Pour plus d’informations sur la bibliothèque de modèles Windows Runtime C++, consultez [bibliothèque de modèles Windows Runtime C++ (WRL)](wrl/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Voir aussi

[C++ dans Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Vue d’ensemble de la programmation Windows en C++](../windows/overview-of-windows-programming-in-cpp.md)<br/>