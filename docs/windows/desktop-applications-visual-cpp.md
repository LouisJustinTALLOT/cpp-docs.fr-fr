---
title: Applications de bureau (Visual C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8e7d3612cd306dc2235b9fb4e6051415cba699c5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569792"
---
# <a name="desktop-applications-visual-c"></a>Applications de bureau (Visual C++)
A *application de bureau* en C++ est une application native qui peut accéder à l’ensemble complet d’API Windows et s’exécute dans une fenêtre ou dans la console système. Applications de bureau en C++ peuvent s’exécuter sur Windows XP et Windows 10 (bien que Windows XP n’est ne sont plus officiellement pris en charge et qu’il existe de nombreuses API Windows qui ont été introduites depuis).

Une application de bureau est distincte à partir d’une application de plateforme Windows universelle (UWP), ce qui peut s’exécuter sur des PC exécutant Windows 10 et également sur XBox, Windows Phone, Surface Hub et autres périphériques. Pour plus d’informations sur les postes de travail Visual Studio. Les applications UWP, consultez [choisir votre technologie](https://msdn.microsoft.com/en-us/library/windows/desktop/dn614993\(v=vs.85\).aspx).  


**Pont de bureau** définir des API Windows dans Windows 10 vous pouvez empaqueter votre application de bureau existante ou d’un objet COM en tant qu’une application UWP et ajoutez UWP fonctionnalités telles que touch, ou appeler des API à partir de la moderne. Vous pouvez également ajouter une application UWP pour une solution de bureau dans Visual Studio et le package dans un seul package et utiliser les API Windows pour communiquer entre eux.  
   
Dans Visual Studio 2017 une version 15.4 et versions ultérieure, vous pouvez créer un projet de Package d’Application Windows pour simplifier le travail de l’empaquetage de votre application de bureau existante. Certaines restrictions s’appliquent en ce qui concerne le Registre appelle ou utilise des API de votre application de bureau, mais dans de nombreux cas, vous pouvez créer des chemins de code de remplacement pour obtenir une fonctionnalité similaire lors de l’exécution dans un package d’application. Pour plus d’informations, consultez [bureau pont](/windows-uwp/porting/desktop-to-uwp-root).  
  
 **Terminologie**  
  
-   A *Win32* application est une application de bureau C++ peuvent utiliser native de Windows [API C de Windows et/ou APIs COM](https://msdn.microsoft.com/en-us/library/windows/desktop/ff818516\(v=vs.85\).aspx) CRT et API de bibliothèque Standard et des bibliothèques tierces 3e. Une application Win32 qui s’exécute dans une fenêtre requiert au développeur d’utiliser explicitement des messages Windows à l’intérieur d’une fonction de procédure de Windows. Malgré son nom, une application Win32 peut être compilée en tant qu’un (x86) 32 bits ou (x64) 64-bit binaire. Dans l’IDE de Visual Studio, les termes du contrat de x86 et Win32 sont synonymes.  
  
-   Le [modèle COM (Component Object)](https://msdn.microsoft.com/en-us/library/windows/desktop/ms694363\(v=vs.85\).aspx) est une spécification qui permet aux programmes écrits dans différents langages pour communiquer avec un autre. Windows de nombreux composants sont implémentés en tant qu’objets COM et suivent les règles COM standard pour créer un objet, interface destruction de découverte et d’objet.  À l’aide d’objets COM à partir d’applications de bureau C++ est relativement simple, mais l’écriture de votre propre objet COM est plus avancé. Le [bibliothèque ATL (Active Template)](../atl/atl-com-desktop-components.md) fournit des macros et fonctions d’assistance qui simplifient le développement de COM.  
  
-   Une application MFC est une application de bureau Windows qui utilisent la [Microsoft Foundation Classes](../mfc/mfc-desktop-applications.md) pour créer l’interface utilisateur. Une application MFC permettre également utiliser des composants COM, ainsi que les CRT et les API de bibliothèque Standard. MFC fournit un wrapper léger orienté objet de C++ sur la boucle de messages de fenêtre et les API Windows. MFC est l’option par défaut pour les applications, notamment des applications d’entreprise, qui ont un grand nombre de contrôles d’interface utilisateur ou des contrôles utilisateur personnalisés. MFC fournit des classes d’assistance pratiques pour la gestion des fenêtres, la sérialisation, la manipulation du texte, l’impression et les éléments d’interface utilisateur modernes tels que le ruban. Pour être efficace avec MFC, vous devez être familiarisé avec Win32.  
  
-   C + c++ / CLI application ou un composant utilise les extensions à la syntaxe C++ (tel qu’il est autorisé par la spécification C++) pour permettre l’interaction entre .NET et le code C++ natif.  C + c++ / application de CLI peut avoir des composants qui s’exécutent en mode natif et les composants qui s’exécutent sur le .NET Framework avec un accès à la bibliothèque de classes de Base .NET. C + c++ / CLI est l’option recommandée lorsque vous avez le code C++ natif qui doit fonctionner avec le code écrit en c# ou Visual Basic. Il est principalement utilisée pour une utilisation dans des DLL .NET plutôt que dans le code de l’interface utilisateur. Pour plus d’informations, consultez [programmation .NET avec C++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
 Toute application de bureau C++ peut utiliser les classes de Runtime C (CRT) et la bibliothèque Standard et des fonctions, des objets COM et les fonctions Windows publiques, appelées collectivement l’API Windows. Pour obtenir une introduction aux applications de bureau Windows en C++, consultez [Apprendre à programmer pour Windows en C++](http://go.microsoft.com/fwlink/p/?LinkId=262281).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Titre|Description|  
|-----------|-----------------|  
|[Applications console](../windows/console-applications-in-visual-cpp.md)|Contient des informations sur les applications console. Une application console Win32 (ou Win64) n’a aucune fenêtre et aucune boucle de message. Elle s'exécute dans la fenêtre de console et l'entrée et la sortie sont gérées via la ligne de commande.|  
|[Applications de bureau Windows](../windows/windows-desktop-applications-cpp.md)|Comment créer des applications de bureau qui s’exécutent dans windows, par opposition à la console.|  
|[Ressources pour la création d’un jeu à l’aide de DirectX (C++)](../windows/resources-for-creating-a-game-using-directx.md)|Liens vers le contenu pour la création de jeux en C++.|  
|[Procédure pas à pas : Création et utilisation d’une bibliothèque statique](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Comment créer un fichier binaire .lib.|  
|[Procédure : utilisation du kit SDK Windows 10 dans une application de bureau Windows](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Contient les étapes pour configurer votre projet à générer avec le Kit de développement logiciel (SDK) Windows 10.|  
  
## <a name="related-articles"></a>Articles connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Développement Windows](http://go.microsoft.com/fwlink/p/?LinkId=262282)|Contient des informations sur l'API Windows et COM. (Certaines API Windows et DLL tierces sont implémentées comme objets COM.)|  
|[Hilo : développement d’applications C++ pour Windows 7](http://go.microsoft.com/fwlink/p/?LinkId=262284)|Explique comment créer une application de bureau Windows cliente enrichie, qui utilise l’animation Windows et Direct2D pour créer une interface utilisateur de type carrousel.  Ce didacticiel n’a pas été mis à jour depuis Windows 7, mais il fournit toujours une présentation détaillée de la programmation Win32.|  
|[Visual C++](../visual-cpp-in-visual-studio.md)|Décrit les principales fonctionnalités de Visual C++ dans Visual Studio et fournit un lien vers le reste de la documentation Visual C++.|  
  
## <a name="see-also"></a>Voir aussi  
 [Visual C++](../visual-cpp-in-visual-studio.md)
