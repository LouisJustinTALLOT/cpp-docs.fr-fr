---
title: Forum aux questions sur les DLL MFC
ms.date: 05/06/2019
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 9108aaf3fcface847b0391455a2aecd4d45658c4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856948"
---
# <a name="dll-frequently-asked-questions"></a>Forum Aux Questions à propos des DLL

Voici quelques questions fréquemment posées (FAQ) sur les dll.

- [Une DLL MFC peut-elle créer plusieurs threads ?](#mfc_multithreaded_1)

- [Une application multithread peut-elle accéder à une DLL MFC dans des threads différents ?](#mfc_multithreaded_2)

- [Existe-t-il des classes ou des fonctions MFC qui ne peuvent pas être utilisées dans une DLL MFC ?](#mfc_prohibited_classes)

- [Quelles techniques d’optimisation dois-je utiliser pour améliorer les performances de l’application cliente lors du chargement ?](#mfc_optimization)

- [Il y a une fuite de mémoire dans ma DLL MFC normale, mais mon code semble parfait. Comment puis-je trouver la fuite de mémoire ?](#memory_leak)

## <a name="mfc_multithreaded_1"></a>Une DLL MFC peut-elle créer plusieurs threads ?

Sauf pendant l’initialisation, une DLL MFC peut créer en toute sécurité plusieurs threads, à condition qu’elle utilise les fonctions de stockage local des threads (TLS) Win32, telles que **TlsAlloc** , pour allouer le stockage local des threads. Toutefois, si une DLL MFC utilise **__declspec (thread)** pour allouer le stockage local des threads, l’application cliente doit être implicitement liée à la dll. Si l’application cliente est liée explicitement à la DLL, l’appel à **LoadLibrary** ne chargera pas correctement la dll. Pour plus d’informations sur les variables locales de thread dans les dll, consultez [thread](../cpp/thread.md).

Une DLL MFC qui crée un nouveau thread MFC au cours du démarrage ne répond plus lorsqu’elle est chargée par une application. Cela comprend à chaque fois qu’un thread est créé en appelant `AfxBeginThread` ou `CWinThread::CreateThread` dans :

- `InitInstance` d’un objet dérivé de `CWinApp`dans une DLL MFC standard.

- Une fonction `DllMain` ou **RawDllMain** fournie dans une DLL MFC standard.

- Une fonction `DllMain` ou **RawDllMain** fournie dans une DLL d’extension MFC.

## <a name="mfc_multithreaded_2"></a>Une application multithread peut-elle accéder à une DLL MFC dans des threads différents ?

Les applications multithread peuvent accéder aux DLL MFC normales qui sont liées de manière dynamique aux DLL d’extension MFC et MFC à partir de différents threads. Une application peut accéder à des DLL MFC standard qui sont liées de manière statique aux MFC à partir de plusieurs threads créés dans l’application.

## <a name="mfc_prohibited_classes"></a>Existe-t-il des classes ou des fonctions MFC qui ne peuvent pas être utilisées dans une DLL MFC ?

Les dll d’extension utilisent la classe dérivée de `CWinApp`de l’application cliente. Ils ne doivent pas avoir leur propre classe dérivée de `CWinApp`.

Les DLL MFC normales doivent avoir une classe dérivée de `CWinApp`et un seul objet de cette classe d’application, comme c’est le cas pour une application MFC. Contrairement à l’objet `CWinApp` d’une application, l’objet `CWinApp` de la DLL n’a pas de pompe de messages principale.

Notez que, étant donné que le mécanisme de `CWinApp::Run` ne s’applique pas à une DLL, l’application possède la pompe de messages principale. Si la DLL ouvre des boîtes de dialogue non modales ou possède sa propre fenêtre frame principale, la pompe de messages principale de l’application doit appeler une routine exportée par la DLL, qui à son tour appelle la fonction membre `CWinApp::PreTranslateMessage` de l’objet d’application de la DLL.

## <a name="mfc_optimization"></a>Quelles techniques d’optimisation dois-je utiliser pour améliorer les&#39;performances des applications clientes lors du chargement ?

Si votre DLL est une DLL MFC normale liée de manière statique aux MFC, le fait de la remplacer par une DLL MFC normale qui est liée de manière dynamique aux MFC réduit la taille du fichier.

Si la DLL comporte un grand nombre de fonctions exportées, utilisez un fichier. def pour exporter les fonctions (au lieu d’utiliser **__declspec (dllexport)** ) et utilisez l' [attribut NoName](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) du fichier. def sur chaque fonction exportée. L’attribut NONAME entraîne le stockage de la valeur ordinale et non du nom de la fonction dans la table d’exportation de la DLL, ce qui réduit la taille du fichier.

Les dll qui sont implicitement liées à une application sont chargées lors du chargement de l’application. Pour améliorer les performances lors du chargement, essayez de diviser la DLL en différentes dll. Placez toutes les fonctions dont l’application appelante a besoin immédiatement après le chargement dans une DLL et faites en sorte que l’application appelante soit implicitement liée à cette DLL. Placez les autres fonctions dont l’application appelante n’a pas besoin directement dans une autre DLL et faites en sorte que l’application soit explicitement liée à cette DLL. Pour plus d’informations, consultez [lier un exécutable à une dll](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).

## <a name="memory_leak"></a>Il&#39;y a une fuite de mémoire dans ma DLL MFC normale, mais mon code semble parfait. Comment puis-je trouver la fuite de mémoire ?

L’une des causes possibles de la fuite de mémoire est que MFC crée des objets temporaires qui sont utilisés dans les fonctions de gestionnaire de messages. Dans les applications MFC, ces objets temporaires sont automatiquement nettoyés dans la fonction `CWinApp::OnIdle()` qui est appelée entre les messages de traitement. Toutefois, dans les bibliothèques de liens dynamiques (dll) MFC, la fonction `OnIdle()` n’est pas appelée automatiquement. Par conséquent, les objets temporaires ne sont pas automatiquement nettoyés. Pour nettoyer des objets temporaires, la DLL doit appeler explicitement `OnIdle(1)` périodiquement.

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)
