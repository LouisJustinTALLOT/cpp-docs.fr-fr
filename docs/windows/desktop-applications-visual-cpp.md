---
description: En savoir plus sur les applications de bureau (Visual C++)
title: Applications de bureau (Visual C++)
ms.date: 07/28/2019
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
ms.topic: overview
ms.openlocfilehash: eb7badb73af507d31c9dd982f0a6189362249a3b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114752"
---
# <a name="desktop-applications-visual-c"></a>Applications de bureau (Visual C++)

Une *application de bureau* en C++ est une application native qui peut accéder à l’ensemble des API Windows et s’exécute dans une fenêtre ou dans la console système. Les applications de bureau en C++ peuvent s’exécuter sur Windows XP via Windows 10 (même si Windows XP n’est plus officiellement pris en charge et que de nombreuses API Windows ont été introduites depuis).

Une application de bureau est distincte d’une application de plateforme Windows universelle (UWP), qui peut s’exécuter sur des PC exécutant Windows 10 et également sur XBox, Windows Phone, Surface Hub et d’autres appareils. Pour plus d’informations sur les applications Desktop et UWP, consultez [choisir votre technologie](/windows/win32/choose-your-technology).

## <a name="desktop-bridge"></a>Pont du bureau

Dans Windows 10, vous pouvez empaqueter votre application de bureau ou votre objet COM existant en tant qu’application UWP et ajouter des fonctionnalités UWP, telles que Touch, ou appeler des API à partir du jeu d’API Windows moderne. Vous pouvez également ajouter une application UWP à une solution de bureau dans Visual Studio et les empaqueter dans un package unique et utiliser des API Windows pour communiquer entre elles.

