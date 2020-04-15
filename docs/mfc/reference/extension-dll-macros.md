---
title: Macros et fonctions pour la gestion des LDL
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: 6945dcc02423516e8d1cee5d8c828c4ed5069bef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365704"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Macros et fonctions pour la gestion des LDL

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Classes d’exportation.|
|[AFX_MANAGE_STATE](#afx_manage_state)|Protéger une fonction exportée dans un DLL.|
|[AfxOleInitModule](#afxoleinitmodule)|Fournit un support OLE à partir d’un DLL MFC régulier qui est dynamiquement lié à MFC.|
|[AfxNetInitModule](#afxnetinitmodule)|Fournit le soutien MFC Sockets à partir d’un DLL MFC régulier qui est dynamiquement lié à MFC.|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|Obtient l’état actuel du drapeau d’état par module.|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|Définit l’état du module avant l’initialisation et/ou pour restaurer l’état du module précédent après le nettoyage.|
|[AfxInitExtensionModule](#afxinitextensionmodule)|Initialise le DLL.|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|définir le drapeau d’état par module, qui affecte le comportement WinSxS de MFC.|
|[AfxTermExtensionModule](#afxtermextensionmodule)|Permet à MFC de nettoyer le DLL d’extension MFC lorsque chaque processus se détache de la DLL.|

## <a name="afx_ext_class"></a><a name="afx_ext_class"></a>AFX_EXT_CLASS

[Les DLL d’extension de MFC](../../build/extension-dlls.md) utilisent les macro-AFX_EXT_CLASS pour exporter des classes ; les exécutables qui lient à l’extension MFC DLL utilisent la macro pour importer des classes.

### <a name="remarks"></a>Notes

Avec la AFX_EXT_CLASS macro, le même fichier d’en-tête(s) utilisé pour construire l’extension MFC DLL peut être utilisé avec les exécutables qui lient à la DLL.

Dans le fichier d’en-tête de votre DLL, ajoutez le mot clé AFX_EXT_CLASS à la déclaration de votre classe comme suit :

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Pour plus d’informations, voir [Exportation et importation en utilisant AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).

### <a name="requirements"></a>Spécifications

**En-tête:** afxv_dll.h

## <a name="afx_manage_state"></a><a name="afx_manage_state"></a>AFX_MANAGE_STATE

Appelez cette macro pour protéger une fonction exportée dans un DLL.

### <a name="syntax"></a>Syntaxe

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>Paramètres

*pModuleState (en)*<br/>
Un pointeur `AFX_MODULE_STATE` vers une structure.

### <a name="remarks"></a>Notes

Lorsque cette macro est invoquée, *pModuleState* est l’état efficace du module pour le reste de la portée de confinement immédiate. En quittant la portée, l’état du module efficace précédent sera automatiquement restauré.
La `AFX_MODULE_STATE` structure contient des données globales pour le module, c’est-à-dire la partie de l’état du module qui est poussé ou sauté.

Par défaut, MFC utilise le handle de ressource d'application principale pour charger le modèle de ressources. Si vous avez une fonction exportée dans un DLL, comme celui qui lance une boîte de dialogue dans le DLL, ce modèle est en fait stocké dans le module DLL. Vous devez changer l’état du module pour que la poignée correcte soit utilisée. Vous pouvez le faire en ajoutant le code suivant au début de la fonction :

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Cela échange l’état actuel du module avec l’état retourné de [AfxGetStaticModuleState](#afxgetstaticmodulestate) jusqu’à la fin de la portée actuelle.

Pour plus d’informations sur les états du module et MFC, voir «Gérer les données d’État des modules MFC» dans [la création de nouveaux documents, Windows, et vues](../creating-new-documents-windows-and-views.md) et note technique [58](../tn058-mfc-module-state-implementation.md).

> [!NOTE]
> Lorsque MFC crée un contexte d’activation pour un assemblage, il `AFX_MANAGE_STATE` utilise [AfxWinInit](application-information-and-management.md#afxwininit) pour créer le contexte et l’activer et le désactiver. Notez `AFX_MANAGE_STATE` également que cela est activé pour les bibliothèques MFC statiques, ainsi que les DLL MFC, afin de permettre au code MFC d’exécuter dans le contexte d’activation approprié sélectionné par l’utilisateur DLL. Pour plus d’informations, voir [Support for Activation Contexts in the MFC Module State](../support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="requirements"></a>Spécifications

**En-tête:** afxstat_.h

## <a name="a-nameafxoleinitmodule-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/>AfxOleInitModule

Pour le support OLE d’un DLL MFC régulier qui est dynamiquement lié à `CWinApp::InitInstance` MFC, appelez cette fonction dans votre fonction régulière MFC DLL pour initialiser le MFC OLE DLL.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>Notes

Le MFC OLE DLL est une extension MFC DLL; Pour qu’une DLL d’extension MFC `CDynLinkLibrary` soit câblée `CDynLinkLibrary` dans une chaîne, elle doit créer un objet dans le contexte de chaque module qui l’utilisera. `AfxOleInitModule`crée `CDynLinkLibrary` l’objet dans le contexte de votre MFC DLL `CDynLinkLibrary` régulier afin qu’il soit câblé dans la chaîne d’objets de la DLL MFC régulière.

Si vous construisez un contrôle `COleControlModule`OLE et `AfxOleInitModule` utilisez `InitInstance` , vous `COleControlModule` `AfxOleInitModule`ne devriez pas appeler parce que la fonction membre pour les appels .

### <a name="requirements"></a>Spécifications

**En-tête**: \<> afxdll_.h

## <a name="afxnetinitmodule"></a><a name="afxnetinitmodule"></a>AfxNetInitModule

Pour le support MFC Sockets d’un DLL MFC régulier qui est dynamiquement lié à MFC, ajoutez un appel à cette fonction dans la fonction de `CWinApp::InitInstance` votre MFC DLL régulière pour initialiser le MFC Sockets DLL.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>Notes

Le MFC Sockets DLL est une extension MFC DLL; Pour qu’une DLL d’extension MFC `CDynLinkLibrary` soit câblée `CDynLinkLibrary` dans une chaîne, elle doit créer un objet dans le contexte de chaque module qui l’utilisera. `AfxNetInitModule`crée `CDynLinkLibrary` l’objet dans le contexte de votre MFC DLL `CDynLinkLibrary` régulier afin qu’il soit câblé dans la chaîne d’objets de la DLL MFC régulière.

### <a name="requirements"></a>Spécifications

**En-tête:** \<afxdll_.h>

## <a name="afxgetambientactctx"></a><a name="afxgetambientactctx"></a>AfxGetAmbientActCtx

Utilisez cette fonction pour obtenir l’état actuel du drapeau d’état par module, qui affecte le comportement WinSxS de MFC.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle du drapeau d’état de module.

### <a name="remarks"></a>Notes

Lorsque le drapeau est défini (qui est par défaut) et qu’un thread entre dans un module MFC (voir [AFX_MANAGE_STATE),](#afx_manage_state)le contexte du module est activé.

Si le drapeau n’est pas défini, le contexte du module n’est pas activé à l’entrée.

Le contexte d’un module est déterminé à partir de son manifeste, généralement intégré dans les ressources du module.

### <a name="requirements"></a>Spécifications

**En-tête:** afxcomctl32.h

## <a name="afxgetstaticmodulestate"></a><a name="afxgetstaticmodulestate"></a>AfxGetStaticModuleState AfxGetStaticModuleState

Appelez cette fonction pour définir l’état du module avant l’initialisation et/ou pour restaurer l’état du module précédent après le nettoyage.

### <a name="syntax"></a>Syntaxe

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `AFX_MODULE_STATE` vers une structure.

### <a name="remarks"></a>Notes

La `AFX_MODULE_STATE` structure contient des données globales pour le module, c’est-à-dire la partie de l’état du module qui est poussé ou sauté.

Par défaut, MFC utilise le handle de ressource d'application principale pour charger le modèle de ressources. Si vous avez une fonction exportée dans un DLL, comme celui qui lance une boîte de dialogue dans le DLL, ce modèle est en fait stocké dans le module DLL. Vous devez changer l’état du module pour que la poignée correcte soit utilisée. Vous pouvez le faire en ajoutant le code suivant au début de la fonction :

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Cela échange l’état actuel du `AfxGetStaticModuleState` module avec l’état retourné jusqu’à la fin de la portée actuelle.

Pour plus d’informations sur les états du module et MFC, voir «Gérer les données d’État des modules MFC» dans [la création de nouveaux documents, Windows, et vues](../creating-new-documents-windows-and-views.md) et note technique [58](../tn058-mfc-module-state-implementation.md).

### <a name="requirements"></a>Spécifications

**En-tête:** afxstat_.h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

Appelez cette fonction dans une extension `DllMain` MFC DLL pour initialiser le DLL.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>Paramètres

*État*<br/>
Une référence à la structure [AFX_EXTENSION_MODULE structure](afx-extension-module-structure.md) qui contiendra l’état du module DLL d’extension MFC après l’initialisation. L’état comprend une copie des objets de classe runtime qui ont été paralés par `DllMain` l’extension MFC DLL dans le cadre de la construction normale d’objets statiques exécutés avant est entré.

*hModule*<br/>
Une poignée du module DLL d’extension MFC.

### <a name="return-value"></a>Valeur de retour

VRAI si l’extension MFC DLL est pararogée avec succès; autrement, FALSE.

### <a name="remarks"></a>Notes

Par exemple :

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;
...
```

`AfxInitExtensionModule`fait une copie du HMODULE du DLL et capture les classes`CRuntimeClass` de temps d’exécution (structures) du DLL ainsi que ses usines d’objets (objets)`COleObjectFactory` pour une utilisation ultérieure lorsque l’objet `CDynLinkLibrary` est créé.
Les DLL d’extension de MFC doivent faire deux choses dans leur `DllMain` fonction :

- Appelez [AfxInitExtensionModule](#afxinitextensionmodule) et vérifiez la valeur de retour.

- Créez `CDynLinkLibrary` un objet si le DLL exporte des objets [CRuntimeClass Structure](cruntimeclass-structure.md) ou dispose de ses propres ressources personnalisées.

Vous pouvez `AfxTermExtensionModule` appeler pour nettoyer l’extension MFC DLL lorsque chaque processus se détache de l’extension MFC DLL (qui se produit `AfxFreeLibrary` lorsque le processus sort, ou lorsque le DLL est déchargé à la suite d’un appel).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdll_.h

## <a name="afxsetambientactctx"></a><a name="afxsetambientactctx"></a>AfxSetAmbientActCtx

Utilisez cette fonction pour définir le drapeau d’état par module, qui affecte le comportement WinSxS de MFC.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>Paramètres

*bSet (en anglais)*<br/>
Nouvelle valeur du drapeau d’état de module.

### <a name="remarks"></a>Notes

Lorsque le drapeau est défini (qui est par défaut) et qu’un thread entre dans un module MFC (voir [AFX_MANAGE_STATE),](#afx_manage_state)le contexte du module est activé.
Si le drapeau n’est pas défini, le contexte du module n’est pas activé à l’entrée.
Le contexte d’un module est déterminé à partir de son manifeste, généralement intégré dans les ressources du module.

### <a name="example"></a>Exemple

```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
}
```

### <a name="requirements"></a>Spécifications

**En-tête:** afxcomctl32.h

## <a name="afxtermextensionmodule"></a><a name="afxtermextensionmodule"></a>AfxTermExtensionModule

Appelez cette fonction pour permettre à MFC de nettoyer la DLL d’extension MFC lorsque chaque processus se détache de la DLL (qui se produit lorsque le processus sort, ou lorsque le DLL est déchargé à la suite d’un `AfxFreeLibrary` appel).

### <a name="syntax"></a>Syntaxe

```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>Paramètres

*État*<br/>
Une référence à la structure [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) qui contient l’état du module DLL d’extension MFC.

*Balle*<br/>
Si TRUE, nettoyez tous les modules DLL d’extension MFC. Sinon, nettoyez uniquement le module DLL actuel.

### <a name="remarks"></a>Notes

`AfxTermExtensionModule`supprimera tout stockage local attaché au module et supprimera toutes les entrées du cache de carte de message. Par exemple :

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;

        new CMyDynLinkLibrary(NVC_MFC_DLLDLL);

    }
    else if (dwReason == DLL_PROCESS_DETACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Terminating!\n");

        // Terminate the library before destructors are called
        AfxTermExtensionModule(NVC_MFC_DLLDLL);
    }
    return 1;   // ok
}
```

Si votre application charge et libère dynamiquement les DLL `AfxTermExtensionModule`d’extension MFC, assurez-vous d’appeler . Étant donné que la plupart des DLL d’extension MFC ne sont `AfxTermExtensionModule` pas chargées dynamiquement (généralement, elles sont liées par l’intermédiaire de leurs bibliothèques d’importation), l’appel à n’est généralement pas nécessaire.

MFC extension DLLs besoin d’appeler [AfxInitExtensionModule](#afxinitextensionmodule) dans leur `DllMain`. Si le DLL exporte des objets [CRuntimeClass](cruntimeclass-structure.md) ou dispose de ses `CDynLinkLibrary` propres `DllMain`ressources personnalisées, vous devez également créer un objet en .

### <a name="requirements"></a>Spécifications

**En-tête:** afxdll_.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[Gestion des données d’état des modules MFC](../managing-the-state-data-of-mfc-modules.md)<br/>
