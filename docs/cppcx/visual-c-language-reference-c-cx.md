---
title: Informations de référence sur le langage C++/CX
ms.date: 09/15/2017
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
ms.openlocfilehash: f28270ace3965a3cf89e250a873af14e48390708
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507418"
---
# <a name="ccx-language-reference"></a>Informations de référence sur le langage C++/CX

C++/CX est un ensemble d’extensions du langage C++ qui permet de créer des applications Windows et des composants de Windows Runtime dans un idiome aussi proche que possible du C++ moderne. Utilisez C++/CX pour écrire des applications et des composants Windows en code natif qui interagissent facilement avec Visual C#, Visual Basic et JavaScript, ainsi que d’autres langages qui prennent en charge le Windows Runtime. Dans ces cas rares qui requièrent un accès direct aux interfaces COM brutes ou du code non exceptionnel, vous pouvez utiliser le [Windows Runtime C++ Template Library (WRL)](./wrl/windows-runtime-cpp-template-library-wrl.md).

> [!NOTE]
> **/WinRT est l’alternative recommandée à C++/CX. [ C++](/windows/uwp/cpp-and-winrt-apis/index)** Il s’agit d’une nouvelle projection standard du langage C++ 17 pour les API Windows Runtime, disponible dans le dernier Kit de développement logiciel (SDK) Windows 10 à partir de la version 1803. C++/WinRT est entièrement implémenté dans les fichiers d’en-tête et conçu pour vous fournir un accès de première classe à l’API Windows moderne.
>
> Avec C++/WinRT, vous pouvez utiliser et créer Windows Runtime API à l’aide de n’importe quel compilateur C++ 17 conforme aux normes. C++/WinRT fonctionne généralement mieux et produit des binaires plus petits que n’importe quelle autre option de langage pour le Windows Runtime. Nous continuerons de prendre en charge les langages C++/CX et WRL, mais recommandons vivement l’utilisation du langage C++/WinRT avec des nouvelles applications. Pour plus d’informations, consultez [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index).

En utilisant C++/CX, vous pouvez créer :

- Applications de plateforme Windows universelle C++ (UWP) qui utilisent XAML pour définir l’interface utilisateur et utiliser la pile native. Pour plus d’informations, consultez [créer une application « Hello World » en C++ (UWP)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

- Les composants C++ Windows Runtime qui peuvent être utilisés par les applications Windows JavaScript. Pour plus d’informations, consultez [Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

- Des jeux et des applications à intensité graphique Windows DirectX. Pour plus d’informations, consultez [créer un jeu UWP simple avec DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game).

## <a name="related-articles"></a>Articles connexes

| Lien | Description |
|--|--|
| [Aide-mémoire](../cppcx/quick-reference-c-cx.md) | Tableau des mots clés et des opérateurs pour C++/CX. |
| [Système de types](../cppcx/type-system-c-cx.md) | Décrit les types de/CX et les constructions de programmation C++ de base, et comment utiliser C++/CX pour utiliser et créer des types de Windows Runtime. |
| [Création d’applications et de bibliothèques](../cppcx/building-apps-and-libraries-c-cx.md) | Explique comment utiliser l’IDE pour générer des applications et créer des liens vers des bibliothèques statiques et des dll. |
| [Interopérabilité avec d’autres langages](../cppcx/interoperating-with-other-languages-c-cx.md) | Explique comment les composants écrits à l’aide de C++/CX peuvent être utilisés avec des composants écrits en JavaScript, tout langage managé ou la bibliothèque de modèles C++ Windows Runtime. |
| [Thread et marshaling](../cppcx/threading-and-marshaling-c-cx.md) | Explique comment spécifier le comportement de threads et de marshaling des composants que vous créez. |
| [Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md) | Documentation de référence sur l’espace de noms par défaut, l’espace de noms de plateforme, Platform::Collections et les espaces de noms associés. |
| [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) | Répertorie les fonctions CRT qui ne peuvent pas être utilisées dans les applications Windows Runtime. |
| [Bien démarrer avec les applications Windows 10](/windows/uwp/get-started/) | Fournit des instructions détaillées sur les applications Windows 10, ainsi que des liens vers d’autres informations. |
| [C++/CX partie 0 sur \[ n \] : présentation](https://devblogs.microsoft.com/cppblog/ccx-part-0-of-n-an-introduction/)<br /><br />[C++/CX partie 1 de \[ n \] : classe simple](https://devblogs.microsoft.com/cppblog/ccx-part-1-of-n-a-simple-class/)<br /><br />[C++/CX partie 2 sur \[ n \] : types qui ont des chapeaux](https://devblogs.microsoft.com/cppblog/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C++/CX partie 3 sur \[ n \] : en cours de construction](https://devblogs.microsoft.com/cppblog/ccx-part-3-of-n-under-construction/)<br /><br />[C++/CX, partie 4 sur \[ n \] : fonctions membres statiques](https://devblogs.microsoft.com/cppblog/ccx-part-4-of-n-static-member-functions/)| Série de blogs de présentation sur C++/CX. |