Dans Visual Studio 2017 version 15,4 et versions ultérieures, vous pouvez créer un projet de package d’application Windows pour simplifier de manière considérable le travail d’empaquetage de votre application de bureau existante. Quelques restrictions s’appliquent en ce qui concerne les appels de registre ou les API utilisés par votre application de bureau, mais dans de nombreux cas, vous pouvez créer d’autres chemins de code pour obtenir des fonctionnalités similaires lors de l’exécution dans un package d’application. Pour plus d’informations, consultez [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="terminology"></a>Terminologie

- Une application *Win32* est une application de bureau Windows en C++ qui peut utiliser des API [Windows C natives et/ou](/windows/win32/apiindex/windows-api-list) des API de bibliothèque CRT et d’API com, ainsi que des bibliothèques tierces. Une application Win32 qui s’exécute dans une fenêtre exige que le développeur travaille explicitement avec des messages Windows dans une fonction de procédure Windows. Malgré le nom, une application Win32 peut être compilée en tant que binaire 32 bits (x86) ou 64 bits (x64). Dans l’IDE de Visual Studio, les termes x86 et Win32 sont synonymes.

- Le [modèle COM (Component Object Model)](/windows/win32/com/the-component-object-model) est une spécification qui permet aux programmes écrits dans différents langages de communiquer les uns avec les autres. De nombreux composants Windows sont implémentés en tant qu’objets COM et suivent des règles COM standard pour la création d’objets, la découverte d’interfaces et la destruction d’objets.  L’utilisation d’objets COM à partir d’applications de bureau C++ est relativement simple, mais l’écriture de votre propre objet COM est plus avancée. La [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) fournit des macros et des fonctions d’assistance qui simplifient le développement com.

- Une application MFC est une application de bureau Windows qui utilise la [Microsoft Foundation classes](../mfc/mfc-desktop-applications.md) pour créer l’interface utilisateur. Une application MFC peut également utiliser des composants COM, ainsi que des API CRT et de bibliothèque standard. MFC fournit un wrapper orienté objet C++ étroit sur la boucle de message de fenêtre et les API Windows. MFC est le choix par défaut pour les applications, en particulier les applications de type entreprise, qui possèdent un grand nombre de contrôles d’interface utilisateur ou de contrôles utilisateur personnalisés. MFC fournit des classes d’assistance pratiques pour la gestion des fenêtres, la sérialisation, la manipulation de texte, l’impression et les éléments d’interface utilisateur modernes tels que le ruban. Pour être efficace avec MFC, vous devez être familiarisé avec Win32.

- Une application ou un composant C++/CLI utilise des extensions à la syntaxe C++ (comme le permettait la norme C++) pour permettre l’interaction entre .NET et le code c++ natif.  Une application C++/CLI peut avoir des composants qui s’exécutent en mode natif et des composants qui s’exécutent sur le .NET Framework avec un accès à la bibliothèque de classes de base .NET. C++/CLI est l’option recommandée lorsque vous avez du code C++ natif qui doit utiliser du code écrit en C# ou Visual Basic. Elle est destinée à être utilisée dans les dll .NET plutôt que dans le code de l’interface utilisateur. Pour plus d’informations, consultez [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Toute application de bureau en C++ peut utiliser C Runtime (CRT) et des classes et des fonctions de bibliothèque standard, des objets COM et les fonctions Windows publiques, qui sont collectivement appelées API Windows. Pour une introduction aux applications de bureau Windows en C++, consultez [prise en main de Win32 et c++](/windows/win32/LearnWin32/learn-to-program-for-windows).

## <a name="in-this-section"></a>Dans cette section

|Titre|Description|
|-----------|-----------------|
|[Application console Windows en C++](./overview-of-windows-programming-in-cpp.md)|Contient des informations sur les applications console. Une application console Win32 (ou Win64) n’a aucune fenêtre et aucune boucle de message. Elle s'exécute dans la fenêtre de console et l'entrée et la sortie sont gérées via la ligne de commande.|
|[Procédure pas à pas : création d’applications de bureau Windows (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Créer une application de bureau Windows simple.|
|[Création d’une application de bureau Windows vide](./overview-of-windows-programming-in-cpp.md)|Comment créer un projet de bureau Windows qui n’a pas de fichiers par défaut.|
|[Ajout de fichiers à des applications Win32 vides](./overview-of-windows-programming-in-cpp.md)|Comment ajouter des fichiers à un projet vide.|
|[Utilisation des fichiers de ressources](working-with-resource-files.md)|Comment ajouter des images, des icônes, des tables de chaînes et d’autres ressources à une application de bureau.|
|[Ressources pour la création d'un jeu à l'aide de DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Liens vers du contenu pour la création de jeux en C++.|
|[Procédure pas à pas : création et utilisation d'une bibliothèque statique](../build/walkthrough-creating-and-using-a-static-library-cpp.md)|Comment créer un fichier binaire. lib.|
|[Comment : utiliser le kit de développement logiciel (SDK) Windows 10 dans une application de bureau Windows](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Contient les étapes pour configurer votre projet à générer avec le Kit de développement logiciel (SDK) Windows 10.|

## <a name="related-articles"></a>Articles connexes

|Titre|Description|
|-----------|-----------------|
|[Développement Windows](/windows/win32/index)|Contient des informations sur l'API Windows et COM. (Certaines API Windows et DLL tierces sont implémentées comme objets COM.)|
|[Hilo : développement d’applications C++ pour Windows 7](/previous-versions/msdn10/ff708696(v=msdn.10))|Explique comment créer une application de bureau Windows cliente enrichie, qui utilise l’animation Windows et Direct2D pour créer une interface utilisateur de type carrousel.  Ce didacticiel n’a pas été mis à jour depuis Windows 7, mais il fournit toujours une introduction complète à la programmation Win32.|
|[Vue d’ensemble de la programmation Windows en C++](overview-of-windows-programming-in-cpp.md)|Décrit les principales fonctionnalités de la programmation Windows Desktop en C++.|

## <a name="see-also"></a>Voir aussi

[C++ dans Visual Studio](../overview/visual-cpp-in-visual-studio.md)
