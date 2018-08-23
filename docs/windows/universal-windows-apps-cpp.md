---
title: Applications universelles Windows (C++) | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7ba556ee3803bb00f07032e0589209af2d32addf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591751"
---
# <a name="universal-windows-apps-c"></a>Applications de plateforme Windows universelle (C++)

Les applications universelles Windows Platform (UWP) représentent un ensemble de principes de conception qui utilisent des interfaces utilisateur simples centrées autour du contenu s’ajuste automatiquement aux différentes tailles d’écran sur différents appareils. Vous créez l'interface utilisateur dans le balisage XAML et le code-behind en C++ natif. Vous pouvez également créer des composants (DLL) qui peuvent être utilisés par des applications de plateforme Windows universelle qui sont écrites dans d'autres langages. La surface d’API pour les applications UWP est l’exécution de Windows, qui est une bibliothèque bien factorisée qui fournit un large éventail de services de système d’exploitation.

> [!TIP]
> Pour Windows 10, vous pouvez utiliser le convertisseur d’application de pont du bureau pour empaqueter votre application de bureau existante pour le déploiement via le Microsoft Store. Pour plus d’informations, consultez [à l’aide de Visual C++ Runtime dans Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) et [pont du bureau](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-cwinrt"></a>Les applications UWP qui utilisent C++ / c++ / WinRT

C++ / c++ / WinRT est une nouveau et à en-tête uniquement en fonction de bibliothèque projection de langage C++ pour le Runtime de Windows qui utilise C++ complètement standard, contrairement à la C + c++ / implémentation de CX. C++ / c++ / WinRT n’utilise pas une syntaxe non standard ou des extensions de langage de Microsoft, et il tire pleinement parti du compilateur C++ pour créer une sortie hautement optimisée. Pour plus d’informations, consultez [C++ / c++ / WinRT](/windows/uwp/cpp-and-winrt-apis). Pour une présentation de C++ / c++ / WinRT et un démarrage rapide de code, consultez [présentation de C++ / c++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

## <a name="uwp-apps-that-use-ccx"></a>Les applications UWP qui utilisent C++ / c++ / CX

|||
|-|-|
|[Informations de référence du langage Visual C++ (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)|Décrit l’ensemble des extensions qui simplifient la consommation C++ Windows Runtime APIs et activer la gestion des erreurs qui sont basée sur les exceptions.|
|[Génération d’applications et de bibliothèques (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|Décrit comment créer des DLL et des bibliothèques statiques qui sont accessibles à partir d’une application ou d’un composant C++/CX.|
|[Didacticiel : Créer une UWP application « Hello, World » en C / c++ / CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Une procédure pas à pas qui présente les concepts de base du développement d’applications UWP en C++ / c++ / CX. |
|[Création de composants Windows Runtime en C / c++ / CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Décrit comment créer des DLL autres composants et les applications UWP peuvent consommer.|
|[Programmation de jeux UWP](/windows/uwp/gaming/)|Décrit comment utiliser DirectX et C++ / c++ / CX pour créer des jeux.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Applications UWP qui utilisent la bibliothèque de modèle C++ Windows Runtime (WRL)

La bibliothèque de modèles Windows Runtime C++ fournit les interfaces COM de bas niveau par lequel code C++ ISO peut accéder à l’exécution de Windows dans un environnement sans exception. Dans la plupart des cas, nous vous recommandons d’utiliser C++ / c++ / WinRT ou C / c++ / CX au lieu de la bibliothèque de modèles Windows Runtime C++ pour le développement d’applications UWP. Pour plus d’informations sur la bibliothèque de modèles Windows Runtime C++, consultez [bibliothèque de modèles Windows Runtime C++ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Voir aussi

[Visual C++](../visual-cpp-in-visual-studio.md)<br/>