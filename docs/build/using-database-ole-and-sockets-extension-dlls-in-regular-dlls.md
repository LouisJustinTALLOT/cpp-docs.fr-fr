---
title: Utilisation de DLL d’extension MFC de base de données, OLE et sockets dans des DLL MFC normales
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
ms.openlocfilehash: d08822a04abe5a01883ad8aa1bd6d94269e810cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314687"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>Utilisation de DLL d’extension MFC de base de données, OLE et sockets dans des DLL MFC normales

Lors de l’utilisation d’une DLL d’extension MFC à partir d’une DLL MFC normale, si la DLL d’extension MFC n’est pas raccordée à la chaîne d’objets **CDynLinkLibrary** de la DLL MFC normale, vous pouvez rencontrer un ou plusieurs problèmes connexes. Étant donné que les versions Debug des dll de base de données, OLE et Sockets MFC prennent en charge les dll d’extension MFC, vous pouvez rencontrer des problèmes similaires si vous utilisez ces fonctionnalités MFC, même si vous n’utilisez pas explicitement vos propres DLL d’extension MFC. Voici quelques symptômes :

- Lors de la tentative de désérialisation d’un objet d’un type de classe défini dans la DLL d’extension MFC, le message «AVERTISSEMENT : impossible de charger CYourClass à partir de l’archive. Classe non définie.» apparaît dans la fenêtre de débogage de TRACE et l’objet ne parvient pas à sérialiser.

- Une exception indiquant une classe incorrecte peut être levée.

- Échec du chargement des ressources stockées dans la DLL d’extension `AfxFindResourceHandle` MFC, car retourne une **valeur null** ou un handle de ressource incorrect.

- `DllGetClassObject`, `DllCanUnloadNow`, et les `UpdateRegistry` `Revoke` `RevokeAll`fonctions membres,, `RegisterAll` et de ne `COleObjectFactory` parviennent pas à localiser une fabrique de classe définie dans la dll d’extension MFC.

- `AfxDoForAllClasses`ne fonctionne pas pour les classes de la DLL d’extension MFC.

- Échec du chargement de la base de données MFC standard, des sockets ou des ressources OLE. Par exemple, **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) retourne une chaîne vide, même lorsque la DLL MFC normale utilise correctement les classes de base de données MFC.

La solution à ces problèmes consiste à créer et exporter une fonction d’initialisation dans la DLL d’extension MFC qui crée un objet **CDynLinkLibrary** . Appelez cette fonction d’initialisation une seule fois à partir de chaque DLL MFC normale qui utilise la DLL d’extension MFC.

## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>Prise en charge des sockets MFC OLE, de base de données MFC (ou DAO) ou MFC

Si vous utilisez une prise en charge des MFC OLE, des bases de données MFC (ou DAO) ou des sockets MFC dans votre DLL MFC normale, respectivement, les dll d’extension MFC Debug MFC MFCOxxD. dll, MFCDxxD. dll et MFCNxxD. dll (où XX est le numéro de version) sont liées automatiquement. Vous devez appeler une fonction d’initialisation prédéfinie pour chacune des dll que vous utilisez.

Pour la prise en charge des bases de `AfxDbInitModule` données, ajoutez un appel à `CWinApp::InitInstance` la fonction de votre DLL MFC normale. Assurez-vous que cet appel se produit avant tout appel de classe de base ou tout code ajouté qui accède à MFCDxxD. dll. Cette fonction n’accepte aucun paramètre et retourne void.

Pour la prise en charge OLE, ajoutez `AfxOleInitModule` un appel à à vos dll `CWinApp::InitInstance`MFC normales. Notez que la fonction **COleControlModule InitInstance** appelle `AfxOleInitModule` déjà. par conséquent, si vous générez un contrôle OLE et `COleControlModule`que vous utilisez, vous ne devez pas `AfxOleInitModule`ajouter cet appel à.

Pour la prise en charge des sockets, `AfxNetInitModule` ajoutez un appel à à vos `CWinApp::InitInstance`DLL MFC normales.

