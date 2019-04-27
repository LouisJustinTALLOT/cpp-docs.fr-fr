---
title: DLL d’extension
ms.date: 11/04/2016
f1_keywords:
- afxdll
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
ms.openlocfilehash: eca33b60b8fa6ba812bf5fa68520f51ceb1d164b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195658"
---
# <a name="mfc-extension-dlls"></a>DLL d’extension MFC

Une extension MFC DLL est une DLL qui implémente généralement des classes réutilisables dérivées de classes Microsoft Foundation Class Library existantes.

Une DLL d’extension MFC présente les fonctionnalités et les exigences suivantes :

- L’exécutable client doit être une application MFC compilée avec `_AFXDLL` défini.

- Une DLL d’extension MFC peut également être utilisé par une DLL MFC normale liée de manière dynamique aux MFC.

- DLL d’extension MFC doivent être compilé avec `_AFXEXT` défini. Cela force `_AFXDLL` à être également défini et garantit que les déclarations appropriées sont extraites les fichiers d’en-tête MFC. Cela garantit également que `AFX_EXT_CLASS` est défini comme `__declspec(dllexport)` lors de la génération de la DLL, qui est nécessaire si vous utilisez cette macro pour déclarer les classes dans votre DLL d’extension MFC.

- DLL d’extension MFC ne doivent pas instancier une classe dérivée de `CWinApp`, mais doivent dépendre de l’application cliente (ou DLL) pour fournir cet objet.

- DLL d’extension MFC doivent, cependant, fournir un `DllMain` de fonction et effectuer toute initialisation nécessaire.

DLL d’extension sont générées à l’aide de la version de la bibliothèque de liens dynamiques de la bibliothèque MFC (également connu sous la version partagée des MFC). Uniquement exécutables MFC (applications ou des DLL MFC normales) qui sont générés avec la version partagée des MFC peuvent utiliser une DLL d’extension MFC. L’application cliente et la DLL d’extension MFC doivent utiliser la même version de MFCx0.dll. Avec une DLL d’extension MFC, vous pouvez dériver de nouvelles classes personnalisées de MFC et offrir cette version étendue de la bibliothèque MFC aux applications qui appellent votre DLL.

DLL d’extension peuvent également être utilisés pour passer des objets dérivés des MFC entre l’application et la DLL. Les fonctions membres associées à l’objet passé existent dans le module où l’objet a été créé. Étant donné que ces fonctions sont exportées correctement lorsque vous utilisez la version DLL partagée de MFC, vous pouvez passer librement MFC ou pointeurs d’objet dérivés des MFC entre une application et il charge des DLL d’extension MFC.

Une DLL d’extension MFC utilise une version partagée des MFC de la même façon qu’une application utilise la version DLL partagée de MFC, avec quelques remarques supplémentaires :

- Il n’a pas un `CWinApp`-objet dérivé. Il doit fonctionner avec le `CWinApp`-objet de l’application cliente dérivé. Cela signifie que l’application cliente possède la pompe de messages principale, la boucle inactive et ainsi de suite.

- Il appelle `AfxInitExtensionModule` dans son `DllMain` (fonction). La valeur de retour de cette fonction doit être vérifiée. Si une valeur zéro est retournée à partir de `AfxInitExtensionModule`, retournent 0 à partir de votre `DllMain` (fonction).

- Il crée un **CDynLinkLibrary** pendant l’initialisation d’objet si l’extension MFC DLL souhaite exporter `CRuntimeClass` objets ou des ressources à l’application.

Avant la version 4.0 de MFC, ce type de DLL a été appelé AFXDLL. AFXDLL désigne le `_AFXDLL` symbole de préprocesseur qui est défini lors de la génération de la DLL.

