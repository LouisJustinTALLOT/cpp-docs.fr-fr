---
title: À l’aide de la base de données, OLE et Sockets MFC DLL d’extension dans les DLL MFC normales
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.assetid: 9f1d14a7-9e2a-4760-b3b6-db014fcdb7ff
ms.openlocfilehash: d08822a04abe5a01883ad8aa1bd6d94269e810cc
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "57807973"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>À l’aide de la base de données, OLE et Sockets MFC DLL d’extension dans les DLL MFC normales

Lorsque vous utilisez une extension MFC DLL à partir d’une DLL MFC normale, si l’extension MFC DLL n’est pas relié à la **CDynLinkLibrary** chaîne de l’objet de la DLL MFC normale, vous pouvez rencontrer un ou plusieurs des problèmes connexes. Étant donné que la prise en charge les versions debug des MFC de base de données, OLE et Sockets DLL sont implémentés en tant que DLL d’extension MFC, vous pouvez voir des problèmes similaires si vous utilisez ces MFC fonctionnalités, même si vous n’utilisez pas explicitement l’un de vos propres DLL d’extension MFC. Certains problèmes sont :

- Lorsque essaie de désérialiser un objet d’un type de classe défini dans le MFC DLL d’extension, le message « Avertissement : Impossible de charger CYourClass à partir de l’archive. Classe non définie ». s’affiche dans la fenêtre de débogage TRACE et l’objet ne parvient pas à sérialiser.

- Une exception indiquant la classe incorrecte peut être levée.

- Ressources stockées dans la DLL d’extension MFC ne parviennent pas à charger, car `AfxFindResourceHandle` retourne **NULL** ou un handle de ressource incorrect.

- `DllGetClassObject`, `DllCanUnloadNow`et le `UpdateRegistry`, `Revoke`, `RevokeAll`, et `RegisterAll` fonctions membres de `COleObjectFactory` ne parviennent pas à trouver une fabrique de classe définie dans la DLL d’extension MFC.

- `AfxDoForAllClasses` ne fonctionne pas pour les classes dans la DLL d’extension MFC.

- Base de données MFC standard, les sockets ou les ressources OLE chargement échouent. Par exemple, **AfxLoadString**(**AFX_IDP_SQL_CONNECT_FAIL**) retourne une chaîne vide, même quand la DLL régulière MFC utilise correctement les classes de base de données MFC.

La solution à ces problèmes consiste à créer et exporter une fonction d’initialisation dans le MFC DLL d’extension qui crée un **CDynLinkLibrary** objet. Appelez cette fonction d’initialisation une seule fois à partir de chaque DLL MFC normale qui utilise la DLL d’extension MFC.

## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>MFC OLE, base de données MFC (ou DAO), ou de la prise en charge des Sockets MFC

Si vous utilisez OLE MFC, base de données MFC (ou DAO) ou Sockets MFC prend en charge dans la DLL MFC normale, respectivement, le débogage MFC MFCOxxD.dll de DLL d’extension MFC, MFCDxxD.dll et MFCNxxD.dll (où xx est le numéro de version) sont liés automatiquement. Vous devez appeler une fonction d’initialisation prédéfinie pour chacune de ces DLL que vous utilisez.

Pour la prise en charge de la base de données, ajoutez un appel à `AfxDbInitModule` à de votre MFC DLL régulière `CWinApp::InitInstance` (fonction). Assurez-vous que cet appel se produit avant tout appel de la classe de base ou de tout code qui accède à MFCDxxD.dll ajouté. Cette fonction n’accepte aucun paramètre et retourne void.

Pour la prise en charge OLE, ajoutez un appel à `AfxOleInitModule` à de votre MFC DLL régulière `CWinApp::InitInstance`. Notez que le **COleControlModule InitInstance** appels de fonction `AfxOleInitModule` déjà, par conséquent si vous créez un contrôle OLE et que vous utilisez `COleControlModule`, vous ne devez pas ajouter cet appel à `AfxOleInitModule`.

Pour la prise en charge des Sockets, ajoutez un appel à `AfxNetInitModule` à de votre MFC DLL régulière `CWinApp::InitInstance`.

