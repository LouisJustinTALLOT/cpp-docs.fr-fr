---
title: DLL MFC normales liées de manière dynamique aux MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
ms.openlocfilehash: 550391d51560ff0beca8252ffb6193dd1e4d89b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632386"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>DLL MFC normales liées de manière dynamique aux MFC

Une expression régulière que MFC DLL liée de manière dynamique aux MFC est une DLL qui utilise MFC en interne, et les fonctions exportées dans la DLL peuvent être appelées par des exécutables MFC ou non-MFC. Comme son nom l’indique, ce type de DLL est généré à l’aide de la version de la bibliothèque de liens dynamiques de la bibliothèque MFC (également connu sous la version partagée des MFC). Fonctions sont généralement exportées à partir d’un DLL MFC à l’aide de l’interface C standard normal.

Vous devez ajouter le `AFX_MANAGE_STATE` macro au début de toutes les fonctions exportées dans des DLL MFC normales liées de manière dynamique aux MFC pour définir l’état du module en cours à celui de la DLL. Cette opération est effectuée en ajoutant la ligne de code suivante au début des fonctions exportées à partir de la DLL :

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

Une expression régulière DLL MFC, est liée de manière dynamique aux MFC présente les caractéristiques suivantes :

- Il s’agit d’un nouveau type de DLL introduit par Visual C++ 4.0.

- L’exécutable client peut être écrites dans n’importe quel langage qui prend en charge l’utilisation de DLL (C, C++, Pascal, Visual Basic et ainsi de suite) ; Il ne devra pas être une application MFC.

- Contrairement à la DLL MFC normale liée statiquement, ce type de DLL est dynamiquement lié à la DLL MFC (également connu sous la DLL MFC partagée).

- La bibliothèque d’importation MFC liée à ce type de DLL est identique à celle utilisée pour les DLL d’extension MFC ou des applications à l’aide de la DLL MFC : MFCxx (D) .lib.

Une expression régulière DLL MFC, est liée de manière dynamique aux MFC possède les conditions suivantes :

- Ces DLL est compilés avec **_AFXDLL** défini, tout comme un fichier exécutable qui est lié de manière dynamique à la DLL de MFC. Mais **_USRDLL** est également défini, tout comme une DLL MFC normale liée de manière statique aux MFC.

- Ce type de DLL doit instancier un `CWinApp`-classe dérivée.

- Ce type de DLL utilise le `DllMain` fournies par MFC. Placez tout le code d’initialisation des DLL dans le `InitInstance` code de fonction et d’arrêt de membre dans `ExitInstance` comme dans une application MFC normale.

Étant donné que ce type de DLL utilise la version DLL de MFC, vous devez explicitement définir l’état du module en cours à celui de la DLL. Pour ce faire, utilisez le [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) macro au début de chaque fonction exportée à partir de la DLL.

DLL MFC normales doit avoir un `CWinApp`-dérivée de classe et un seul objet de cette classe d’application, comme une application MFC. Toutefois, le `CWinApp` objet de la DLL n’a pas de pompe de messages principale, comme le fait le `CWinApp` objet d’une application.

Notez que le `CWinApp::Run` mécanisme ne s’applique pas à une DLL, étant donné que l’application qui possède la pompe de messages principale. Si votre DLL met des boîtes de dialogue non modales ou possède une fenêtre frame principale propre, pompe de messages principale de votre application doit appeler une routine exportée par la DLL qui appelle `CWinApp::PreTranslateMessage`.

Placez l’initialisation des DLL dans le `CWinApp::InitInstance` fonction membre, comme dans une application MFC normale. Le `CWinApp::ExitInstance` fonction membre de votre `CWinApp` classe dérivée est appelée à partir de la bibliothèque MFC fournie `DllMain` fonctionner avant que la DLL est déchargée.

Vous devez distribuer les DLL partagées MFCx0.dll et Msvcr*0.dll (ou des fichiers similaires) avec votre application.

Une DLL liée de manière dynamique aux MFC ne peut pas lier également statiquement à MFC. Lien d’applications pour des DLL MFC normales liées dynamiquement à MFC il comme n’importe quel autre DLL.

Symboles sont généralement exportés à partir d’un DLL MFC à l’aide de l’interface C standard normal. La déclaration d’une fonction exportée à partir d’une DLL MFC normale ressemble à ceci :

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Toutes les allocations de mémoire dans une DLL MFC normale doivent rester dans la DLL ; la DLL ne doit pas passer à ou de réception à partir de l’exécutable appelant les éléments suivants :

- pointeurs vers les objets MFC

- pointeurs vers la mémoire allouée par MFC

Si vous avez besoin effectuer l’une des options ci-dessus, ou si vous avez besoin passer des objets dérivés des MFC entre l’exécutable appelant et la DLL, vous devez générer une DLL d’extension MFC.

Il est possible de passer des pointeurs vers la mémoire qui ont été alloués par les bibliothèques Runtime C entre une application et une DLL seulement si vous effectuez une copie des données. Vous ne devez pas supprimer ou redimensionner ces pointeurs ou les utiliser sans avoir à effectuer une copie de la mémoire.

Lors de la génération d’une DLL MFC normale qui dynamiquement est liée à MFC, vous devez utiliser la macro [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) pour changer l’état du module MFC correctement. Cette opération est effectuée en ajoutant la ligne de code suivante au début des fonctions exportées à partir de la DLL :

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

Le **AFX_MANAGE_STATE** macro ne doit pas être utilisée dans des DLL MFC normales liées de manière statique aux MFC ou dans la DLL d’extension MFC. Pour plus d’informations, consultez [la gestion des données d’état des Modules MFC](../mfc/managing-the-state-data-of-mfc-modules.md).

Pour obtenir un exemple montrant comment écrire, créer et utiliser une DLL MFC normale, consultez l’exemple [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap). Pour plus d’informations sur les DLL MFC normales de manière dynamique aux MFC, consultez la section intitulée « Conversion de DLLScreenCap à une liaison dynamique avec la DLL MFC » dans le résumé de l’exemple.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Initialiser des DLL MFC normales](../build/run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [États du module d’une DLL MFC normale liée de manière dynamique aux MFC](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [Gestion des données d’état des modules MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Utilisation de DLL d’extension de MFC de type base de données, OLE et sockets dans des DLL MFC normales](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [À l’aide de MFC dans le cadre d’une DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>Voir aussi

[Genres de DLL](../build/kinds-of-dlls.md)