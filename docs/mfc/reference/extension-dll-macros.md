---
title: Macros et fonctions pour la gestion de DLL
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: b27f8763b60dc7ce3ee074cad1365e7e1de3a7e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322200"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Macros et fonctions pour la gestion de DLL

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Exporte des classes.|
|[AFX_MANAGE_STATE](#afx_manage_state)|Protéger une fonction exportée dans une DLL.|
|[AfxOleInitModule](#afxoleinitmodule)|Fournit la prise en charge OLE à partir d’une DLL MFC normale liée de manière dynamique aux MFC.|
|[AfxNetInitModule](#afxnetinitmodule)|Fournit la que prise en charge des Sockets MFC à partir d’une DLL MFC normale liée de manière dynamique aux MFC.|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|Obtient l’état actuel de l’indicateur d’état par module.|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|Définit l’état du module avant l’initialisation et/ou pour restaurer l’état du module précédent après nettoyage.|
|[AfxInitExtensionModule](#afxinitextensionmodule)|Initialise la DLL.|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|définir l’indicateur d’état par module, ce qui affecte le comportement de WinSxS de MFC.|
|[AfxTermExtensionModule](#afxtermextensionmodule)|Permet à nettoyer la DLL d’extension MFC lorsque chaque processus se détache de la DLL MFC.|

## <a name="afx_ext_class"></a>  AFX_EXT_CLASS

[DLL d’extension MFC](../../build/extension-dlls.md) utiliser la macro AFX_EXT_CLASS pour exporter des classes ; les exécutables liés à la DLL d’extension MFC utilisent la macro pour importer des classes.

### <a name="remarks"></a>Notes

Avec la macro AFX_EXT_CLASS, les mêmes fichiers d’en-tête utilisés pour générer la DLL d’extension MFC peuvent être utilisés avec les exécutables liés à la DLL.

Dans le fichier d’en-tête pour votre DLL, ajoutez le mot clé AFX_EXT_CLASS à la déclaration de votre classe comme suit :

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Pour plus d’informations, consultez [exportation et importation à l’aide de AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxv_dll.h

## <a name="afx_manage_state"></a>  AFX_MANAGE_STATE

Appelez cette macro pour protéger une fonction exportée dans une DLL.

### <a name="syntax"></a>Syntaxe

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>Paramètres

*pModuleState*<br/>
Un pointeur vers un `AFX_MODULE_STATE` structure.

### <a name="remarks"></a>Notes

Lorsque cette macro est appelée, *pModuleState* est l’état du module effectif pour le reste de l’exécution étendue contenante. En quittant la portée, l’état du module effectif précédent sera automatiquement rétablie.
Le `AFX_MODULE_STATE` structure contient des données globales du module, autrement dit, la partie de l’état du module qui est envoyé ou dépilé.

Par défaut, MFC utilise le handle de ressource d'application principale pour charger le modèle de ressources. Si vous avez une fonction exportée dans une DLL, tel que celui qui lance une boîte de dialogue dans la DLL, ce modèle est en fait stocké dans le module DLL. Vous devez basculer l’état du module pour le handle correct à utiliser. Vous pouvez le faire en ajoutant le code suivant au début de la fonction :

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Cela permute l’état actuel du module avec l’état retourné par [AfxGetStaticModuleState](#afxgetstaticmodulestate) jusqu'à la fin de la portée actuelle.

Pour plus d’informations sur les États du module et MFC, consultez « La gestion de l’état de MFC Modules de données » dans [création de nouveaux Documents, Windows et des vues](../creating-new-documents-windows-and-views.md) et [Technical Note 58](../tn058-mfc-module-state-implementation.md).

> [!NOTE]
>  Lorsque MFC crée un contexte d’activation pour un assembly, il utilise [AfxWinInit](application-information-and-management.md#afxwininit) pour créer le contexte et `AFX_MANAGE_STATE` pour activer et désactiver. Notez également que `AFX_MANAGE_STATE` est activé pour statique bibliothèques MFC, ainsi que les DLL MFC, afin d’autoriser le code MFC à exécuter dans le contexte d’activation approprié sélectionné par la DLL de l’utilisateur. Pour plus d’informations, consultez [prise en charge des contextes d’Activation dans l’état du Module MFC](../support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxstat_.h

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> AfxOleInitModule

Pour la prise en charge OLE à partir d’une DLL MFC normale liée de manière dynamique aux MFC, appelez cette fonction dans votre MFC DLL régulière `CWinApp::InitInstance` fonction pour initialiser la OLE DLL MFC.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>Notes

La MFC OLE DLL est une extension MFC DLL ; pour une DLL d’extension MFC puisse être raccordée à un `CDynLinkLibrary` chaîne, il doit créer un `CDynLinkLibrary` objet dans le contexte de chaque module qui l’utiliserez. `AfxOleInitModule` crée le `CDynLinkLibrary` de l’objet dans le contexte de votre MFC DLL régulière afin qu’il obtient câblé dans le `CDynLinkLibrary` chaîne de la DLL MFC normale de l’objet.

Si vous créez un contrôle OLE et que vous utilisez `COleControlModule`, vous ne devez pas appeler `AfxOleInitModule` , car le `InitInstance` fonction membre pour `COleControlModule` appels `AfxOleInitModule`.

### <a name="requirements"></a>Configuration requise

**En-tête**: \<afxdll_.h >

## <a name="afxnetinitmodule"></a>  AfxNetInitModule

Pour les Sockets de MFC prend en charge à partir d’une DLL MFC normale liée de manière dynamique aux MFC, ajoutez un appel à cette fonction dans votre MFC DLL régulière `CWinApp::InitInstance` fonction pour initialiser la DLL de Sockets de MFC.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>Notes

La DLL de Sockets MFC est une extension MFC DLL ; pour une DLL d’extension MFC puisse être raccordée à un `CDynLinkLibrary` chaîne, il doit créer un `CDynLinkLibrary` objet dans le contexte de chaque module qui l’utiliserez. `AfxNetInitModule` crée le `CDynLinkLibrary` de l’objet dans le contexte de votre MFC DLL régulière afin qu’il obtient câblé dans le `CDynLinkLibrary` chaîne de la DLL MFC normale de l’objet.

### <a name="requirements"></a>Configuration requise

**En-tête :** \<afxdll_.h >

## <a name="afxgetambientactctx"></a> AfxGetAmbientActCtx

Cette fonction permet d’obtenir l’état actuel de l’indicateur d’état par module, ce qui affecte le comportement de WinSxS de MFC.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle module état indicateur.

### <a name="remarks"></a>Notes

Lorsque l’indicateur est défini (qui est la valeur par défaut) et un thread entre dans un module MFC (consultez [AFX_MANAGE_STATE](#afx_manage_state)), le contexte du module est activé.

Si l’indicateur n’est pas défini, le contexte du module n’est pas activé sur ENTRÉE.

Le contexte d’un module est déterminé à partir de son manifeste, généralement incorporé dans les ressources du module.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxcomctl32.h

## <a name="afxgetstaticmodulestate"></a> AfxGetStaticModuleState

Appelez cette fonction pour définir l’état du module avant l’initialisation et/ou pour restaurer l’état du module précédent après nettoyage.

### <a name="syntax"></a>Syntaxe

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un `AFX_MODULE_STATE` structure.

### <a name="remarks"></a>Notes

Le `AFX_MODULE_STATE` structure contient des données globales du module, autrement dit, la partie de l’état du module qui est envoyé ou dépilé.

Par défaut, MFC utilise le handle de ressource d'application principale pour charger le modèle de ressources. Si vous avez une fonction exportée dans une DLL, tel que celui qui lance une boîte de dialogue dans la DLL, ce modèle est en fait stocké dans le module DLL. Vous devez basculer l’état du module pour le handle correct à utiliser. Vous pouvez le faire en ajoutant le code suivant au début de la fonction :

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Cela permute l’état actuel du module avec l’état retourné par `AfxGetStaticModuleState` jusqu'à la fin de la portée actuelle.

Pour plus d’informations sur les États du module et MFC, consultez « La gestion de l’état de MFC Modules de données » dans [création de nouveaux Documents, Windows et des vues](../creating-new-documents-windows-and-views.md) et [Technical Note 58](../tn058-mfc-module-state-implementation.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxstat_.h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

Appelez cette fonction dans une DLL d’extension MFC `DllMain` pour initialiser la DLL.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>Paramètres

*state*<br/>
Une référence à la [AFX_EXTENSION_MODULE, Structure](afx-extension-module-structure.md) structure qui contient l’état du module DLL d’extension MFC après l’initialisation. L’état inclut une copie des classe des objets d’exécution qui ont été initialisés par la DLL d’extension MFC dans le cadre de la construction d’objet statique normale exécutée avant `DllMain` est entré.

*hModule*<br/>
Handle du module DLL d’extension MFC.

### <a name="return-value"></a>Valeur de retour

TRUE si la DLL d’extension MFC est initialisé avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Exemple :

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

`AfxInitExtensionModule` effectue une copie de HMODULE la DLL et capture des classes d’exécution de la DLL (`CRuntimeClass` structures), ainsi que ses fabriques d’objets (`COleObjectFactory` objets) pour une utilisation ultérieurement, lorsque le `CDynLinkLibrary` objet est créé.
Extension MFC DLL devoir faire deux choses dans leur `DllMain` (fonction) :

- Appelez [AfxInitExtensionModule](#afxinitextensionmodule) et vérifiez la valeur de retournée.

- Créer un `CDynLinkLibrary` de l’objet si la DLL exporterez [CRuntimeClass, Structure](cruntimeclass-structure.md) objets ou a ses propres ressources personnalisées.

Vous pouvez appeler `AfxTermExtensionModule` pour nettoyer la DLL d’extension MFC lorsque chaque processus se détache de la DLL d’extension MFC (ce qui se produit lorsque le processus se termine, ou lorsque la DLL est déchargée à la suite d’un `AfxFreeLibrary` appeler).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdll_.h

## <a name="afxsetambientactctx"></a>  AfxSetAmbientActCtx

Utilisez cette fonction pour définir l’indicateur d’état par module, ce qui affecte le comportement de WinSxS de MFC.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>Paramètres

*bSet*<br/>
Nouvelle valeur de l’indicateur d’état de module.

### <a name="remarks"></a>Notes

Lorsque l’indicateur est défini (qui est la valeur par défaut) et un thread entre dans un module MFC (consultez [AFX_MANAGE_STATE](#afx_manage_state)), le contexte du module est activé.
Si l’indicateur n’est pas défini, le contexte du module n’est pas activé sur ENTRÉE.
Le contexte d’un module est déterminé à partir de son manifeste, généralement incorporé dans les ressources du module.

### <a name="example"></a>Exemple

```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
}
```

### <a name="requirements"></a>Configuration requise

**En-tête :** afxcomctl32.h

## <a name="afxtermextensionmodule"></a>  AfxTermExtensionModule

Appelez cette fonction pour permettre à nettoyer la DLL d’extension MFC lorsque chaque processus se détache de la DLL MFC (ce qui se produit lorsque le processus se termine, ou lorsque la DLL est déchargée à la suite d’un `AfxFreeLibrary` appeler).

### <a name="syntax"></a>Syntaxe

```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>Paramètres

*state*<br/>
Une référence à la [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) structure qui contient l’état du module DLL d’extension MFC.

*bAll*<br/>
Si la valeur est TRUE, nettoyer tous les modules DLL d’extension MFC. Sinon, nettoyer uniquement le module DLL en cours.

### <a name="remarks"></a>Notes

`AfxTermExtensionModule` Supprime tout attachée au module de stockage local et supprimer toutes les entrées du cache de mappage de message. Exemple :

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

Si votre application charge et libère dynamiquement les DLL d’extension MFC, veillez à appeler `AfxTermExtensionModule`. Depuis la plupart des DLL ne sont pas chargées dynamiquement d’extension MFC (en règle générale, elles sont liées par le biais de leurs bibliothèques d’importation), l’appel à `AfxTermExtensionModule` n’est généralement pas nécessaire.

Extension MFC DLL doivent appeler [AfxInitExtensionModule](#afxinitextensionmodule) dans leurs `DllMain`. Si l’exportation de la DLL [CRuntimeClass](cruntimeclass-structure.md) objets ou a ses propres ressources personnalisées, vous devez également créer un `CDynLinkLibrary` dans l’objet `DllMain`.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdll_.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[Gestion des données d’état des modules MFC](../managing-the-state-data-of-mfc-modules.md)<br/>
