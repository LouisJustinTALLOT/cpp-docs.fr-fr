---
title: Utilisation de DLL d’extension MFC de base de données, OLE et sockets dans des DLL MFC normales
description: Montre comment utiliser les dll d’extension MFC de base de données, OLE et sockets dans des DLL MFC normales.
ms.date: 11/30/2020
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.openlocfilehash: a28e80c4d554a86f45f708e661382ee4a54eca9e
ms.sourcegitcommit: 432c24dde31c400437c4320e8432b1ddb232f844
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440270"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>Utilisation de DLL d’extension MFC de base de données, OLE et sockets dans des DLL MFC normales

Lors de l’utilisation d’une DLL d’extension MFC à partir d’une DLL MFC normale, si la DLL d’extension MFC n’est pas raccordée à la `CDynLinkLibrary` chaîne d’objets de la DLL MFC normale, vous pouvez rencontrer un ou plusieurs problèmes connexes. Étant donné que les versions Debug des dll de base de données, OLE et Sockets MFC prennent en charge les dll d’extension MFC, vous pouvez rencontrer des problèmes similaires si vous utilisez ces fonctionnalités MFC, même si vous n’utilisez pas explicitement vos propres DLL d’extension MFC. Voici quelques symptômes :

- Lors de la tentative de désérialisation d’un objet d’un type de classe défini dans la DLL d’extension MFC, le message «AVERTISSEMENT : impossible de charger CYourClass à partir de l’archive. Classe non définie.» apparaît dans la fenêtre de débogage de TRACE et l’objet ne parvient pas à sérialiser.

- Une exception indiquant une classe incorrecte peut être levée.

- Échec du chargement des ressources stockées dans la DLL d’extension MFC, car `AfxFindResourceHandle` retourne `NULL` ou un handle de ressource incorrect.

- `DllGetClassObject`, `DllCanUnloadNow` , et les `UpdateRegistry` `Revoke` `RevokeAll` fonctions membres,, et `RegisterAll` de `COleObjectFactory` ne parviennent pas à localiser une fabrique de classe définie dans la dll d’extension MFC.

- `AfxDoForAllClasses` ne fonctionne pas pour les classes de la DLL d’extension MFC.

- Échec du chargement de la base de données MFC standard, des sockets ou des ressources OLE. Par exemple, `AfxLoadString(AFX_IDP_SQL_CONNECT_FAIL)` retourne une chaîne vide, même lorsque la DLL MFC normale utilise correctement les classes de base de données MFC.

La solution à ces problèmes consiste à créer et exporter une fonction d’initialisation dans la DLL d’extension MFC qui crée un `CDynLinkLibrary` objet. Appelez cette fonction d’initialisation une seule fois à partir de chaque DLL MFC normale qui utilise la DLL d’extension MFC.

## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>Prise en charge des sockets MFC OLE, de base de données MFC (ou DAO) ou MFC

Si vous utilisez une prise en charge des MFC OLE, des bases de données MFC (ou DAO) ou des sockets MFC dans votre DLL MFC normale, respectivement, les dll d’extension MFC de débogage MFC *`MFCOxxD.dll`* , *`MFCDxxD.dll`* et *`MFCNxxD.dll`* (où *XX* est le numéro de version) sont liées automatiquement. Appelez une fonction d’initialisation prédéfinie pour chacune des dll que vous utilisez :

- Pour la prise en charge des bases de données, ajoutez un appel à `AfxDbInitModule` votre DLL MFC normale dans sa `CWinApp::InitInstance` fonction. Assurez-vous que cet appel se produit avant tout appel de classe de base ou tout code ajouté qui accède à *`MFCDxxD.dll`* . Cette fonction n’accepte aucun paramètre et retourne `void` .

- Pour la prise en charge OLE, ajoutez à `AfxOleInitModule` votre DLL MFC régulière son `CWinApp::InitInstance` fonction. La `COleControlModule::InitInstance` fonction appelle `AfxOleInitModule` déjà. par conséquent, si vous créez un contrôle OLE et utilisez `COleControlModule` , vous ne devez pas ajouter cet appel à `AfxOleInitModule` .

- Pour la prise en charge des sockets, ajoutez un appel à `AfxNetInitModule` à votre DLL MFC normale dans `CWinApp::InitInstance` .

Les versions Release des dll et des applications MFC n’utilisent pas de dll distinctes pour la base de données, les sockets ou la prise en charge OLE. Toutefois, il est possible d’appeler ces fonctions d’initialisation en mode release.

## <a name="cdynlinklibrary-objects"></a>Objets CDynLinkLibrary

Au cours de chaque opération mentionnée au début de cet article, MFC doit rechercher une valeur ou un objet spécifique. Par exemple, pendant la désérialisation, MFC doit effectuer une recherche dans toutes les classes d’exécution actuellement disponibles pour faire correspondre les objets de l’archive avec leur classe d’exécution appropriée.