Notez que les versions release de DLL MFC et applications n’utilisent pas des DLL séparées pour la base de données, sockets, ou la prise en charge OLE. Toutefois, il est déconseillé d’appeler ces fonctions d’initialisation en mode release.

## <a name="cdynlinklibrary-objects"></a>Objets CDynLinkLibrary

Au cours de chacune des opérations mentionnées au début de cette rubrique, MFC doit rechercher pour un objet ou la valeur souhaitée. Par exemple, pendant la désérialisation, MFC doit effectuer une recherche dans toutes les classes de runtime actuellement disponibles pour faire correspondre des objets dans l’archive avec leur classe d’exécution approprié.

Dans le cadre de ces recherches, les MFC analysent toutes les DLL d’extension MFC en cours d’utilisation en parcourant une chaîne de **CDynLinkLibrary** objets. **CDynLinkLibrary** objets attachent automatiquement à une chaîne pendant leur construction et sont créés par chaque DLL d’extension MFC, à son tour, lors de l’initialisation. En outre, chaque module (application ou DLL MFC normale) possède sa propre chaîne de **CDynLinkLibrary** objets.

Pour une extension MFC DLL puisse être raccordée à un **CDynLinkLibrary** chaîne, il doit créer un **CDynLinkLibrary** objet dans le contexte de chaque module qui utilise la DLL d’extension MFC. Par conséquent, si une extension MFC DLL doit être utilisée à partir de la DLL MFC normales, il doit fournir une fonction d’initialisation exportée qui crée un **CDynLinkLibrary** objet. Chaque DLL régulière MFC qui utilise l’extension MFC DLL doit appeler la fonction d’initialisation exportée.

Si une extension MFC DLL ne va être utilisé à partir d’une application MFC (.exe) et jamais à partir d’une DLL MFC normale, il suffit de créer le **CDynLinkLibrary** objet dans de la DLL d’extension MFC `DllMain`. C’est ce que la code de la DLL d’extension de MFC d’Assistant DLL MFC. Lors du chargement d’une DLL d’extension MFC implicitement, `DllMain` charge et s’exécute avant que l’application démarre jamais. N’importe quel **CDynLinkLibrary** créations sont associées à une chaîne par défaut que la DLL MFC réserve pour une application MFC.

Notez qu’il est déconseillé d’avoir plusieurs **CDynLinkLibrary** objets à partir d’une DLL d’extension MFC dans la même chaîne, en particulier si la DLL d’extension MFC vont être dynamiquement déchargée de la mémoire. N’appelez pas la fonction d’initialisation plusieurs fois à partir de n’importe quel un module.

## <a name="sample-code"></a>Exemple de code

Cet exemple de code suppose que la DLL régulière MFC implicitement établit une liaison à la DLL d’extension MFC. Pour cela, vous devez lier à la bibliothèque d’importation (.lib) de la DLL d’extension MFC lors de la génération de la DLL régulière MFC.

Les lignes suivantes doivent figurer dans la source de la DLL d’extension MFC :

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

Veillez à exporter la **InitYourExtDLL** (fonction). Cette opération peut être effectuée à l’aide **__declspec (dllexport)** ou dans le fichier .def de votre DLL comme suit :

```
// YourExtDLL.Def:
LIBRARY      YOUREXTDLL
CODE         PRELOAD MOVEABLE DISCARDABLE
DATA         PRELOAD SINGLE
EXPORTS
    InitYourExtDLL
```

Ajoutez un appel à la `InitInstance` membre de la `CWinApp`-objet dans chaque DLL MFC normale à l’aide de la DLL d’extension MFC dérivé :

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

### <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Initialiser une DLL d’extension MFC](run-time-library-behavior.md#initializing-extension-dlls)

- [Initialiser des DLL MFC normales](run-time-library-behavior.md#initializing-regular-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [DLL d’extension de MFC](extension-dlls.md)

- [DLL MFC normales liées de manière statique à MFC](regular-dlls-statically-linked-to-mfc.md)

- [DLL MFC normales liées de manière dynamique à MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [À l’aide de MFC dans le cadre d’une DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [Version DLL de MFC](../mfc/tn033-dll-version-of-mfc.md)

## <a name="see-also"></a>Voir aussi

[DLL d’extension de MFC](extension-dlls.md)
