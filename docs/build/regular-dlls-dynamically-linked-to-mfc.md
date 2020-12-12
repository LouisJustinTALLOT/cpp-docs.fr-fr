---
description: 'En savoir plus sur : DLL MFC régulières liées de manière dynamique aux MFC'
title: DLL MFC normales liées de manière dynamique aux MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
ms.openlocfilehash: a16320427d881e2d37dd2afedc0566a759d59b9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273859"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>DLL MFC normales liées de manière dynamique aux MFC

Une DLL MFC normale liée de manière dynamique aux MFC est une DLL qui utilise MFC en interne, et les fonctions exportées dans la DLL peuvent être appelées par des exécutables MFC ou non-MFC. Comme son nom l’indique, ce type de DLL est généré à l’aide de la version de bibliothèque de liens dynamiques de MFC (également appelée version partagée de MFC). Les fonctions sont généralement exportées à partir d’une DLL MFC normale à l’aide de l’interface C standard.

Vous devez ajouter la `AFX_MANAGE_STATE` macro au début de toutes les fonctions exportées dans des DLL MFC standard qui sont liées de manière dynamique aux MFC pour définir l’état du module actuel à celui de la dll. Pour ce faire, ajoutez la ligne de code suivante au début des fonctions exportées à partir de la DLL :

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

Une DLL MFC normale, liée de manière dynamique aux MFC, présente les fonctionnalités suivantes :

- Il s’agit d’un nouveau type de DLL introduit par Visual C++ 4,0.

- L’exécutable client peut être écrit dans n’importe quel langage qui prend en charge l’utilisation de dll (C, C++, Pascal, Visual Basic, etc.); Il n’est pas nécessaire qu’il s’agit d’une application MFC.

- Contrairement à la DLL MFC normale liée de manière statique, ce type de DLL est lié de manière dynamique à la DLL MFC (également appelée DLL MFC partagée).

- La bibliothèque d’importation MFC liée à ce type de DLL est la même que celle utilisée pour les dll d’extension MFC ou les applications utilisant la DLL MFC : MFCxx (D). lib.

Une DLL MFC normale, liée de manière dynamique aux MFC, présente les exigences suivantes :

- Ces dll sont compilées avec **_AFXDLL** définie, tout comme un fichier exécutable qui est lié dynamiquement à la DLL MFC. Toutefois, **_USRDLL** est également défini, tout comme une DLL MFC normale liée de manière statique aux MFC.

- Ce type de DLL doit instancier une `CWinApp` classe dérivée de.

- Ce type de DLL utilise le `DllMain` fourni par MFC. Placez tout le code d’initialisation propre à la DLL dans la `InitInstance` fonction membre et le code d’arrêt dans `ExitInstance` comme dans une application MFC normale.

Étant donné que ce type de DLL utilise la version de bibliothèque de liens dynamiques de MFC, vous devez définir explicitement l’état du module actuel à celui de la DLL. Pour ce faire, utilisez la macro [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) au début de chaque fonction exportée à partir de la dll.

les DLL MFC normales doivent avoir une `CWinApp` classe dérivée de et un objet unique de cette classe d’application, comme c’est le cas pour une application MFC. Toutefois, l' `CWinApp` objet de la dll n’a pas de pompe de messages principale, comme l' `CWinApp` objet d’une application.

Notez que le `CWinApp::Run` mécanisme ne s’applique pas à une dll, car l’application possède la pompe de messages principale. Si votre DLL affiche des boîtes de dialogue non modales ou possède sa propre fenêtre frame principale, la pompe de messages principale de votre application doit appeler une routine exportée par la DLL qui appelle `CWinApp::PreTranslateMessage` .

Placez toute l’initialisation propre à la DLL dans la `CWinApp::InitInstance` fonction membre comme dans une application MFC normale. La `CWinApp::ExitInstance` fonction membre de votre `CWinApp` classe dérivée est appelée à partir de la fonction fournie par la bibliothèque MFC `DllMain` avant le déchargement de la dll.

Vous devez distribuer les DLL partagées MFCx0.dll et Msvcr * 0.dll (ou des fichiers similaires) à votre application.

Une DLL liée de manière dynamique aux MFC ne peut pas également être liée de manière statique aux MFC. Les applications sont liées aux DLL MFC normales liées de manière dynamique aux MFC, comme n’importe quelle autre DLL.

Les symboles sont généralement exportés à partir d’une DLL MFC normale à l’aide de l’interface C standard. La déclaration d’une fonction exportée à partir d’une DLL MFC normale ressemble à ceci :

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Toutes les allocations de mémoire dans une DLL MFC normale doivent rester dans la DLL. la DLL ne doit pas passer à l’exécutable appelant ou en recevoir de l’un des éléments suivants :

- pointeurs vers des objets MFC

- pointeurs vers la mémoire allouée par MFC

Si vous devez effectuer l’une des actions ci-dessus ou si vous devez passer des objets dérivés de MFC entre l’exécutable appelant et la DLL, vous devez générer une DLL d’extension MFC.

Il est possible de transmettre en toute sécurité des pointeurs vers la mémoire allouée par les bibliothèques Runtime C entre une application et une DLL uniquement si vous effectuez une copie des données. Vous ne devez pas supprimer ou redimensionner ces pointeurs, ni les utiliser sans effectuer une copie de la mémoire.

Lors de la génération d’une DLL MFC normale liée de manière dynamique aux MFC, vous devez utiliser la macro [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) pour basculer correctement l’état du module MFC. Pour ce faire, ajoutez la ligne de code suivante au début des fonctions exportées à partir de la DLL :

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

La macro **AFX_MANAGE_STATE** ne doit pas être utilisée dans les DLL MFC standard qui sont liées statiquement aux MFC ou aux DLL d’extension MFC. Pour plus d’informations, consultez [gestion des données d’état des modules MFC](../mfc/managing-the-state-data-of-mfc-modules.md).

Pour obtenir un exemple d’écriture, de génération et d’utilisation d’une DLL MFC standard, consultez l’exemple [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap). Pour plus d’informations sur les DLL MFC normales liées de manière dynamique aux MFC, consultez la section intitulée « conversion de DLLScreenCap en liaison dynamique avec la DLL MFC » dans le résumé de l’exemple.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Initialiser des DLL MFC normales](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [États du module d’une DLL MFC normale liée de manière dynamique aux MFC](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [Gestion des données d'état des modules MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Utilisation de DLL d’extension MFC de base de données, OLE et sockets dans des DLL MFC normales](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Utilisation de MFC dans le cadre d’une DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>Voir aussi

[Types de DLL](kinds-of-dlls.md)