Les bibliothèques d’importation pour la version partagée des MFC sont nommées selon la convention décrite dans [conventions de nommage pour les DLL MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Visual C++ fournit des versions prégénérées des DLL MFC, plus un nombre de DLL non - MFC que vous pouvez utiliser et distribuer avec vos applications. Ces résultats sont décrits dans le fichier Redist.txt, qui est installé dans le dossier Program Files\Microsoft Visual Studio.

Si vous exportez à l’aide d’un fichier .def, placez le code suivant au début et à la fin du fichier d’en-tête :

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Ces quatre lignes garantissent que votre code est compilé correctement pour une DLL d’extension MFC. Si vous omettez ces quatre lignes risque d’être compilée ou liée de manière incorrecte.

Si vous devez transmettre une MFC ou le pointeur d’objet dérivé de MFC vers ou à partir d’une DLL MFC, la DLL doit être une DLL d’extension MFC. Les fonctions membres associées à l’objet passé existent dans le module où l’objet a été créé. Étant donné que ces fonctions sont exportées correctement lorsque vous utilisez la version DLL partagée de MFC, vous pouvez passer librement MFC ou pointeurs d’objet dérivés des MFC entre une application et il charge des DLL d’extension MFC.

Compte tenu des problèmes d’altération et exportation du C++, la liste d’exportation à partir d’une extension MFC DLL peut-être être différente entre les versions de débogage et de la vente au détail de la même DLL et les DLL pour différentes plateformes. La vente au détail MFCx0.dll a environ 2 000 points d’entrée exportés ; le débogage MFCx0D.dll a environ 3 000 points d’entrée exporté.

## <a name="memory-management"></a>Gestion de la mémoire

MFCx0.dll et toutes les DLL chargées dans l’espace d’adressage d’une application cliente d’extension MFC utilisent l’allocateur de mémoire de même, le chargement des ressources et autres États globaux MFC comme s’ils étaient dans la même application. C’est important, car les bibliothèques de DLL non - MFC et DLL régulières MFC l’inverse exact et que chaque DLL affecte en dehors de son propre pool de mémoire.

Si une DLL d’extension MFC alloue de la mémoire, cette mémoire peut alors être librement mélangée avec tout autre objet alloué par l’application. En outre, si une application liée de manière dynamique aux MFC échoue, la protection du système d’exploitation maintient l’intégrité de toute autre application MFC partageant la DLL.

De même les autres États MFC globaux, tels que le fichier exécutable en cours pour charger les ressources à partir, sont également partagés entre l’application cliente et toutes les DLL d’extension MFC ainsi que MFCx0.dll elle-même.

## <a name="sharing-resources-and-classes"></a>Partage des ressources et des Classes

Exportation de ressources s’effectue via une liste de ressources. Chaque application contienne une seule liste liée de **CDynLinkLibrary** objets. Lorsque vous recherchez une ressource, la plupart des implémentations MFC standard qui chargent des ressources commencez par consulter le module de ressources en cours (`AfxGetResourceHandle`) et si la ressource est introuvable, parcourent la liste de **CDynLinkLibrary** objets tentative de chargement de la ressource demandée.

Parcours de la liste a les inconvénients qu’il est légèrement plus lente et nécessite la gestion de plages d’ID de ressource. Il a l’avantage qu’une application cliente qui lie à plusieurs DLL d’extension MFC pouvez utiliser n’importe quelle ressource DLL fournie sans avoir à spécifier le handle d’instance DLL. `AfxFindResourceHandle` une API utilisée pour parcourir la liste des ressources pour rechercher une correspondance donnée. Il prend le nom et le type d’une ressource et retourne le handle de ressource où il a été trouvée en premier (ou NULL).

Si vous ne souhaitez pas parcourir la liste mais seulement charger les ressources à partir d’un emplacement spécifique, utilisez les fonctions `AfxGetResourceHandle` et `AfxSetResourceHandle` pour enregistrer l’ancien handle et définir le nouveau handle. Veillez à restaurer l’ancien handle de ressource avant de retourner à l’application cliente. Pour obtenir un exemple d’utilisation de cette approche pour charger explicitement un menu, consultez le fichier .cpp Testdll2 dans l’exemple MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk).

La création dynamique d’objets MFC reçoit un nom MFC est similaire. Le mécanisme de la désérialisation d’objets MFC doit avoir tous les `CRuntimeClass` objets enregistrés afin qu’il puisse reconstruire en créant dynamiquement des objets C++ du type requis en fonction de ce qui était stocké précédemment.

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

MFCxx.dll est généralement la dernière sur la ressource et la liste de classe. MFCxx.dll inclut toutes les ressources MFC standards, y compris les chaînes d’invite pour tous les ID de commande standard. En le plaçant à la fin de la liste permet la DLL et l’application cliente lui-même ne pas avoir leur propre copie des ressources MFC standards, mais s’appuyer sur les ressources partagées dans la MFCxx.dll à la place.

Fusionner les ressources et les noms de classes de toutes les DLL dans l’espace de noms de l’application cliente a l’inconvénient de vous obliger à être prudent avec les ID ou les noms que vous sélectionnez.

Le [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk) exemple gère l’espace de noms de ressource partagée à l’aide de plusieurs fichiers d’en-tête.

Si votre DLL d’extension MFC doit gérer des données supplémentaires pour chaque application, vous pouvez dériver une nouvelle classe à partir de **CDynLinkLibrary** et créez-le dans `DllMain`. Lors de l’exécution, la DLL peut consulter la liste de l’application en cours de **CDynLinkLibrary** objets pour trouver celui pour cette DLL d’extension MFC particulier.

### <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Initialiser une DLL d’extension MFC](run-time-library-behavior.md#initializing-extension-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Conseils sur l’utilisation de fichiers de ressources partagées](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

- [Version DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)

- [DLL MFC normales liées de manière statique aux MFC](regular-dlls-statically-linked-to-mfc.md)

- [DLL MFC normales liées de manière dynamique aux MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Utilisation de DLL d’extension de MFC de type base de données, OLE et sockets dans des DLL MFC normales](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

## <a name="see-also"></a>Voir aussi

[DLL dans Visual C++](dlls-in-visual-cpp.md)
