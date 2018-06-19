---
title: DLL régulière MFC liées de manière statique aux MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c48fdfb0b10541c1643ec49038e29cfa60c633d9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383746"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>DLL régulière MFC liées statiquement aux MFC
Une expression régulière que MFC DLL liée de manière statique aux MFC est une DLL qui utilise MFC en interne, et les fonctions exportées de la DLL peuvent être appelées par des exécutables MFC ou non MFC. Comme son nom l’indique, ce type de DLL est généré à l’aide de la version de bibliothèque de liens statiques de MFC. Les fonctions sont généralement exportées à partir d’une expression régulière DLL MFC à l’aide de l’interface C standard. Pour obtenir un exemple montrant comment écrire, générer et utiliser une DLL normale de MFC, consultez l’exemple [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap).  
  
 Notez que le terme USRDLL n’est plus utilisé dans la documentation Visual C++. Une DLL MFC normale liée de manière statique aux MFC possède les mêmes caractéristiques que l’ancienne USRDLL.  
  
 Une DLL MFC normale, liées de manière statique aux MFC, comporte les fonctionnalités suivantes :  
  
-   Le fichier exécutable du client peut être écrites dans n’importe quel langage qui prend en charge l’utilisation des DLL (C, C++, Pascal, Visual Basic et ainsi de suite) ; Il n’a pas à être une application MFC.  
  
-   La DLL peut être liée aux mêmes bibliothèques de liens statiques MFC utilisés par les applications. Il n’est plus une version distincte des bibliothèques de liens statiques pour les DLL.  
  
-   Avant la version 4.0 de MFC, les USRDLL offraient le même type de fonctionnalités que les DLL MFC normales liées de manière statique aux MFC. À compter de Visual C++ version 4.0, le terme USRDLL est obsolète.  
  
 Une DLL MFC normale, liées de manière statique aux MFC, présente les exigences suivantes :  
  
-   Ce type de DLL doit instancier une classe dérivée de `CWinApp`.  
  
-   Ce type de DLL utilise la `DllMain` fournies par MFC. Placez tout le code d’initialisation des DLL dans le `InitInstance` code de fonction et l’arrêt du membre dans `ExitInstance` comme dans une application MFC normale.  
  
-   Même si le terme USRDLL est obsolète, vous devez toujours définir «**_USRDLL**» sur la ligne de commande du compilateur. Cette définition détermine les déclarations qui sont extraites les fichiers d’en-tête MFC.  
  
 les DLL régulières MFC doit avoir un `CWinApp`-dérivée de classe et un objet unique de cette classe d’application, contrairement à une application MFC. Toutefois, le `CWinApp` objet de la DLL n’a pas de pompe de messages principale, comme le fait le `CWinApp` l’objet d’une application.  
  
 Notez que le `CWinApp::Run` mécanisme ne s’applique pas à une DLL, car l’application qui possède la pompe de messages principale. Si la DLL ouvre des boîtes de dialogue non modales ou possède une fenêtre frame principale propre, pompe de messages principale de l’application doit appeler une routine exportée par la DLL qui appelle à son tour le `CWinApp::PreTranslateMessage` fonction membre de l’objet d’application de la DLL.  
  
 Pour obtenir un exemple de cette fonction, consultez l’exemple DLLScreenCap.  
  
 Symboles sont généralement exportés à partir d’une expression régulière DLL MFC à l’aide de l’interface C standard. La déclaration d’une fonction exportée à partir d’une DLL MFC normale ressemblerait à ceci :  
  
```  
extern "C" __declspec(dllexport) MyExportedFunction( );  
```  
  
 Toutes les allocations de mémoire dans une DLL MFC normale doivent rester au sein de la DLL ; la DLL ne doit pas passer à ou de réception à partir de l’exécutable appelant une des opérations suivantes :  
  
-   Pointeurs vers les objets MFC  
  
-   Pointeurs vers la mémoire allouée par MFC  
  
 Si vous devez effectuer l’une des éléments ci-dessus ou passer des objets dérivés des MFC entre l’exécutable appelant et la DLL, vous devez générer une DLL d’extension MFC.  
  
 Il est possible de passer des pointeurs vers la mémoire alloués par les bibliothèques Runtime C entre une application et une DLL seulement si vous effectuez une copie des données. Vous ne devez pas supprimer ou redimensionner ces pointeurs ou les utiliser sans faire de copie de la mémoire.  
  
 Une DLL liée de manière statique aux MFC ne peut pas lier également dynamiquement aux DLL MFC partagée. Une DLL liée de manière statique aux MFC est dynamiquement liée à une application comme n’importe quel autre DLL ; lier des applications à ce dernier comme n’importe quel autre DLL.  
  
 Les bibliothèques de liens statiques MFC standards sont nommées selon la convention décrite dans [les Conventions d’affectation de noms pour les DLL MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Toutefois, avec MFC version 3.0 et versions ultérieure, il n’est plus nécessaire de spécifier manuellement à l’éditeur de liens de la version de la bibliothèque MFC à lier. Au lieu de cela, les fichiers d’en-tête MFC déterminent automatiquement définit la version correcte de la bibliothèque MFC à lier dans en fonction de préprocesseur, telles que  **\_déboguer** ou **_UNICODE**. Les fichiers d’en-tête MFC ajoutent les directives /DEFAULTLIB en demandant l’éditeur de liens à lier dans une version spécifique de la bibliothèque MFC.  
  
## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Initialiser des DLL régulière MFC](../build/run-time-library-behavior.md#initializing-regular-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [Utilisation de MFC dans le cadre d’une DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
  
-   [Utilisation de DLL d’extension de MFC de type base de données, OLE et sockets dans des DLL MFC normales](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [Création d’une DLL MFC](../mfc/reference/mfc-dll-wizard.md)  
  
-   [DLL MFC normales liées de manière dynamique à MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [DLL d’extension de MFC](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Genres de DLL](../build/kinds-of-dlls.md)