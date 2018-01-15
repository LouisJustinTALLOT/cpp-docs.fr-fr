---
title: DLL MFC Forum aux Questions | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 39c3a36f697527c7e133409f49656e4415f86a7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="dll-frequently-asked-questions"></a>Forum Aux Questions à propos des DLL  
  
Suivantes sont certaines questions fréquemment posées (FAQ) sur les DLL.  
    
-   [Une DLL MFC peut créer des plusieurs threads ?](#mfc_multithreaded_1)  

-   [Une application multithread peut accéder à une DLL MFC dans différents threads ?](#mfc_multithreaded_2)  
  
-   [Existe-t-il des classes MFC ou des fonctions qui ne peut pas être utilisées dans une DLL MFC ?](#mfc_prohibited_classes)  
  
-   [Quelles techniques d’optimisation dois-je utiliser pour améliorer les performances de l’application cliente lors du chargement ?](#mfc_optimization)  
  
-   [Il existe une fuite de mémoire dans ma DLL MFC normale, mais code semble correct. Comment puis-je trouver la fuite de mémoire ?](#memory_leak)  

## <a name="mfc_multithreaded_1"></a>Une DLL MFC peut créer des plusieurs threads ?  
  
Sauf pendant l’initialisation, une DLL MFC peut créer de manière sécurisée plusieurs threads tant qu’il utilise le thread Win32, tels que des fonctions de stockage local (TLS) **TlsAlloc** pour allouer le stockage local des threads. Toutefois, si une DLL MFC utilise **__declspec (thread)** pour allouer le stockage local des threads, l’application cliente doit être liée implicitement à la DLL. Si l’application cliente liée de manière explicite à la DLL, l’appel à **LoadLibrary** pas réussi à charger la DLL. Pour plus d’informations sur la création de plusieurs threads dans les DLL MFC, consultez l’article de la Base de connaissances, « PRB : Calling LoadLibrary() à charge une DLL qu’a statique TLS » (Q118816). Pour plus d’informations sur les variables locales de thread dans les DLL, consultez [thread](../cpp/thread.md).
  
 Une DLL MFC qui crée un nouveau thread MFC pendant le démarrage cesse de répondre quand il est chargé par une application. Cela inclut chaque fois qu’un thread est créé en appelant `AfxBeginThread` ou `CWinThread::CreateThread` dans :  
  
-   Le `InitInstance` d’un `CWinApp`-objet dans une DLL MFC standard dérivé.  
  
-   Un fourni `DllMain` ou **RawDllMain fournie** dans une DLL MFC normale.  
  
-   Un fourni `DllMain` ou **RawDllMain fournie** fonction dans une DLL d’extension MFC.  
  
 Pour plus d’informations sur la création de threads pendant l’initialisation, consultez l’article de la Base de connaissances, « PRB : ne peut pas créer un MFC des threads au cours de démarrage de la DLL » (Q142243).  
  
## <a name="mfc_multithreaded_2"></a>Une application multithread peut accéder à une DLL MFC dans différents threads ?
Applications multithread peuvent accéder à des DLL MFC standard qui lient dynamiquement à MFC et DLL d’extension MFC à partir de différents threads. Et, à compter de Visual C++ version 4.2, une application peut accéder à des DLL MFC normales liées de manière statique aux MFC à partir de plusieurs threads créés dans l’application.  
  
 Avant la version 4.2, un seul thread externe peut attacher à une DLL MFC normale liée de manière statique aux MFC. Pour plus d’informations sur les restrictions d’accès aux DLL MFC normales liées de manière statique aux MFC à partir de plusieurs threads (avant Visual C++ version 4.2), consultez l’article de la Base de connaissances, « plusieurs Threads et MFC _USRDLL » (Q122676).  
  
 Notez que le terme USRDLL n’est plus utilisé dans la documentation Visual C++. Une DLL MFC normale liée de manière statique aux MFC possède les mêmes caractéristiques que l’ancienne USRDLL.  


## <a name="mfc_prohibited_classes"></a>Existe-t-il des classes MFC ou des fonctions qui ne peut pas être utilisées dans une DLL MFC ?
DLL d’extension utilisent le `CWinApp`-classe dérivée de l’application cliente. Ils ne doivent pas avoir leur propre `CWinApp`-classe dérivée.  
  
les DLL régulières MFC doit avoir un `CWinApp`-dérivée de classe et un objet unique de cette classe d’application, contrairement à une application MFC. Contrairement à la `CWinApp` objet d’une application, le `CWinApp` objet de la DLL n’a pas de pompe de messages principale.  
  
 Étant donné que le `CWinApp::Run` mécanisme ne s’applique pas à une DLL, l’application qui possède la pompe de messages principale. Si la DLL ouvre des boîtes de dialogue non modales ou possède une fenêtre frame principale propre, pompe de messages principale de l’application doit appeler une routine exportée par la DLL qui appelle à son tour le `CWinApp::PreTranslateMessage` fonction membre de l’objet d’application de la DLL.  

## <a name="mfc_optimization"></a>Quelles techniques d’optimisation dois-je utiliser pour améliorer l’application cliente &#39; performances lors du chargement ?
Si votre DLL est une DLL MFC normale liée de manière statique aux MFC, la modifier à intervalles réguliers DLL MFC qui est liée de manière dynamique aux MFC réduit la taille du fichier.  
  
 Si la DLL possède un grand nombre de fonctions exportées, utilisez un fichier .def pour exporter les fonctions (au lieu d’utiliser **__declspec (dllexport)**) et utiliser le fichier .def [attribut NONAME](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) sur chaque fonction exportée. L’attribut NONAME entraîne uniquement la valeur ordinale et pas le nom de fonction à stocker dans la table d’exportation de DLL, ce qui réduit la taille du fichier.  
  
 DLL liées de manière implicite à une application sont chargées lorsque l’application charge. Pour améliorer les performances lors du chargement, essayez de diviser la DLL dans différentes DLL. Placez toutes les fonctions que l’application appelante doit immédiatement après le chargement dans une DLL et avoir l’application appelante implicitement liée à cette DLL. Placez les fonctions de l’application appelante n’a pas immédiatement besoin dans une autre DLL et liez l’application explicitement à cette DLL. Pour plus d’informations, consultez [déterminer la méthode de liaison à utiliser](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).  

## <a name="memory_leak"></a>Il &#39; s une fuite de mémoire dans ma DLL MFC normale, mais mon code semble fonctionner correctement. Comment puis-je trouver la fuite de mémoire ?  
  
Une des causes possibles de la fuite de mémoire est que MFC crée des objets temporaires qui sont utilisés à l’intérieur de fonctions gestionnaires de messages. Dans les applications MFC, ces objets temporaires sont automatiquement nettoyés dans la `CWinApp::OnIdle()` fonction appelée entre le traitement des messages. Toutefois, dans les bibliothèques de liens dynamiques MFC (DLL), le `OnIdle()` fonction n’est pas appelée automatiquement. Par conséquent, les objets temporaires ne sont pas automatiquement nettoyés. Pour nettoyer les objets temporaires, la DLL doit appeler explicitement `OnIdle(1)` régulièrement.  
  
## <a name="see-also"></a>Voir aussi  
 [DLL dans Visual C++](../build/dlls-in-visual-cpp.md)