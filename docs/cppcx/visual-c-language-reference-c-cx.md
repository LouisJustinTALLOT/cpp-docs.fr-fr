---
title: Référence du langage Visual C++ (C + c++ / CX) | Documents Microsoft
ms.custom: ''
ms.date: 09/15/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b251a89eee456905fae1e2096a74362fc6c44ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090155"
---
# <a name="visual-c-language-reference-ccx"></a>Référence du langage Visual C++ (C++/CX)

C + c++ / CX est un ensemble d’extensions du langage C++ qui permet de créer des applications Windows et de composants Windows Runtime dans un idiome aussi proche que possible moderne C++. Utiliser c++ / CX pour écrire des applications Windows et des composants dans le code natif qui interagissent facilement avec Visual c#, Visual Basic et JavaScript et d’autres langages qui prennent en charge le Windows Runtime. Dans ces cas rares qui nécessitent un accès direct aux interfaces COM brutes ou au code non exceptionnel, vous pouvez utiliser la [bibliothèque de modèles Windows Runtime C++ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

> [!NOTE]
> C + c++ / WinRT est une nouveau, standard C ++ 17 projection du langage for Windows Runtime APIs. Il est disponible dans le SDK Windows 10 plus récentes à partir de la version 1803 qui interviennent. C + c++ / WinRT est entièrement implémentée dans les fichiers d’en-tête et conçu pour vous fournir un accès de première classe de l’API Windows modernes.

> Avec C + c++ / WinRT, vous pouvez consommer et créer APIs Windows Runtime à l’aide de n’importe quel conforme aux normes compilateur C ++ 17. C + c++ / WinRT généralement plus performant et génère des fichiers binaires du plus petits que toute autre option de langue pour le Windows Runtime. Nous continuerons à prendre en charge C + c++ / CX et WRL, mais le recommandons vivement que les nouvelles applications utiliser C + c++ / WinRT. Pour plus d’informations, consultez [C + c++ / WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index).


À l’aide de C + c++ / CX, vous pouvez créer :

- Les applications C++ Universal Windows Platform (UWP) qui utilisent XAML pour définir l’utilisateur de l’interface et utilisent la pile native. Pour plus d’informations, consultez [créer une application « hello world » dans C++ (UWP)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

- Composants C++ Windows Runtime qui peuvent être utilisés par les applications Windows JavaScript. Pour plus d’informations, consultez [création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

- Des jeux et des applications à intensité graphique Windows DirectX. Pour plus d’informations, consultez [créer un jeu UWP simple avec DirectX](/windows/uwp/gaming/tutorial--create-your-first-metro-style-directx-game).

## <a name="related-articles"></a>Articles connexes

|||
|-|-|
|[Référence rapide](../cppcx/quick-reference-c-cx.md)|Tableau de mots clés et des opérateurs pour C + c++ / CX.|
|[Système de type](../cppcx/type-system-c-cx.md)|Décrit la base C + c++ / CX types et les constructions de programmation et comment utiliser C + c++ / CX pour consommer et créer des types Windows Runtime.|
|[Génération d’applications et de bibliothèques](../cppcx/building-apps-and-libraries-c-cx.md)|Explique comment utiliser l'IDE pour générer des applications et les lier aux bibliothèques et DLL statiques.|
|[Interopérabilité avec d’autres langages](../cppcx/interoperating-with-other-languages-c-cx.md)|Explique comment les composants qui sont écrits à l’aide de C + c++ / CX peut être utilisé avec les composants qui sont écrites en JavaScript, un langage managé ou la [!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)].|
|[Thread et Marshaling](../cppcx/threading-and-marshaling-c-cx.md)|Explique comment spécifier le comportement de threads et de marshaling des composants que vous créez.|
|[Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md)|Documentation de référence sur l’espace de noms par défaut, l’espace de noms de plateforme, Platform::Collections et les espaces de noms associés.|
|[Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|Répertorie les fonctions CRT qui ne peuvent pas être utilisées dans les applications Windows Runtime.|
|[Guides de procédures pour les applications Windows 10](http://msdn.microsoft.com/library/windows/apps/xaml/mt244352.aspx)|Fournit des instructions détaillées sur les applications Windows 10, ainsi que des liens vers d’autres informations.|
|[C + c++ / CX partie 0 sur \[n\]: Introduction](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction/)<br /><br />[C + c++ / CX partie 1 sur \[n\]: une classe Simple](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class/)<br /><br />[C + c++ / CX partie 2 sur \[n\]: Types avec chapeaux](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C + c++ / CX partie 3 sur \[n\]: en cours d’élaboration](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)<br /><br />[C + c++ / CX partie 4 sur \[n\]: les fonctions membres Static](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions/)|Une série blog Visual C++ sur C + c++ / CX.|
