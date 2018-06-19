---
title: DLL d’extension | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- afxdll
dev_langs:
- C++
helpviewer_keywords:
- memory [C++], DLLs
- MFC extension DLLs [C++]
- AFXDLL library
- shared resources [C++]
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- resource sharing [C++]
- extension DLLs [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: f69ac3d4-e474-4b1c-87a1-6738843a135c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f60540735be44adf4305dcda77373faf8a83514
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377129"
---
# <a name="mfc-extension-dlls"></a>DLL d’extension MFC
DLL d’une extension MFC est une DLL qui implémentent généralement des classes réutilisables dérivées les classes existantes de la bibliothèque Microsoft Foundation Class.  
  
 Une DLL d’extension MFC présente les fonctionnalités et les exigences suivantes :  
  
-   L’exécutable client doit être une application MFC compilée avec `_AFXDLL` défini.  
  
-   Une DLL d’extension MFC peut également être utilisé par une DLL régulière MFC qui est lié dynamiquement à MFC.  
  
-   DLL d’extension MFC doivent être compilée avec `_AFXEXT` défini. Cette opération force `_AFXDLL` à être également défini et garantit que l’extraction des déclarations appropriées des fichiers d’en-tête MFC. Cela garantit également que `AFX_EXT_CLASS` est défini comme `__declspec(dllexport)` lors de la génération de la DLL, qui est nécessaire si vous utilisez cette macro pour déclarer les classes dans votre DLL d’extension MFC.  
  
-   DLL d’extension MFC ne doivent pas instancier une classe dérivée de `CWinApp`, mais devez compter sur l’application cliente (ou DLL) pour fournir cet objet.  
  
-   DLL d’extension MFC doivent, cependant, fournir un `DllMain` la fonction et effectuer toute initialisation nécessaire.  
  
 DLL d’extension sont générées à l’aide de la version de la bibliothèque de liens dynamiques des MFC (également appelée la version partagée de MFC). Uniquement exécutables MFC (applications ou des DLL MFC standard) qui sont générés avec la version partagée de MFC peuvent utiliser une DLL d’extension MFC. L’application cliente et la DLL d’extension MFC doivent utiliser la même version de MFCx0.dll. Avec une DLL d’extension MFC, vous pouvez dériver de nouvelles classes personnalisées à partir de MFC et puis offrir cette version étendue des MFC pour les applications qui appellent votre DLL.  
  
 DLL d’extension peuvent également servir pour passer des objets dérivés des MFC entre l’application et la DLL. Les fonctions membres associées à l’objet passé existent dans le module où l’objet a été créé. Étant donné que ces fonctions sont exportées correctement lorsque vous utilisez la version DLL partagée de MFC, vous pouvez passer librement MFC ou des pointeurs d’objet dérivé des MFC entre une application et la chargement de DLL d’extension MFC.  
  
 Une DLL d’extension MFC utilise une version partagée de MFC de la même façon qu’une application utilise la version DLL partagée de MFC, avec quelques remarques supplémentaires :  
  
-   Il n’a pas un `CWinApp`-objet dérivé. Il doit fonctionner avec le `CWinApp`-dérivée de l’objet de l’application cliente. Cela signifie que l’application cliente possède la pompe de messages principale, la boucle inactive et ainsi de suite.  
  
-   Il appelle `AfxInitExtensionModule` dans son `DllMain` (fonction). La valeur de retour de cette fonction doit être vérifiée. Si une valeur zéro est retournée à partir de `AfxInitExtensionModule`, retournent 0 à partir de votre `DllMain` (fonction).  
  
-   Il crée un **CDynLinkLibrary** si l’extension MFC DLL souhaite exporter l’objet lors de l’initialisation `CRuntimeClass` objets ou des ressources à l’application.  
  
 Avant la version 4.0 de MFC, ce type de DLL s’appelait AFXDLL. AFXDLL désigne le `_AFXDLL` symbole de préprocesseur qui est défini lors de la génération de la DLL.  
  
 Les bibliothèques d’importation de la version partagée de MFC sont nommées selon la convention décrite dans [conventions d’affectation de noms pour les DLL MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Visual C++ fournit des versions prégénérées des DLL MFC, plus un nombre de DLL non - MFC que vous pouvez utiliser et distribuer avec vos applications. Ceux-ci sont décrits dans le fichier Redist.txt, qui est installé dans le dossier Program Files\Microsoft Visual Studio.  
  
 Si vous exportez un fichier .def, placez le code suivant au début et à la fin du fichier d’en-tête :  
  
```cpp  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
 Ces quatre lignes vous assurer que votre code est compilé correctement pour une DLL d’extension MFC. Si vous omettez ces quatre lignes risque d’être compilée ou liée de manière incorrecte.  
  
 Si vous devez passer une MFC ou pointeur d’objet dérivé des MFC vers ou à partir d’une DLL MFC, la DLL doit être une DLL d’extension MFC. Les fonctions membres associées à l’objet passé existent dans le module où l’objet a été créé. Étant donné que ces fonctions sont exportées correctement lorsque vous utilisez la version DLL partagée de MFC, vous pouvez passer librement MFC ou des pointeurs d’objet dérivé des MFC entre une application et la chargement de DLL d’extension MFC.  
  
 Compte tenu des problèmes d’altération et l’exportation du C++, la liste d’exportation à partir d’une extension MFC DLL peut-être être différente entre les versions debug et la vente au détail de la même DLL et les DLL pour différentes plateformes. La version commerciale MFCx0.dll a environ 2 000 points d’entrée exportés ; le débogage MFCx0D.dll a environ 3 000 points d’entrée exporté.  
  
## <a name="memory-management"></a>Gestion de la mémoire  
 MFCx0.dll et toutes les DLL chargées dans l’espace d’adressage d’une application cliente d’extension MFC utilisent l’allocateur de mémoire de même, le chargement des ressources et autres États globaux MFC comme s’ils étaient dans la même application. Ceci est important car les bibliothèques DLL non - MFC et DLL régulières MFC faisons exactement le contraire et que chaque DLL affecte en dehors de son propre pool de mémoire.  
  
 Si une DLL d’extension MFC alloue de la mémoire, cette mémoire peut alors être librement mélangée avec tout autre objet alloué par l’application. En outre, si une application liée de manière dynamique aux MFC échoue, la protection du système d’exploitation assure l’intégrité de toute autre application MFC partageant la DLL.  
  
 De même les autres États MFC globaux, tels que le fichier exécutable en cours pour charger les ressources à partir, sont également partagés entre l’application cliente et toutes les DLL d’extension MFC ainsi que MFCx0.dll elle-même.  
  
## <a name="sharing-resources-and-classes"></a>Partage des ressources et des Classes  
 Exportation de ressources s’effectue via une liste de ressources. Chaque application contient une seule liste liée de **CDynLinkLibrary** objets. Lors de la recherche d’une ressource, la plupart des implémentations MFC standard qui chargent des ressources examinent d’abord en le module de ressources en cours (`AfxGetResourceHandle`) et si la ressource est introuvable, parcourent la liste de **CDynLinkLibrary** objets tentative de chargement de la ressource demandée.  
  
 Parcourir la liste comporte les inconvénients qu’il est légèrement plus lente et nécessite la gestion de plages d’ID de ressource. Il a l’avantage qu’une application cliente qui est liée à plusieurs DLL d’extension MFC peut utiliser n’importe quelle ressource fournie par la DLL sans avoir à spécifier le handle d’instance DLL. `AfxFindResourceHandle` est une API utilisée pour parcourir la liste de ressources pour rechercher une correspondance donnée. Il prend le nom et le type d’une ressource et retourne le handle de ressource où elle a été trouvée en premier (ou NULL).  
  
 Si vous ne souhaitez pas parcourir la liste mais seulement charger les ressources à partir d’un emplacement spécifique, utilisez les fonctions `AfxGetResourceHandle` et `AfxSetResourceHandle` pour enregistrer l’ancien handle et définir le nouveau handle. Veillez à restaurer l’ancien handle de ressource avant de retourner à l’application cliente. Pour obtenir un exemple de l’utilisation de cette approche pour charger explicitement un menu, consultez le fichier .cpp Testdll2 dans l’exemple MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk).  
  
 La création dynamique d’objets MFC reçoit un nom MFC est similaire. Le mécanisme de la désérialisation d’objets MFC doit avoir tous les `CRuntimeClass` objets enregistrés afin qu’il puisse reconstruire en créant dynamiquement des objets C++ du type requis en fonction de ce qui a été stocké précédemment.  
  
 Dans le cas de l’exemple MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk), la liste ressemble à ceci :  
  
```  
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE  
               |                      |  
          TESTDLL2.DLL           TESTDLL2.DLL  
               |                      |  
          TESTDLL1.DLL           TESTDLL1.DLL  
               |                      |  
           MFCOxxD.DLL                |  
               |                      |  
           MFCDxxD.DLL                |  
               |                      |  
            MFCxxD.DLL            MFCxx.DLL  
```  
  
 où *xx* est le numéro de version ; par exemple, 42 représente la version 4.2.  
  
 MFCxx.dll occupe généralement la dernière sur la ressource et la liste de classes. MFCxx.dll inclut toutes les ressources MFC standards, y compris les chaînes d’invite pour tous les ID de commande standard. Placer à la fin de la liste permet de DLL et l’application cliente elle-même ne pas avoir leur propre copie des ressources MFC standards, mais s’appuyer sur les ressources partagées dans la MFCxx.dll à la place.  
  
 Fusionner les ressources et les noms de classe de toutes les DLL dans l’espace de noms de l’application cliente a l’inconvénient de devoir être prudent avec les ID ou les noms que vous sélectionnez.  
  
 Le [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk) exemple gère l’espace de noms de ressource partagée à l’aide de plusieurs fichiers d’en-tête.  
  
 Si votre DLL d’extension MFC doit gérer des données supplémentaires pour chaque application, vous pouvez dériver une classe nouvelle à partir de **CDynLinkLibrary** et créez-le dans `DllMain`. Lors de l’exécution, la DLL peut consulter la liste de l’application en cours de **CDynLinkLibrary** objets à rechercher celui de cette DLL d’extension MFC particulière.  
  
### <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Initialiser une DLL d’extension MFC](../build/run-time-library-behavior.md#initializing-extension-dlls)  
  
### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [Conseils sur l’utilisation des fichiers de ressources](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)  
  
-   [Version DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)  
  
-   [DLL MFC normales liées de manière statique aux MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [DLL MFC normales liées dynamiquement à MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Utilisation de DLL d’extension de MFC de type base de données, OLE et sockets dans des DLL MFC normales](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DLL dans Visual C++](../build/dlls-in-visual-cpp.md)