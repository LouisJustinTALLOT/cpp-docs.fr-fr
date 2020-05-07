---
title: Forum aux questions sur les DLL MFC
ms.date: 05/06/2019
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 9108aaf3fcface847b0391455a2aecd4d45658c4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417347"
---
# <a name="dll-frequently-asked-questions"></a>Forum Aux Questions à propos des DLL

Voici quelques questions fréquemment posées (FAQ) sur les dll.

- [Une DLL MFC peut-elle créer plusieurs threads ?](#mfc_multithreaded_1)

- [Une application multithread peut-elle accéder à une DLL MFC dans différents threads ?](#mfc_multithreaded_2)

- [Existe-t-il des classes ou des fonctions MFC qui ne peuvent pas être utilisées dans une DLL MFC ?](#mfc_prohibited_classes)

- [Quelles techniques d'optimisation dois-je utiliser pour améliorer les performances de l'application cliente lors du chargement ?](#mfc_optimization)

- [Il y a une fuite de mémoire dans ma DLL MFC normale, mais mon code semble parfait. Comment puis-je trouver la fuite de mémoire ?](#memory_leak)

## <a name="can-an-mfc-dll-create-multiple-threads"></a><a name="mfc_multithreaded_1"></a>Une DLL MFC peut-elle créer plusieurs threads ?

Sauf pendant l’initialisation, une DLL MFC peut créer en toute sécurité plusieurs threads, à condition qu’elle utilise les fonctions de stockage local des threads (TLS) Win32, telles que **TlsAlloc** , pour allouer le stockage local des threads. Toutefois, si une DLL MFC utilise **__declspec (thread)** pour allouer le stockage local des threads, l’application cliente doit être implicitement liée à la dll. Si l’application cliente est liée explicitement à la DLL, l’appel à **LoadLibrary** ne chargera pas correctement la dll. Pour plus d’informations sur les variables locales de thread dans les dll, consultez [thread](../cpp/thread.md).

Une DLL MFC qui crée un nouveau thread MFC au cours du démarrage ne répond plus lorsqu’elle est chargée par une application. Cela comprend chaque fois qu’un thread est créé `AfxBeginThread` en `CWinThread::CreateThread` appelant ou à l’intérieur de :

- `InitInstance` D’un `CWinApp`objet dérivé de dans une DLL MFC normale.

- Fonction fournie `DllMain` ou **RAWDLLMAIN** dans une DLL MFC standard.

- Fonction fournie `DllMain` ou **RAWDLLMAIN** dans une DLL d’extension MFC.

## <a name="can-a-multithreaded-application-access-an-mfc-dll-in-different-threads"></a><a name="mfc_multithreaded_2"></a>Une application multithread peut-elle accéder à une DLL MFC dans des threads différents ?

Les applications multithread peuvent accéder aux DLL MFC normales qui sont liées de manière dynamique aux DLL d’extension MFC et MFC à partir de différents threads. Une application peut accéder à des DLL MFC standard qui sont liées de manière statique aux MFC à partir de plusieurs threads créés dans l’application.

## <a name="are-there-any-mfc-classes-or-functions-that-cannot-be-used-in-an-mfc-dll"></a><a name="mfc_prohibited_classes"></a>Existe-t-il des classes ou des fonctions MFC qui ne peuvent pas être utilisées dans une DLL MFC ?

Les dll d’extension `CWinApp`utilisent la classe dérivée de l’application cliente. Ils ne doivent pas avoir leur `CWinApp`propre classe dérivée de.

Les DLL MFC normales doivent avoir `CWinApp`une classe dérivée de et un objet unique de cette classe d’application, comme c’est le cas pour une application MFC. Contrairement à `CWinApp` l’objet d’une application, `CWinApp` l’objet de la dll n’a pas de pompe de messages principale.

Notez que dans la `CWinApp::Run` mesure où le mécanisme ne s’applique pas à une dll, l’application possède la pompe de messages principale. Si la DLL ouvre des boîtes de dialogue non modales ou possède sa propre fenêtre frame principale, la pompe de messages principale de l’application doit appeler une routine exportée par la DLL, `CWinApp::PreTranslateMessage` qui à son tour appelle la fonction membre de l’objet d’application de la dll.

## <a name="what-optimization-techniques-should-i-use-to-improve-the-client-application39s-performance-when-loading"></a><a name="mfc_optimization"></a>Quelles techniques d’optimisation dois-je utiliser pour améliorer les performances de l’application cliente&#39;s lors du chargement ?

Si votre DLL est une DLL MFC normale liée de manière statique aux MFC, le fait de la remplacer par une DLL MFC normale qui est liée de manière dynamique aux MFC réduit la taille du fichier.

Si la DLL comporte un grand nombre de fonctions exportées, utilisez un fichier. def pour exporter les fonctions (au lieu d’utiliser **__declspec (dllexport)**) et utilisez l' [attribut NoName](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) du fichier. def sur chaque fonction exportée. L’attribut NONAME entraîne le stockage de la valeur ordinale et non du nom de la fonction dans la table d’exportation de la DLL, ce qui réduit la taille du fichier.

Les dll qui sont implicitement liées à une application sont chargées lors du chargement de l’application. Pour améliorer les performances lors du chargement, essayez de diviser la DLL en différentes dll. Placez toutes les fonctions dont l’application appelante a besoin immédiatement après le chargement dans une DLL et faites en sorte que l’application appelante soit implicitement liée à cette DLL. Placez les autres fonctions dont l’application appelante n’a pas besoin directement dans une autre DLL et faites en sorte que l’application soit explicitement liée à cette DLL. Pour plus d’informations, consultez [lier un exécutable à une dll](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).

## <a name="there39s-a-memory-leak-in-my-regular-mfc-dll-but-my-code-looks-fine-how-can-i-find-the-memory-leak"></a><a name="memory_leak"></a>Il y a&#39;une fuite de mémoire dans ma DLL MFC normale, mais mon code semble parfait. Comment puis-je trouver la fuite de mémoire ?

L’une des causes possibles de la fuite de mémoire est que MFC crée des objets temporaires qui sont utilisés dans les fonctions de gestionnaire de messages. Dans les applications MFC, ces objets temporaires sont automatiquement nettoyés dans `CWinApp::OnIdle()` la fonction qui est appelée entre le traitement des messages. Toutefois, dans les bibliothèques de liens dynamiques (dll) MFC, `OnIdle()` la fonction n’est pas appelée automatiquement. Par conséquent, les objets temporaires ne sont pas automatiquement nettoyés. Pour nettoyer des objets temporaires, la DLL doit explicitement appeler `OnIdle(1)` périodiquement.

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)
