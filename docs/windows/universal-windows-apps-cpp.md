---
title: Les applications Windows universelles (C++) | Documents Microsoft
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
ms.openlocfilehash: 9914e9ac83efcc43ef120259254b65ef4f1e0ee9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891121"
---
# <a name="universal-windows-apps-c"></a>Applications de plateforme Windows universelle (C++)

Les applications universelles Windows Platform (UWP) sont basées sur un ensemble de principes de conception qui mettent l’accent sur les interfaces utilisateur simples centrées sur le contenu s’ajuste automatiquement pour différentes tailles d’écran sur différents appareils. Vous créez l'interface utilisateur dans le balisage XAML et le code-behind en C++ natif. Vous pouvez également créer des composants (DLL) qui peuvent être utilisés par des applications de plateforme Windows universelle qui sont écrites dans d'autres langages. La surface de l’API pour les applications UWP est le Windows Runtime, qui est une bibliothèque bien factorisée fournissant une grande variété de services de système d’exploitation.

> [!TIP]  
> Pour Windows 10, vous pouvez utiliser le convertisseur d’application de bureau pont pour empaqueter votre application de bureau existante pour le déploiement via Microsoft Store. Pour plus d’informations, consultez [à l’aide de Visual C++ Runtime dans le projet Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) et [bureau pont](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-cwinrt"></a>Les applications UWP utilisant c++ / WinRT

C + c++ / WinRT est une nouvelle, en-tête uniquement basée sur la bibliothèque C++ projection du langage pour le Windows Runtime qui utilise C++ complètement standard, contrairement à la C + c++ / mise en œuvre CX. C + c++ / WinRT n’utilise une syntaxe non standard ou des extensions Microsoft du langage, et il exploite pleinement du compilateur C++ pour créer une sortie de hautement optimisée. Pour plus d’informations, consultez [C + c++ / WinRT](/windows/uwp/cpp-and-winrt-apis). Pour obtenir une présentation C + c++ / WinRT et un démarrage rapide de code, consultez [Introduction au langage c++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

## <a name="uwp-apps-that-use-ccx"></a>Les applications UWP utilisant c++ / CX

|||
|-|-|
|[Informations de référence du langage Visual C++ (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)|Décrit l’ensemble des extensions qui simplifient la consommation par C++ des APIs Windows Runtime et activer la gestion des erreurs sont basée sur les exceptions.|
|[Génération d’applications et de bibliothèques (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|Décrit comment créer des DLL et des bibliothèques statiques qui sont accessibles à partir d’une application ou d’un composant C++/CX.|
|[Didacticiel : Créer une application UWP application « Hello, World » en langage c++ / CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Une procédure pas à pas qui présente les concepts de base du développement d’applications UWP dans C + c++ / CX. |
|[Création de composants Windows Runtime en C++ c++ / CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Décrit comment créer des DLL que d’autres composants et applications UWP peuvent consommer.|
|[Programmation de jeux UWP](/windows/uwp/gaming/)|Décrit comment utiliser DirectX et C + c++ / CX pour créer des jeux.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Applications UWP qui utilisent la bibliothèque Windows Runtime modèle C++ (WRL)

La bibliothèque de modèles Windows Runtime C++ fournit les interfaces COM de bas niveau qui code C++ ISO peut accéder au Windows Runtime dans un environnement sans exception. Dans la plupart des cas, nous vous recommandons d’utiliser C + c++ / WinRT ou C + c++ / CX au lieu de la bibliothèque de modèles Windows Runtime C++ pour le développement d’applications UWP. Pour plus d’informations sur la bibliothèque de modèles Windows Runtime C++, consultez [bibliothèque de modèles Windows Runtime C++ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Voir aussi

[Visual C++](../visual-cpp-in-visual-studio.md)<br/>
