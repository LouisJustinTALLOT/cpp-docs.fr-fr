---
description: 'En savoir plus sur : dll d’extension MFC'
title: DLL d’extension
ms.date: 05/06/2019
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
ms.openlocfilehash: 6500d8ba3cfcc4311ef993064aa9516f27fa45d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156474"
---
# <a name="mfc-extension-dlls"></a>DLL d’extension de MFC

Une DLL d’extension MFC est une DLL qui implémente généralement des classes réutilisables dérivées des classes de bibliothèque MFC (Microsoft Foundation Class) existantes.

Une DLL d’extension MFC présente les fonctionnalités et les spécifications suivantes :

- L’exécutable client doit être une application MFC compilée avec `_AFXDLL` défini.

- Une DLL d’extension MFC peut également être utilisée par une DLL MFC normale qui est liée de manière dynamique aux MFC.

- Les dll d’extension MFC doivent être compilées avec `_AFXEXT` défini. Cela oblige `_AFXDLL` également à être défini et garantit que les déclarations appropriées sont extraites à partir des fichiers d’en-tête MFC. Elle garantit également que `AFX_EXT_CLASS` est défini comme `__declspec(dllexport)` lors de la génération de la dll, ce qui est nécessaire si vous utilisez cette macro pour déclarer les classes dans votre dll d’extension MFC.

- Les dll d’extension MFC ne doivent pas instancier une classe dérivée de `CWinApp` , mais doivent s’appuyer sur l’application cliente (ou dll) pour fournir cet objet.

- Toutefois, les dll d’extension MFC doivent fournir une `DllMain` fonction et effectuer toutes les initialisations nécessaires.

Les dll d’extension sont créées à l’aide de la version de bibliothèque de liens dynamiques de MFC (également appelée version partagée de MFC). Seuls les exécutables MFC (applications ou DLL MFC régulières) qui sont générés avec la version partagée de MFC peuvent utiliser une DLL d’extension MFC. L’application cliente et la DLL d’extension MFC doivent utiliser la même version de MFCx0.dll. Avec une DLL d’extension MFC, vous pouvez dériver de nouvelles classes personnalisées à partir de MFC, puis proposer cette version étendue de MFC aux applications qui appellent votre DLL.

Les dll d’extension peuvent également être utilisées pour passer des objets dérivés de MFC entre l’application et la DLL. Les fonctions membres associées à l’objet passé existent dans le module dans lequel l’objet a été créé. Étant donné que ces fonctions sont correctement exportées lors de l’utilisation de la version DLL partagée de MFC, vous pouvez passer librement des pointeurs d’objets dérivés de MFC ou MFC entre une application et les dll d’extension MFC qu’elle charge.

Une DLL d’extension MFC utilise une version partagée de MFC de la même façon qu’une application utilise la version DLL partagée de MFC, avec quelques remarques supplémentaires :

- Elle n’a pas d' `CWinApp` objet dérivé de. Il doit fonctionner avec l' `CWinApp` objet dérivé de l’application cliente. Cela signifie que l’application cliente possède la pompe de messages principale, la boucle inactive, et ainsi de suite.

- Elle appelle `AfxInitExtensionModule` dans sa `DllMain` fonction. La valeur de retour de cette fonction doit être vérifiée. Si une valeur zéro est retournée à partir de `AfxInitExtensionModule` , retournez 0 à partir de votre `DllMain` fonction.

- Elle crée un objet **CDynLinkLibrary** pendant l’initialisation si la dll d’extension MFC souhaite exporter `CRuntimeClass` des objets ou des ressources vers l’application.

Avant la version 4,0 de MFC, ce type de DLL s’appelait AFXDLL. AFXDLL fait référence au `_AFXDLL` symbole de préprocesseur défini lors de la génération de la dll.

