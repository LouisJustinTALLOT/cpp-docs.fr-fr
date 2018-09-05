---
title: Applications de bureau (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d4f44e3587e9b274bbe89e2fa4f91accadb08ab
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688257"
---
# <a name="desktop-applications-visual-c"></a>Applications de bureau (Visual C++)

Un *application de bureau* en C++ est une application native qui peut accéder à l’ensemble des API de Windows et s’exécute dans une fenêtre ou dans la console système. Applications de bureau en C++ peuvent exécuter sur XP de Windows via Windows 10 (bien que Windows XP n’est ne sont plus officiellement pris en charge et il existe de nombreuses API Windows qui ont été introduites depuis).

Une application de bureau est distincte à partir d’une application de plateforme universelle Windows (UWP), ce qui peut s’exécuter sur les PC exécutant Windows 10, ainsi que sur la XBox, Windows Phone, Surface Hub et autres appareils. Pour plus d’informations sur les postes de travail Visual Studio. Les applications UWP, consultez [choisir votre technologie](https://msdn.microsoft.com/library/windows/desktop/dn614993\(v=vs.85\).aspx).


### <a name="desktop-bridge"></a>Pont du bureau

Dans Windows 10, vous pouvez empaqueter votre application de bureau existante ou d’un objet COM en tant qu’une application UWP et ajouter des fonctionnalités telles que touch UWP ou appeler des API à partir de l’ensemble d’API de Windows moderne. Vous pouvez également ajouter une application UWP à une solution de postes de travail dans Visual Studio et utilisez-les dans un seul package et que vous utilisent les API de Windows pour communiquer entre eux de package.

Dans Visual Studio 2017 version 15.4 ou ultérieure, vous pouvez créer un projet de Package d’Application Windows pour simplifier considérablement le travail d’empaquetage de votre application de bureau existante. Quelques restrictions s’appliquent en ce qui concerne le Registre appelle ou utilise des API de votre application de bureau, mais dans de nombreux cas, vous pouvez créer des chemins de code de remplacement pour obtenir une fonctionnalité similaire lors de l’exécution dans un package d’application. Pour plus d’informations, consultez [Desktop Bridge](/windows-uwp/porting/desktop-to-uwp-root).

### <a name="terminology"></a>Terminologie

- Un *Win32* application est une application de bureau C++ qui peuvent rendre utiliser native de Windows [API C de Windows et/ou APIs COM](https://msdn.microsoft.com/library/windows/desktop/ff818516\(v=vs.85\).aspx) CRT et API de bibliothèque Standard et des bibliothèques tierces 3e. Une application Win32 qui s’exécute dans une fenêtre exige que le développeur à utiliser explicitement des messages de Windows à l’intérieur d’une fonction de procédure de Windows. Malgré son nom, une application Win32 peut être compilée comme un (x86) 32 bits ou 64 bits (x64) binaire. Dans l’IDE de Visual Studio, les conditions x86 Win32 sont synonymes.

- Le [composant COM (Object Model)](/windows/desktop/com/the-component-object-model) est une spécification qui permet aux programmes écrits dans différents langages pour communiquer entre eux. Windows de nombreux composants sont implémentés en tant qu’objets COM et suivez les règles COM standard pour la création des objets interface destruction de découverte et d’objet.  À l’aide des objets COM à partir d’applications de bureau C++ est relativement simple, écrivez votre propre objet COM est toutefois plus avancée. Le [bibliothèque ATL (Active Template)](../atl/atl-com-desktop-components.md) fournit des macros et fonctions d’assistance qui simplifient le développement de COM.

- Une application MFC est une application de bureau Windows qui utilisent la [Microsoft Foundation Classes](../mfc/mfc-desktop-applications.md) pour créer l’interface utilisateur. Une application MFC permettre également utiliser des composants COM, ainsi que les CRT et les API de bibliothèque Standard. MFC fournit un simple wrapper orienté objet C++ au fil de la boucle de messages de fenêtre et les API de Windows. MFC est le choix par défaut pour les applications, en particulier les applications de type de l’entreprise, qui ont un grand nombre de contrôles d’interface utilisateur ou des contrôles utilisateur personnalisés. MFC fournit des classes d’assistance pratiques pour la gestion des fenêtres, la sérialisation, manipulation de texte, l’impression et les éléments d’interface utilisateur modernes tels que le ruban. Pour être efficace avec MFC, vous devez connaître avec Win32.

- C++ / c++ / CLI application ou un composant utilise les extensions à la syntaxe C++ (comme autorisé par la spécification C++) pour permettre l’interaction entre .NET et le code C++ natif.  C++ / c++ / application de l’interface CLI peut avoir des composants qui s’exécutent en mode natif et les composants qui s’exécutent sur le .NET Framework avec un accès à la bibliothèque de classes de Base .NET. C++ / c++ / CLI est l’option recommandée lorsque vous avez le code C++ natif qui doit fonctionner avec le code écrit en c# ou Visual Basic. Il s’adresse principalement pour une utilisation dans des DLL .NET plutôt que dans le code d’interface utilisateur. Pour plus d’informations, consultez [programmation .NET avec C++ / c++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Toute application de bureau en C++ peut utiliser C Runtime (CRT) et la bibliothèque Standard classes et fonctions, des objets COM et les fonctions Windows publiques, appelées collectivement comme l’API Windows. Pour obtenir une introduction aux applications de bureau Windows en C++, consultez [Apprendre à programmer pour Windows en C++](http://go.microsoft.com/fwlink/p/?LinkId=262281).

## <a name="in-this-section"></a>Dans cette section

|Titre|Description|
|-----------|-----------------|
|[Applications console](../windows/console-applications-in-visual-cpp.md)|Contient des informations sur les applications console. Une application console Win32 (ou Win64) n’a aucune fenêtre et aucune boucle de message. Elle s'exécute dans la fenêtre de console et l'entrée et la sortie sont gérées via la ligne de commande.|
|[Applications de bureau Windows](../windows/windows-desktop-applications-cpp.md)|Comment créer des applications de bureau qui s’exécutent dans windows, par opposition à la console.|
|[Ressources pour la création d’un jeu à l’aide de DirectX (C++)](../windows/resources-for-creating-a-game-using-directx.md)|Liens vers du contenu pour la création de jeux en C++.|
|[Procédure pas à pas : Création et utilisation d’une bibliothèque statique](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Comment créer un fichier binaire .lib.|
|[Procédure : utilisation du kit SDK Windows 10 dans une application de bureau Windows](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Contient les étapes pour configurer votre projet à générer avec le Kit de développement logiciel (SDK) Windows 10.|

## <a name="related-articles"></a>Articles connexes

|Titre|Description|
|-----------|-----------------|
|[Développement Windows](http://go.microsoft.com/fwlink/p/?LinkId=262282)|Contient des informations sur l'API Windows et COM. (Certaines API Windows et DLL tierces sont implémentées comme objets COM.)|
|[Hilo : développement d’applications C++ pour Windows 7](http://go.microsoft.com/fwlink/p/?LinkId=262284)|Explique comment créer une application de bureau Windows cliente enrichie, qui utilise l’animation Windows et Direct2D pour créer une interface utilisateur de type carrousel.  Ce didacticiel n’a pas été mis à jour depuis Windows 7, mais fournit malgré tout une présentation détaillée de la programmation Win32.|
|[Visual C++](../visual-cpp-in-visual-studio.md)|Décrit les principales fonctionnalités de Visual C++ dans Visual Studio et fournit un lien vers le reste de la documentation Visual C++.|

## <a name="see-also"></a>Voir aussi

[Visual C++](../visual-cpp-in-visual-studio.md)