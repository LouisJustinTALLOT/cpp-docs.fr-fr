---
description: 'En savoir plus sur : DLL MFC régulières liées statiquement à MFC'
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
ms.openlocfilehash: b213be6bf076557fc57a5bcac62cbf9767587bd3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273798"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>DLL MFC normales liées de manière statique aux MFC

Une DLL MFC normale liée de manière statique aux MFC est une DLL qui utilise MFC en interne, et les fonctions exportées dans la DLL peuvent être appelées par des exécutables MFC ou non-MFC. Comme son nom l’indique, ce type de DLL est généré à l’aide de la version de bibliothèque de liens statique de MFC. Les fonctions sont généralement exportées à partir d’une DLL MFC normale à l’aide de l’interface C standard. Pour obtenir un exemple d’écriture, de génération et d’utilisation d’une DLL MFC standard, consultez l’exemple [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap).

Notez que le terme USRDLL n’est plus utilisé dans la documentation Visual C++. Une DLL MFC normale liée de manière statique aux MFC a les mêmes caractéristiques que l’ancienne USRDLL.

Une DLL MFC normale, liée de manière statique aux MFC, présente les fonctionnalités suivantes :

- L’exécutable client peut être écrit dans n’importe quel langage qui prend en charge l’utilisation de dll (C, C++, Pascal, Visual Basic, etc.); Il n’est pas nécessaire qu’il s’agit d’une application MFC.

- La DLL peut être liée aux mêmes bibliothèques de liens statiques MFC que celles utilisées par les applications. Il n’existe plus de version distincte des bibliothèques de liens statiques pour les dll.

- Avant la version 4,0 de MFC, USRDLL offrait le même type de fonctionnalités que les DLL MFC normales liées de manière statique aux MFC. À partir de Visual C++ version 4,0, le terme USRDLL est obsolète.

Une DLL MFC normale, liée de manière statique aux MFC, présente les exigences suivantes :

- Ce type de DLL doit instancier une classe dérivée de `CWinApp` .

- Ce type de DLL utilise le `DllMain` fourni par MFC. Placez tout le code d’initialisation propre à la DLL dans la `InitInstance` fonction membre et le code d’arrêt dans `ExitInstance` comme dans une application MFC normale.

- Même si le terme USRDLL est obsolète, vous devez toujours définir «**_USRDLL**» sur la ligne de commande du compilateur. Cette définition détermine les déclarations extraites de à partir des fichiers d’en-tête MFC.

les DLL MFC normales doivent avoir une `CWinApp` classe dérivée de et un objet unique de cette classe d’application, comme c’est le cas pour une application MFC. Toutefois, l' `CWinApp` objet de la dll n’a pas de pompe de messages principale, comme l' `CWinApp` objet d’une application.

Notez que le `CWinApp::Run` mécanisme ne s’applique pas à une dll, car l’application possède la pompe de messages principale. Si la DLL ouvre des boîtes de dialogue non modales ou possède sa propre fenêtre frame principale, la pompe de messages principale de l’application doit appeler une routine exportée par la DLL qui, à son tour, appelle la `CWinApp::PreTranslateMessage` fonction membre de l’objet application de la dll.

Pour obtenir un exemple de cette fonction, consultez l’exemple DLLScreenCap.

Les symboles sont généralement exportés à partir d’une DLL MFC normale à l’aide de l’interface C standard. La déclaration d’une fonction exportée à partir d’une DLL MFC normale devrait ressembler à ceci :

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Toutes les allocations de mémoire dans une DLL MFC normale doivent rester dans la DLL. la DLL ne doit pas passer à l’exécutable appelant ou en recevoir de l’un des éléments suivants :

- Pointeurs vers des objets MFC

- Pointeurs vers la mémoire allouée par MFC

Si vous devez effectuer l’une des actions ci-dessus ou si vous devez passer des objets dérivés de MFC entre l’exécutable appelant et la DLL, vous devez générer une DLL d’extension MFC.

Il est possible de transmettre en toute sécurité des pointeurs vers la mémoire allouée par les bibliothèques Runtime C entre une application et une DLL uniquement si vous effectuez une copie des données. Vous ne devez pas supprimer ou redimensionner ces pointeurs, ni les utiliser sans effectuer une copie de la mémoire.

Une DLL liée de manière statique aux MFC ne peut pas également établir de liaison dynamique avec les DLL MFC partagées. Une DLL liée de manière statique aux MFC est liée de manière dynamique à une application comme n’importe quelle autre DLL. les applications sont liées à celles-ci comme n’importe quelle autre DLL.

Les bibliothèques de liens statiques MFC standard sont nommées en fonction de la convention décrite dans [conventions d’affectation de noms pour les DLL MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Toutefois, avec MFC version 3,0 et versions ultérieures, il n’est plus nécessaire de spécifier manuellement à l’éditeur de liens la version de la bibliothèque MFC que vous souhaitez lier. Au lieu de cela, les fichiers d’en-tête MFC déterminent automatiquement la version appropriée de la bibliothèque MFC à lier en fonction des définitions de préprocesseur, telles que **\_ DEBUG** ou **_UNICODE**. Les fichiers d’en-tête MFC ajoutent des directives/DEFAULTLIB qui demandent à l’éditeur de liens de créer un lien dans une version spécifique de la bibliothèque MFC.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Initialiser des DLL MFC normales](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Utilisation de MFC dans le cadre d’une DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [Utilisation de DLL d’extension MFC de base de données, OLE et sockets dans des DLL MFC normales](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Création d’une DLL MFC](../mfc/reference/mfc-dll-wizard.md)

- [DLL MFC normales liées de manière dynamique aux MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [DLL d’extension de MFC](extension-dlls-overview.md)

## <a name="see-also"></a>Voir aussi

[Types de DLL](kinds-of-dlls.md)