Les bibliothèques d’importation pour la version partagée de MFC sont nommées en fonction de la convention décrite dans [conventions d’affectation de noms pour les DLL MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Visual Studio fournit des versions prédéfinies des DLL MFC, ainsi qu’un certain nombre de dll non-MFC que vous pouvez utiliser et distribuer avec vos applications. Celles-ci sont documentées dans Redist.txt, qui est installé dans le dossier Program Files\Microsoft Visual Studio.

Si vous exportez à l’aide d’un fichier. def, placez le code suivant au début et à la fin de votre fichier d’en-tête :

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Ces quatre lignes garantissent que votre code est compilé correctement pour une DLL d’extension MFC. Le fait de laisser ces quatre lignes peut entraîner la compilation ou le lien de votre DLL de manière incorrecte.

Si vous devez passer un pointeur d’objet dérivé de MFC ou MFC vers ou à partir d’une DLL MFC, la DLL doit être une DLL d’extension MFC. Les fonctions membres associées à l’objet passé existent dans le module dans lequel l’objet a été créé. Étant donné que ces fonctions sont correctement exportées lors de l’utilisation de la version DLL partagée de MFC, vous pouvez passer librement des pointeurs d’objets dérivés de MFC ou MFC entre une application et les dll d’extension MFC qu’elle charge.

En raison des problèmes d’exportation et de gestion de noms C++, la liste d’exportation à partir d’une DLL d’extension MFC peut être différente entre les versions Debug et version commerciale de la même DLL et des dll pour différentes plateformes. Le MFCx0.dll de vente au détail dispose d’environ 2 000 points d’entrée exportés ; le MFCx0D.dll de débogage a environ 3 000 points d’entrée exportés.

## <a name="memory-management"></a>Gestion de la mémoire

MFCx0.dll et toutes les dll d’extension MFC chargées dans l’espace d’adressage d’une application cliente utilisent le même allocateur de mémoire, le chargement des ressources et d’autres États globaux MFC comme s’ils se trouvaient dans la même application. Cela est important, car les bibliothèques DLL non-MFC et les DLL MFC standard font exactement le contraire et ont chaque DLL allouée à partir de son propre pool de mémoire.

Si une DLL d’extension MFC alloue de la mémoire, cette mémoire peut être mélangée librement avec tout autre objet alloué par l’application. En outre, si une application liée de manière dynamique aux MFC échoue, la protection du système d’exploitation maintient l’intégrité de toute autre application MFC qui partage la DLL.

De même que d’autres États MFC globaux, comme le fichier exécutable actuel à partir duquel charger des ressources, sont également partagés entre l’application cliente et toutes les dll d’extension MFC, ainsi que MFCx0.dll elles-mêmes.

## <a name="sharing-resources-and-classes"></a>Partage des ressources et des classes

L’exportation des ressources s’effectue par le biais d’une liste de ressources. Chaque application contient une liste d’objets **CDynLinkLibrary** liée de façon unique. Lors de la recherche d’une ressource, la plupart des implémentations MFC standard qui chargent les ressources examinent d’abord le module de ressource actuel ( `AfxGetResourceHandle` ) et, si la ressource est introuvable, parcourent la liste des objets **CDynLinkLibrary** qui tentent de charger la ressource demandée.

Le parcours de la liste présente des inconvénients qu’elle est légèrement plus lente et requiert la gestion des plages d’ID de ressource. Il présente l’avantage qu’une application cliente liée à plusieurs DLL d’extension MFC peut utiliser n’importe quelle ressource fournie par la DLL sans devoir spécifier le descripteur d’instance de DLL. `AfxFindResourceHandle` API utilisée pour parcourir la liste des ressources afin de rechercher une correspondance donnée. Elle prend le nom et le type d’une ressource et retourne le descripteur de ressource où elle a été trouvée pour la première fois (ou NULL).

Si vous ne souhaitez pas parcourir la liste et charger uniquement les ressources à partir d’un emplacement spécifique, utilisez les fonctions `AfxGetResourceHandle` et `AfxSetResourceHandle` pour enregistrer l’ancien descripteur et définir le nouveau descripteur. Veillez à restaurer l’ancien handle de ressource avant de revenir à l’application cliente. Pour obtenir un exemple d’utilisation de cette approche pour charger explicitement un menu, consultez Testdll2. cpp dans l’exemple MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk).

La création dynamique d’objets MFC à partir d’un nom MFC est similaire. Le mécanisme de désérialisation des objets MFC doit avoir tous les objets inscrits pour pouvoir être `CRuntimeClass` reconstruit en créant dynamiquement des objets C++ du type requis en fonction de ce qui a été stocké précédemment.

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

où *XX* est le numéro de version ; par exemple, 42 représente la version 4,2.

Le MFCxx.dll est généralement en dernier dans la liste des ressources et des classes. MFCxx.dll inclut toutes les ressources MFC standard, y compris les chaînes de demande pour tous les ID de commande standard. Le fait de le placer à la fin de la liste permet aux dll et à l’application cliente de ne pas avoir leur propre copie des ressources MFC standard, mais de s’appuyer sur les ressources partagées dans le MFCxx.dll à la place.

La fusion des ressources et des noms de classes de toutes les dll dans l’espace de noms de l’application cliente présente l’inconvénient de vous obliger à faire attention aux ID ou noms que vous choisissez.

L’exemple [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk) gère l’espace de noms de ressources partagées à l’aide de plusieurs fichiers d’en-tête.

Si votre DLL d’extension MFC doit gérer des données supplémentaires pour chaque application, vous pouvez dériver une nouvelle classe de **CDynLinkLibrary** et la créer dans `DllMain` . Lors de l’exécution de, la DLL peut vérifier la liste des objets **CDynLinkLibrary** de l’application actuelle pour trouver celle de cette DLL d’extension MFC particulière.

### <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Initialiser une DLL d’extension MFC](run-time-library-behavior.md#initializing-extension-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Conseils sur l’utilisation des fichiers de ressources partagées](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

- [Version DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)

- [DLL MFC normales liées de manière statique à MFC](regular-dlls-statically-linked-to-mfc.md)

- [DLL MFC normales liées de manière dynamique à MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Utilisation de DLL d’extension MFC de base de données, OLE et sockets dans des DLL MFC normales](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)