Notez que les versions Release des dll et des applications MFC n’utilisent pas de dll distinctes pour la base de données, les sockets ou la prise en charge OLE. Toutefois, il est possible d’appeler ces fonctions d’initialisation en mode release en toute sécurité.

## <a name="cdynlinklibrary-objects"></a>Objets CDynLinkLibrary

Au cours de chacune des opérations mentionnées au début de cette rubrique, MFC doit rechercher une valeur ou un objet souhaité. Par exemple, pendant la désérialisation, MFC doit effectuer une recherche dans toutes les classes d’exécution actuellement disponibles pour faire correspondre les objets de l’archive avec leur classe d’exécution appropriée.

Dans le cadre de ces recherches, MFC analyse toutes les dll d’extension MFC en cours d’utilisation en parcourant une chaîne d’objets **CDynLinkLibrary** . Les objets **CDynLinkLibrary** s’attachent automatiquement à une chaîne pendant leur construction et sont créés par chaque dll d’extension MFC à son tour pendant l’initialisation. En outre, chaque module (application ou DLL MFC normale) possède sa propre chaîne d’objets **CDynLinkLibrary** .

Pour qu’une DLL d’extension MFC soit connectée à une chaîne **CDynLinkLibrary** , elle doit créer un objet **CDynLinkLibrary** dans le contexte de chaque module qui utilise la dll d’extension MFC. Par conséquent, si une DLL d’extension MFC va être utilisée à partir de DLL MFC normales, elle doit fournir une fonction d’initialisation exportée qui crée un objet **CDynLinkLibrary** . Chaque DLL MFC normale qui utilise la DLL d’extension MFC doit appeler la fonction d’initialisation exportée.

Si une DLL d’extension MFC va uniquement être utilisée à partir d’une application MFC (. exe) et jamais à partir d’une DLL MFC normale, il suffit de créer l’objet **CDynLinkLibrary** dans les dll d' `DllMain`extension MFC. C’est ce que fait le code de la DLL d’extension MFC de l’Assistant DLL MFC. Lors du chargement implicite d’une DLL d' `DllMain` extension MFC, se charge et s’exécute avant le démarrage de l’application. Toutes les créations **CDynLinkLibrary** sont associées à une chaîne par défaut que la DLL MFC réserve pour une application MFC.

Notez qu’il est déconseillé d’avoir plusieurs objets **CDynLinkLibrary** d’une DLL d’extension MFC dans une chaîne, surtout si la dll d’extension MFC sera déchargée dynamiquement de la mémoire. N’appelez pas la fonction d’initialisation plus d’une fois à partir d’un module.

## <a name="sample-code"></a>Exemple de code

Cet exemple de code suppose que la DLL MFC normale est implicitement liée à la DLL d’extension MFC. Pour ce faire, établissez une liaison à la bibliothèque d’importation (. lib) de la DLL d’extension MFC lors de la génération de la DLL MFC normale.

Les lignes suivantes doivent se trouver dans la source de la DLL d’extension MFC :

```
// YourExtDLL.cpp:

// standard MFC extension DLL routines
#include "afxdllx.h"

static AFX_EXTENSION_MODULE NEAR extensionDLL = { NULL, NULL };

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

Veillez à exporter la fonction **InitYourExtDLL** . Cela peut être fait à l’aide de **__declspec (dllexport)** ou dans le fichier. def de votre dll, comme suit :

```
// YourExtDLL.Def:
LIBRARY      YOUREXTDLL
CODE         PRELOAD MOVEABLE DISCARDABLE
DATA         PRELOAD SINGLE
EXPORTS
    InitYourExtDLL
```

Ajoutez un appel au `InitInstance` membre de l' `CWinApp`objet dérivé de dans chaque DLL MFC standard à l’aide de la dll d’extension MFC :

```
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

- [Dll d’extension MFC](extension-dlls.md)

- [DLL MFC normales liées de manière statique aux MFC](regular-dlls-statically-linked-to-mfc.md)

- [DLL MFC normales liées de manière dynamique aux MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Utilisation de MFC dans le cadre d’une DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [Version DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)

## <a name="see-also"></a>Voir aussi

[Dll d’extension MFC](extension-dlls.md)
