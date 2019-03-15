---
title: DLL MFC normales liées de manière statique aux MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
ms.openlocfilehash: 1f05b5e3c268935cf3161fb7184e04b3e3ea1446
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815799"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>DLL MFC normales liées de manière statique aux MFC

Une expression régulière que MFC DLL liée de manière statique aux MFC est une DLL qui utilise MFC en interne, et les fonctions exportées dans la DLL peuvent être appelées par des exécutables MFC ou non-MFC. Comme son nom l’indique, ce type de DLL est généré à l’aide de la version de bibliothèque de liens statiques de MFC. Fonctions sont généralement exportées à partir d’un DLL MFC à l’aide de l’interface C standard normal. Pour obtenir un exemple montrant comment écrire, créer et utiliser une DLL MFC normale, consultez l’exemple [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap).

Notez que le terme USRDLL n’est plus utilisé dans la documentation de Visual C++. Une DLL MFC normale liée de manière statique aux MFC possède les mêmes caractéristiques que l’ancienne USRDLL.

Une DLL MFC normale, liées de manière statique aux MFC, présente les caractéristiques suivantes :

- L’exécutable client peut être écrites dans n’importe quel langage qui prend en charge l’utilisation de DLL (C, C++, Pascal, Visual Basic et ainsi de suite) ; Il ne devra pas être une application MFC.

- La DLL peut être liée aux mêmes bibliothèques de liens statiques MFC utilisées par les applications. Il n’est plus une version distincte des bibliothèques de liens statiques pour les DLL.

- Avant la version 4.0 de MFC, les USRDLL offraient le même type de fonctionnalités que les DLL MFC normales liées de manière statique aux MFC. À compter de Visual C++ version 4.0, le terme USRDLL est obsolète.

Une DLL MFC normale, liées de manière statique aux MFC, présente les exigences suivantes :

- Ce type de DLL doit instancier une classe dérivée de `CWinApp`.

- Ce type de DLL utilise le `DllMain` fournies par MFC. Placez tout le code d’initialisation des DLL dans le `InitInstance` code de fonction et d’arrêt de membre dans `ExitInstance` comme dans une application MFC normale.

- Même si le terme USRDLL est obsolète, vous devez toujours définir «**_USRDLL**» sur la ligne de commande du compilateur. Cette définition détermine les déclarations qui sont extraites les fichiers d’en-tête MFC.

DLL MFC normales doit avoir un `CWinApp`-dérivée de classe et un seul objet de cette classe d’application, comme une application MFC. Toutefois, le `CWinApp` objet de la DLL n’a pas de pompe de messages principale, comme le fait le `CWinApp` objet d’une application.

Notez que le `CWinApp::Run` mécanisme ne s’applique pas à une DLL, étant donné que l’application qui possède la pompe de messages principale. Si la DLL ouvre des boîtes de dialogue non modales ou possède une fenêtre frame principale de son propre, pompe de messages principale de l’application doit appeler une routine exportée par la DLL qui appelle à son tour le `CWinApp::PreTranslateMessage` fonction membre de l’objet d’application de la DLL.

Pour obtenir un exemple de cette fonction, consultez l’exemple DLLScreenCap.

Symboles sont généralement exportés à partir d’un DLL MFC à l’aide de l’interface C standard normal. La déclaration d’une fonction exportée à partir d’une DLL MFC normale ressemblent à ceci :

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Toutes les allocations de mémoire dans une DLL MFC normale doivent rester dans la DLL ; la DLL ne doit pas passer à ou de réception à partir de l’exécutable appelant les éléments suivants :

- pointeurs vers les objets MFC

- pointeurs vers la mémoire allouée par MFC

Si vous avez besoin effectuer l’une des options ci-dessus, ou pour transmettre des objets dérivés des MFC entre l’exécutable appelant et la DLL, vous devez générer une DLL d’extension MFC.

Il est possible de passer des pointeurs vers la mémoire qui ont été alloués par les bibliothèques Runtime C entre une application et une DLL seulement si vous effectuez une copie des données. Vous ne devez pas supprimer ou redimensionner ces pointeurs ou les utiliser sans avoir à effectuer une copie de la mémoire.

Une DLL liée de manière statique aux MFC ne peut pas lier également dynamiquement aux DLL MFC partagée. Une DLL liée de manière statique aux MFC est dynamiquement liée à une application comme n’importe quel autre DLL ; le lien vers les applications comme n’importe quel autre DLL.

Les bibliothèques de liens statiques MFC standards sont nommées selon la convention décrite dans [Conventions de nommage pour les DLL MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Toutefois, avec MFC version 3.0 et versions ultérieure, il n’est plus nécessaire de spécifier manuellement à l’éditeur de liens de la version de la bibliothèque MFC à lier. Au lieu de cela, les fichiers d’en-tête MFC déterminent automatiquement définit la version correcte de la bibliothèque MFC à lier dans en fonction de préprocesseur, telles que  **\_déboguer** ou **_UNICODE**. Les fichiers d’en-tête MFC ajoutent les directives /DEFAULTLIB en demandant l’éditeur de liens à lier dans une version spécifique de la bibliothèque MFC.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Initialiser des DLL MFC normales](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [À l’aide de MFC dans le cadre d’une DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [Utilisation de DLL d’extension de MFC de type base de données, OLE et sockets dans des DLL MFC normales](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Création d’une DLL MFC](../mfc/reference/mfc-dll-wizard.md)

- [DLL MFC normales liées de manière dynamique à MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [DLL d’extension de MFC](extension-dlls-overview.md)

## <a name="see-also"></a>Voir aussi

[Genres de DLL](kinds-of-dlls.md)