Dans le cadre de ces recherches, MFC analyse toutes les dll d’extension MFC en cours d’utilisation en parcourant une chaîne d' `CDynLinkLibrary` objets. `CDynLinkLibrary` les objets sont automatiquement attachés à une chaîne pendant leur construction et sont créés par chaque DLL d’extension MFC à son tour pendant l’initialisation. Chaque module (application ou DLL MFC normale) a sa propre chaîne d' `CDynLinkLibrary` objets.

Pour qu’une DLL d’extension MFC soit connectée à une `CDynLinkLibrary` chaîne, elle doit créer un `CDynLinkLibrary` objet dans le contexte de chaque module qui utilise la dll d’extension MFC. Pour utiliser une DLL d’extension MFC dans des DLL MFC normales, la DLL d’extension doit fournir une fonction d’initialisation exportée qui crée un `CDynLinkLibrary` objet. Chaque DLL MFC normale qui utilise la DLL d’extension MFC doit appeler la fonction d’initialisation exportée.

Si vous utilisez uniquement une DLL d’extension MFC à partir d’une application MFC et jamais à partir d’une DLL MFC normale, il suffit de créer l' `CDynLinkLibrary` objet dans la fonction DLL d’extension MFC `DllMain` . C’est ce que fait le code de la DLL d’extension MFC de l’Assistant DLL MFC. Lors du chargement implicite d’une DLL d’extension MFC, se `DllMain` charge et s’exécute avant le démarrage de l’application. Toutes les `CDynLinkLibrary` créations sont raccordées à une chaîne par défaut que la DLL MFC réserve pour une application MFC.

Il est déconseillé d’avoir plusieurs `CDynLinkLibrary` objets d’une DLL d’extension MFC dans une seule chaîne. Cela est particulièrement vrai si la DLL d’extension MFC peut être déchargée dynamiquement de la mémoire. N’appelez pas la fonction d’initialisation plus d’une fois à partir d’un module.

## <a name="sample-code"></a>Exemple de code

Cet exemple de code suppose que la DLL MFC normale est implicitement liée à la DLL d’extension MFC. Pour créer un lien implicitement, liez-le à la bibliothèque d’importation (fichier LIB) de la DLL d’extension MFC lorsque vous générez la DLL MFC normale.

Les lignes suivantes doivent se trouver dans la source de la DLL d’extension MFC :

```cpp
// YourExtDLL.cpp:

// standard MFC extension DLL routines
#include "afxdllx.h"

static AFX_EXTENSION_MODULE extensionDLL;

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    if (dwReason == DLL_PROCESS_ATTACH)
    {
        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(extensionDLL, hInstance))
           return 0;
    }
    return 1;   // ok
}

// Exported DLL initialization is run in context of
// application or regular MFC DLL
extern "C" void WINAPI InitYourExtDLL()
{
    // create a new CDynLinkLibrary for this app
    new CDynLinkLibrary(extensionDLL);

    // add other initialization here
}
```

Veillez à exporter la fonction **InitYourExtDLL** . Vous pouvez utiliser **`__declspec(dllexport)`** ou l’exporter dans le fichier def pour votre dll, comme illustré ici :

```def
// YourExtDLL.Def:
LIBRARY      YOUREXTDLL
CODE         PRELOAD MOVEABLE DISCARDABLE
DATA         PRELOAD SINGLE
EXPORTS
    InitYourExtDLL
```

Ajoutez un appel au `InitInstance` membre de l' `CWinApp` objet dérivé de dans chaque DLL MFC standard à l’aide de la dll d’extension MFC :

```cpp
// YourRegularDLL.cpp:

class CYourRegularDLL : public CWinApp
{
public:
    virtual BOOL InitInstance(); // Initialization
    virtual int ExitInstance();  // Termination

    // nothing special for the constructor
    CYourRegularDLL(LPCTSTR pszAppName) : CWinApp(pszAppName) { }
};

BOOL CYourRegularDLL::InitInstance()
{
    // any DLL initialization goes here
    TRACE0("YOUR regular MFC DLL initializing\n");

    // wire any MFC extension DLLs into CDynLinkLibrary chain
    InitYourExtDLL();

    return TRUE;
}
```

### <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Initialiser une DLL d’extension MFC](run-time-library-behavior.md#initializing-extension-dlls)

- [Initialiser des DLL MFC normales](run-time-library-behavior.md#initializing-regular-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [DLL d’extension de MFC](extension-dlls.md)

- [DLL MFC normales liées de manière statique aux MFC](regular-dlls-statically-linked-to-mfc.md)

- [DLL MFC normales liées de manière dynamique aux MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Utilisation de MFC dans le cadre d’une DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [Version DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)

## <a name="see-also"></a>Voir aussi

[DLL d’extension de MFC](extension-dlls.md)
