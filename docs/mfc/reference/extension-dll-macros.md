---
title: Macros et fonctions pour la gestion des dll
description: Guide de référence sur les macros et les fonctions MFC pour la gestion des dll.
ms.date: 11/30/2020
helpviewer_keywords:
- module macros in MFC
ms.openlocfilehash: b70c4506d49f656e1570f2500cfaa39c28053291
ms.sourcegitcommit: 432c24dde31c400437c4320e8432b1ddb232f844
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440324"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Macros et fonctions pour la gestion des dll

| Nom | Description |
|--|--|
| [`AFX_EXT_CLASS`](#afx_ext_class)] | Exporte les classes. |
| [`AFX_MANAGE_STATE`](#afx_manage_state) | Protégez une fonction exportée dans une DLL. |
| [`AfxOleInitModule`](#afxoleinitmodule) | Fournit la prise en charge OLE d’une DLL MFC normale qui est liée de manière dynamique aux MFC. |
| [`AfxNetInitModule`](#afxnetinitmodule) | Fournit la prise en charge des sockets MFC à partir d’une DLL MFC normale liée de manière dynamique aux MFC. |
| [`AfxGetAmbientActCtx`](#afxgetambientactctx) | Obtient l’état actuel de l’indicateur d’État par module. |
| [`AfxGetStaticModuleState`](#afxgetstaticmodulestate) | Définit l’état du module avant l’initialisation et restaure l’état du module précédent après le nettoyage. |
| [`AfxInitExtensionModule`](#afxinitextensionmodule) | Initialise la DLL. |
| [`AfxSetAmbientActCtx`](#afxsetambientactctx) | Définissez l’indicateur d’État par module, ce qui affecte le comportement WinSxS de MFC. |
| [`AfxTermExtensionModule`](#afxtermextensionmodule) | Permet à MFC de nettoyer la DLL d’extension MFC lorsque chaque processus se détache de la DLL. |

## <a name="afx_ext_class"></a><a name="afx_ext_class"></a> `AFX_EXT_CLASS`

Les [dll d’extension MFC](../../build/extension-dlls.md) utilisent la macro `AFX_EXT_CLASS` pour exporter des classes ; les exécutables qui sont liés à la dll d’extension MFC utilisent la macro pour importer des classes.

### <a name="remarks"></a>Remarques

Avec la `AFX_EXT_CLASS` macro, le ou les fichiers d’en-tête utilisés pour générer la dll d’extension MFC peuvent être utilisés avec les exécutables qui sont liés à la dll.

Dans le fichier d’en-tête de votre DLL, ajoutez le `AFX_EXT_CLASS` mot clé à la déclaration de votre classe comme suit :

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Pour plus d’informations, consultez [exporter et importer `AFX_EXT_CLASS` à l’aide ](../../build/exporting-and-importing-using-afx-ext-class.md)de.

### <a name="requirements"></a>Spécifications

**En-tête :**\<afxv_dll.h>

## <a name="afx_manage_state"></a><a name="afx_manage_state"></a> `AFX_MANAGE_STATE`

Appelez cette macro pour protéger une fonction exportée dans une DLL.

### <a name="syntax"></a>Syntaxe

```cpp
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>Paramètres

*`pModuleState`*<br/>
Pointeur vers une `AFX_MODULE_STATE` structure.

### <a name="remarks"></a>Remarques

Lorsque cette macro est appelée, *`pModuleState`* est l’état du module effectif pour le reste de l’étendue contenante immédiate. Lors de la sortie de l’étendue, l’état du module effectif précédent sera automatiquement restauré.

La `AFX_MODULE_STATE` structure contient des données globales pour le module, autrement dit, la partie de l’état du module qui fait l’objet d’un push ou d’un dépilé.

Par défaut, MFC utilise le handle de ressource d'application principale pour charger le modèle de ressources. Si vous disposez d’une fonction exportée dans une DLL, telle que celle qui lance une boîte de dialogue dans la DLL, le modèle de ressource est stocké dans le module DLL. Veillez à faire basculer l’état du module pour le handle approprié à utiliser. Vous pouvez basculer l’État en ajoutant le code suivant au début de la fonction :

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Cette macro permute l’état du module en cours avec l’état retourné depuis [`AfxGetStaticModuleState`](#afxgetstaticmodulestate) jusqu’à la fin de la portée actuelle.

Pour plus d’informations sur les États des modules et les MFC, consultez [gestion des données d’état des modules MFC](../managing-the-state-data-of-mfc-modules.md) et [note technique 58](../tn058-mfc-module-state-implementation.md).

> [!NOTE]
> Lorsque MFC crée un contexte d’activation pour un assembly, il utilise [`AfxWinInit`](application-information-and-management.md#afxwininit) pour créer le contexte et l' `AFX_MANAGE_STATE` activer et le désactiver. Notez également que `AFX_MANAGE_STATE` est activé pour les bibliothèques MFC statiques, ainsi que les DLL MFC, afin d’autoriser le code MFC à s’exécuter dans le contexte d’activation approprié sélectionné par la dll utilisateur. Pour plus d’informations, consultez [prise en charge des contextes d’activation dans l’état du module MFC](../support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="requirements"></a>Spécifications

**En-tête :**\<afxstat_.h>

## <a name="a-nameafxoleinitmodule-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> `AfxOleInitModule`

Pour la prise en charge OLE d’une DLL MFC normale liée de manière dynamique aux MFC, appelez cette fonction dans la fonction de votre DLL MFC normale `CWinApp::InitInstance` pour initialiser la dll OLE MFC.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>Notes

La DLL OLE MFC est une DLL d’extension MFC ; pour qu’une DLL d’extension MFC puisse être connectée à une `CDynLinkLibrary` chaîne, elle doit créer un `CDynLinkLibrary` objet dans le contexte de chaque module qui l’utilisera. `AfxOleInitModule` crée l' `CDynLinkLibrary` objet dans le contexte de votre DLL MFC normale afin qu’il soit relié à la `CDynLinkLibrary` chaîne d’objets de la DLL MFC normale.

Si vous créez un contrôle OLE et que vous utilisez `COleControlModule` , vous ne devez pas appeler, `AfxOleInitModule` car la `InitInstance` fonction membre pour les `COleControlModule` appels `AfxOleInitModule` .

### <a name="requirements"></a>Spécifications

**En-tête**: \<afxdll_.h>

## <a name="afxnetinitmodule"></a><a name="afxnetinitmodule"></a> `AfxNetInitModule`

Pour la prise en charge des sockets MFC à partir d’une DLL MFC normale liée de manière dynamique aux MFC, ajoutez un appel à cette fonction dans la fonction de votre DLL MFC normale `CWinApp::InitInstance` pour initialiser la dll des sockets MFC.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>Notes

La DLL des sockets MFC est une DLL d’extension MFC ; pour qu’une DLL d’extension MFC puisse être connectée à une `CDynLinkLibrary` chaîne, elle doit créer un `CDynLinkLibrary` objet dans le contexte de chaque module qui l’utilisera. `AfxNetInitModule` crée l' `CDynLinkLibrary` objet dans le contexte de votre DLL MFC normale afin qu’il soit relié à la `CDynLinkLibrary` chaîne d’objets de la DLL MFC normale.

### <a name="requirements"></a>Spécifications

**En-tête :**\<afxdll_.h>

## <a name="afxgetambientactctx"></a><a name="afxgetambientactctx"></a> `AfxGetAmbientActCtx`

Utilisez cette fonction pour récupérer l’état actuel de l’indicateur d’État par module, ce qui affecte le comportement WinSxS de MFC.

### <a name="syntax"></a>Syntaxe

```cpp
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>Valeur de retour

Valeur actuelle de l’indicateur d’État du module.

### <a name="remarks"></a>Remarques

Lorsque l’indicateur est défini (valeur par défaut) et qu’un thread entre dans un module MFC (consultez [`AFX_MANAGE_STATE`](#afx_manage_state) ), le contexte du module est activé.

Si l’indicateur n’est pas défini, le contexte du module n’est pas activé à l’entrée.

Le contexte d’un module est déterminé à partir de son manifeste, souvent incorporé dans les ressources de module.

### <a name="requirements"></a>Spécifications

**En-tête :**\<afxcomctl32.h>

## <a name="afxgetstaticmodulestate"></a><a name="afxgetstaticmodulestate"></a> `AfxGetStaticModuleState`

Appelez cette fonction pour définir l’état du module avant l’initialisation et pour restaurer l’état du module précédent après le nettoyage.

### <a name="syntax"></a>Syntaxe

```cpp
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une `AFX_MODULE_STATE` structure.

### <a name="remarks"></a>Remarques

La `AFX_MODULE_STATE` structure contient des données globales pour le module, autrement dit, la partie de l’état du module qui fait l’objet d’un push ou d’un dépilé.

Par défaut, MFC utilise le handle de ressource d'application principale pour charger le modèle de ressources. Si vous disposez d’une fonction exportée dans une DLL, telle que celle qui lance une boîte de dialogue dans la DLL, le modèle de ressource est stocké dans le module DLL. Veillez à faire basculer l’état du module pour le handle approprié à utiliser. Vous pouvez basculer l’État en ajoutant le code suivant au début de la fonction :

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Cette macro permute l’état du module en cours avec l’état retourné depuis `AfxGetStaticModuleState` jusqu’à la fin de la portée actuelle.

Pour plus d’informations sur les États des modules et les MFC, consultez [gestion des données d’état des modules MFC](../managing-the-state-data-of-mfc-modules.md) et [note technique 58](../tn058-mfc-module-state-implementation.md).

### <a name="requirements"></a>Spécifications

**En-tête :**\<afxstat_.h>

## <a name="afxinitextensionmodule"></a><a name="afxinitextensionmodule"></a> `AfxInitExtensionModule`

Appelez cette fonction dans une DLL d’extension MFC `DllMain` pour initialiser la dll.

### <a name="syntax"></a>Syntaxe

```cpp
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>Paramètres

*`state`*<br/>
Référence à la structure de [ `AFX_EXTENSION_MODULE` structure](afx-extension-module-structure.md) qui doit contenir l’état du module dll d’extension MFC après l’initialisation. L’État comprend une copie des objets de classe d’exécution qui ont été initialisés par la DLL d’extension MFC dans le cadre de la construction d’objet statique normale exécutée avant l' `DllMain` entrée de.

*`hModule`*<br/>
Handle du module DLL d’extension MFC.

### <a name="return-value"></a>Valeur renvoyée

`TRUE` Si la DLL d’extension MFC est correctement initialisée ; Sinon, `FALSE` .

### <a name="remarks"></a>Remarques

Par exemple :

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL;
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

`AfxInitExtensionModule` effectue une copie du HMODULE de la DLL et capture les classes Runtime (structures) de la DLL `CRuntimeClass` et également ses fabriques d’objets ( `COleObjectFactory` objets) pour une utilisation ultérieure lorsque l' `CDynLinkLibrary` objet est créé.
Les dll d’extension MFC doivent faire deux choses dans leur `DllMain` fonction :

- Appelez [`AfxInitExtensionModule`](#afxinitextensionmodule) et vérifiez la valeur de retour.

- Créez un `CDynLinkLibrary` objet si la dll exporte des objets de [ `CRuntimeClass` structure](cruntimeclass-structure.md) ou possède ses propres ressources personnalisées.

Vous pouvez appeler `AfxTermExtensionModule` pour nettoyer la dll d’extension MFC lorsque chaque processus se détache de la dll d’extension MFC (ce qui se produit lorsque le processus se termine, ou lorsque la dll est déchargée par un `AfxFreeLibrary` appel).

### <a name="requirements"></a>Spécifications

**En-tête :**\<afxdll_.h>

## <a name="afxsetambientactctx"></a><a name="afxsetambientactctx"></a> `AfxSetAmbientActCtx`

Utilisez cette fonction pour définir l’indicateur d’État par module, ce qui affecte le comportement WinSxS de MFC.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>Paramètres

*`bSet`*<br/>
Nouvelle valeur de l’indicateur d’État du module.

### <a name="remarks"></a>Remarques

Lorsque l’indicateur est défini (valeur par défaut) et qu’un thread entre dans un module MFC (consultez [`AFX_MANAGE_STATE`](#afx_manage_state) ), le contexte du module est activé.
Si l’indicateur n’est pas défini, le contexte du module n’est pas activé à l’entrée.
Le contexte d’un module est déterminé à partir de son manifeste, souvent incorporé dans les ressources de module.

### <a name="example"></a>Exemple

```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
}
```

### <a name="requirements"></a>Spécifications

**En-tête :**\<afxcomctl32.h>

## <a name="afxtermextensionmodule"></a><a name="afxtermextensionmodule"></a> `AfxTermExtensionModule`

Appelez cette fonction pour permettre à MFC de nettoyer la DLL d’extension MFC lorsque chaque processus se détache de la DLL (ce qui se produit lorsque le processus se termine ou lorsque la DLL est déchargée par un `AfxFreeLibrary` appel).

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI AfxTermExtensionModule( AFX_EXTENSION_MODULE& state, BOOL bAll = FALSE );
```

### <a name="parameters"></a>Paramètres

*`state`*<br/>
Référence à la [`AFX_EXTENSION_MODULE`](afx-extension-module-structure.md) structure qui contient l’état du module dll d’extension MFC.

*`bAll`*<br/>
Si la valeur est TRUE, nettoie tous les modules DLL d’extension MFC. Sinon, nettoyez uniquement le module DLL actuel.

### <a name="remarks"></a>Remarques

`AfxTermExtensionModule` va supprimer tout stockage local attaché au module et supprimer toutes les entrées du cache de la table des messages. Par exemple :

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL;
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

Si votre application charge et libère des dll d’extension MFC de manière dynamique, veillez à appeler `AfxTermExtensionModule` . Étant donné que la plupart des dll d’extension MFC ne sont pas chargées dynamiquement (normalement, elles sont liées via leurs bibliothèques d’importation), l’appel à `AfxTermExtensionModule` n’est généralement pas nécessaire.

Les dll d’extension MFC doivent appeler [`AfxInitExtensionModule`](#afxinitextensionmodule) leur `DllMain` . Si la DLL exporte des [`CRuntimeClass`](cruntimeclass-structure.md) objets ou possède ses propres ressources personnalisées, vous devez également créer un `CDynLinkLibrary` objet dans `DllMain` .

### <a name="requirements"></a>Spécifications

**En-tête :**\<afxdll_.h>

## <a name="see-also"></a>Voir aussi

[Macros et globales](mfc-macros-and-globals.md)<br/>
[`AfxMessageBox`](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[Gestion des données d'état des modules MFC](../managing-the-state-data-of-mfc-modules.md)<br/>
