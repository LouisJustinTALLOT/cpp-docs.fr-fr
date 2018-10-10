---
title: Questions fréquentes sur les DLL MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a68a0ae6392c2a9a64c9ff6c567451c2672c861
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890190"
---
# <a name="dll-frequently-asked-questions"></a>Forum Aux Questions à propos des DLL

Suivantes sont certaines questions fréquentes (FAQ) sur les DLL.

- [Une DLL MFC peut créer de plusieurs threads ?](#mfc_multithreaded_1)

- [Une application multithread peut accéder à une DLL MFC dans différents threads ?](#mfc_multithreaded_2)

- [Existe-t-il des classes MFC ou des fonctions qui ne peut pas être utilisées dans une DLL MFC ?](#mfc_prohibited_classes)

- [Quelles techniques d’optimisation dois-je utiliser pour améliorer les performances de l’application cliente lors du chargement ?](#mfc_optimization)

- [Il existe une fuite de mémoire dans ma DLL MFC normale, mais le code semble correct. Comment puis-je trouver la fuite de mémoire ?](#memory_leak)

## <a name="mfc_multithreaded_1"></a> Une DLL MFC peut créer de plusieurs threads ?

Sauf que pendant l’initialisation, une DLL MFC peuvent créer en toute sécurité plusieurs threads tant qu’il utilise le thread Win32 (TLS) de stockage local fonctions telles que **TlsAlloc** pour allouer le stockage local des threads. Toutefois, si une DLL MFC utilise **__declspec (thread)** pour allouer le stockage local des threads, l’application cliente doit être liée implicitement à la DLL. Si l’application cliente liée de manière explicite à la DLL, l’appel à **LoadLibrary** se chargeront pas correctement la DLL. Pour plus d’informations sur les variables locales de thread dans les DLL, consultez [thread](../cpp/thread.md).

Une DLL MFC qui crée un nouveau thread MFC lors du démarrage cesse de répondre lorsqu’il est chargé par une application. Cela inclut chaque fois qu’un thread est créé en appelant `AfxBeginThread` ou `CWinThread::CreateThread` à l’intérieur :

- Le `InitInstance` d’un `CWinApp`-objet dans une DLL MFC normale dérivé.

- Un fourni `DllMain` ou **RawDllMain fournie** dans une DLL MFC normale.

- Un fourni `DllMain` ou **RawDllMain fournie** fonction dans une DLL d’extension MFC.

## <a name="mfc_multithreaded_2"></a> Une application multithread peut accéder à une DLL MFC dans différents threads ?

Les applications multithread peuvent accéder à des DLL MFC normales liées de manière dynamique aux MFC et DLL d’extension MFC à partir de différents threads. Et, à compter de Visual C++ version 4.2, une application peut accéder à des DLL MFC normales liées de manière statique aux MFC à partir de plusieurs threads créés dans l’application.

Avant la version 4.2, un seul thread externe peut attacher à une DLL MFC normale liée de manière statique aux MFC.

Notez que le terme USRDLL n’est plus utilisé dans la documentation de Visual C++. Une DLL MFC normale liée de manière statique aux MFC possède les mêmes caractéristiques que l’ancienne USRDLL.

## <a name="mfc_prohibited_classes"></a> Existe-t-il des classes MFC ou des fonctions qui ne peut pas être utilisées dans une DLL MFC ?

DLL d’extension utilisent les `CWinApp`-classe dérivée de l’application cliente. Elles ne doivent comporter leurs propres `CWinApp`-classe dérivée.

DLL MFC normales doit avoir un `CWinApp`-dérivée de classe et un seul objet de cette classe d’application, comme une application MFC. Contrairement à la `CWinApp` objet d’une application, le `CWinApp` objet de la DLL n’a pas de pompe de messages principale.

Notez que, comme le `CWinApp::Run` mécanisme ne s’applique pas à une DLL, l’application qui possède la pompe de messages principale. Si la DLL pour ouvrir les boîtes de dialogue non modales ou possède une fenêtre frame principale propre, pompe de messages principale de l’application doit appeler une routine exportée par la DLL, qui à son tour appelle la `CWinApp::PreTranslateMessage` fonction membre de l’objet d’application de la DLL.

## <a name="mfc_optimization"></a> Quelles techniques d’optimisation dois-je utiliser pour améliorer l’application cliente&#39;performances s lors du chargement ?

Si votre DLL est une DLL MFC normale liée de manière statique aux MFC, modifiez-le à intervalles réguliers des DLL MFC qui est liée de manière dynamique aux MFC réduit la taille du fichier.

Si la DLL possède un grand nombre de fonctions exportées, utilisez un fichier .def pour exporter les fonctions (au lieu d’utiliser **__declspec (dllexport)**) et utiliser le fichier .def [NONAME (attribut)](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) sur chaque fonction exportée. L’attribut NONAME provoque uniquement la valeur ordinale et pas le nom de fonction à stocker dans la table d’exportation de la DLL, ce qui réduit la taille du fichier.

DLL liées implicitement à une application sont chargés lorsque l’application charge. Pour améliorer les performances lors du chargement, essayez de diviser la DLL dans différentes DLL. Placez toutes les fonctions dont l’application appelante doit immédiatement après le chargement dans une DLL et disposer de l’application appelante implicitement liée à cette DLL. Placez les autres fonctions de l’application appelante n’a pas besoin de tout de suite dans une autre DLL et lier l’application explicitement à cette DLL. Pour plus d’informations, consultez [déterminer la méthode de liaison à utiliser](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).

## <a name="memory_leak"></a> Il&#39;s une fuite de mémoire dans ma DLL MFC normale, mais mon code semble correct. Comment puis-je trouver la fuite de mémoire ?

Une des causes possibles de la fuite de mémoire est que MFC crée des objets temporaires qui sont utilisés à l’intérieur de fonctions gestionnaires de messages. Dans les applications MFC, ces objets temporaires sont automatiquement nettoyés dans la `CWinApp::OnIdle()` fonction appelée entre le traitement des messages. Toutefois, dans les bibliothèques de liens dynamiques MFC (DLL), le `OnIdle()` fonction n’est pas appelée automatiquement. Par conséquent, les objets temporaires ne sont pas automatiquement nettoyés. Pour nettoyer les objets temporaires, la DLL doit appeler explicitement `OnIdle(1)` régulièrement.

## <a name="see-also"></a>Voir aussi

[DLL dans Visual C++](../build/dlls-in-visual-cpp.md)