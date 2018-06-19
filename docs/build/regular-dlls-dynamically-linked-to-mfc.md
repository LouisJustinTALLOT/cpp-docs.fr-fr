---
title: DLL régulière MFC liées dynamiquement à MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e20a3937786d65945256eeadcf0bf08b0314470
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383725"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>DLL régulière MFC liées dynamiquement à MFC
Une expression régulière que MFC DLL liée dynamiquement à MFC est une DLL qui utilise MFC en interne, et les fonctions exportées de la DLL peuvent être appelées par des exécutables MFC ou non MFC. Comme son nom l’indique, ce type de DLL est généré à l’aide de la version de la bibliothèque de liens dynamiques des MFC (également appelée la version partagée de MFC). Les fonctions sont généralement exportées à partir d’une expression régulière DLL MFC à l’aide de l’interface C standard.  
  
 Vous devez ajouter le `AFX_MANAGE_STATE` macro au début de toutes les fonctions exportées dans la DLL régulière MFC de manière dynamique aux MFC pour définir l’état du module en cours à celui de la DLL. Cela est effectué en ajoutant la ligne de code suivante au début des fonctions exportées à partir de la DLL :  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 Une expression régulière DLL MFC, liée dynamiquement à MFC présente les caractéristiques suivantes :  
  
-   Il s’agit d’un nouveau type de DLL introduit par Visual C++ 4.0.  
  
-   Le fichier exécutable du client peut être écrites dans n’importe quel langage qui prend en charge l’utilisation des DLL (C, C++, Pascal, Visual Basic et ainsi de suite) ; Il n’a pas à être une application MFC.  
  
-   Contrairement à la DLL MFC régulière lié de manière statique, ce type de DLL est lié dynamiquement à la DLL MFC (également appelée la DLL MFC partagée).  
  
-   La bibliothèque d’importation MFC liée à ce type de DLL est la même que celle utilisée pour les DLL d’extension MFC ou des applications à l’aide de la DLL MFC : MFCxx (D) .lib.  
  
 Une expression régulière DLL MFC, liée dynamiquement à MFC a les conditions suivantes :  
  
-   Ces DLL est compilés avec **_AFXDLL** défini, tout comme un exécutable qui est lié dynamiquement à la DLL MFC. Mais **_USRDLL** est également défini, tout comme une DLL régulière MFC liée de manière statique aux MFC.  
  
-   Ce type de DLL doit instancier un `CWinApp`-classe dérivée.  
  
-   Ce type de DLL utilise la `DllMain` fournies par MFC. Placez tout le code d’initialisation des DLL dans le `InitInstance` code de fonction et l’arrêt du membre dans `ExitInstance` comme dans une application MFC normale.  
  
 Étant donné que ce type de DLL utilise la version DLL de MFC, vous devez explicitement définir l’état du module en cours à celui de la DLL. Pour ce faire, utilisez le [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) macro au début de chaque fonction exportée à partir de la DLL.  
  
 les DLL régulières MFC doit avoir un `CWinApp`-dérivée de classe et un objet unique de cette classe d’application, contrairement à une application MFC. Toutefois, le `CWinApp` objet de la DLL n’a pas de pompe de messages principale, comme le fait le `CWinApp` l’objet d’une application.  
  
 Notez que le `CWinApp::Run` mécanisme ne s’applique pas à une DLL, car l’application qui possède la pompe de messages principale. Si votre DLL met des boîtes de dialogue non modales ou possède une fenêtre frame principale propre, pompe de messages principale de votre application doit appeler une routine exportée par la DLL qui appelle `CWinApp::PreTranslateMessage`.  
  
 Placez l’initialisation des DLL dans le `CWinApp::InitInstance` fonction membre comme dans une application MFC normale. Le `CWinApp::ExitInstance` fonction membre de votre `CWinApp` classe dérivée est appelée à partir de la bibliothèque MFC fournie `DllMain` fonction avant que la DLL est déchargée.  
  
 Vous devez distribuer les DLL partagées MFCx0.dll et Msvcr*0.dll (ou des fichiers similaires) avec votre application.  
  
 Une DLL liée de manière dynamique aux MFC ne peut pas lier également statiquement à MFC. Lien d’applications pour les DLL régulières MFC liées dynamiquement à MFC il comme n’importe quel autre DLL.  
  
 Symboles sont généralement exportés à partir d’une expression régulière DLL MFC à l’aide de l’interface C standard. La déclaration d’une fonction exportée à partir d’une DLL MFC normale ressemble à ceci :  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 Toutes les allocations de mémoire dans une DLL MFC normale doivent rester au sein de la DLL ; la DLL ne doit pas passer à ou de réception à partir de l’exécutable appelant une des opérations suivantes :  
  
-   Pointeurs vers les objets MFC  
  
-   Pointeurs vers la mémoire allouée par MFC  
  
 Si vous avez besoin effectuer l’une des éléments ci-dessus, ou si vous avez besoin passer des objets dérivés des MFC entre l’exécutable appelant et la DLL, vous devez générer une DLL d’extension MFC.  
  
 Il est possible de passer des pointeurs vers la mémoire alloués par les bibliothèques Runtime C entre une application et une DLL seulement si vous effectuez une copie des données. Vous ne devez pas supprimer ou redimensionner ces pointeurs ou les utiliser sans faire de copie de la mémoire.  
  
 Lorsque vous générez une DLL de MFC standard qui dynamiquement liée à MFC, vous devez utiliser la macro [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) pour changer l’état du module MFC correctement. Cela est effectué en ajoutant la ligne de code suivante au début des fonctions exportées à partir de la DLL :  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
 Le **AFX_MANAGE_STATE** macro ne doit pas être utilisée dans des DLL MFC normales liées de manière statique aux MFC ou dans la DLL d’extension MFC. Pour plus d’informations, consultez [la gestion des données d’état des Modules MFC](../mfc/managing-the-state-data-of-mfc-modules.md).  
  
 Pour obtenir un exemple montrant comment écrire, générer et utiliser une DLL normale de MFC, consultez l’exemple [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap). Pour plus d’informations sur les DLL régulières MFC de manière dynamique aux MFC, consultez la section intitulée « Conversion de DLLScreenCap pour une liaison dynamique avec la DLL MFC » dans le résumé de l’exemple.  
  
## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Initialiser des DLL régulière MFC](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [États du module d’une DLL MFC normale liée de manière dynamique aux MFC](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
  
-   [Gestion des données d’état des modules MFC](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [Utilisation de DLL d’extension de MFC de type base de données, OLE et sockets dans des DLL MFC normales](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [Utilisation de MFC dans le cadre d’une DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Genres de DLL](../build/kinds-of-dlls.md)