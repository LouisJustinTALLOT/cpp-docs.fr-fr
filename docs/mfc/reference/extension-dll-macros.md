---
title: Macros et fonctions de gestion des DLL | Documents Microsoft
ms.custom: ''
ms.date: 04/03/2017
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5e79556bf6e3ae92f7a8d4975dbd30f199e2ca8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376474"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Macros et fonctions de gestion des DLL

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Exporte des classes.|
|[AFX_MANAGE_STATE](#afx_manage_state)|Protéger une fonction exportée dans une DLL.|
|[AfxOleInitModule](#afxoleinitmodule)|Fournit la prise en charge OLE à partir d’une DLL régulière MFC qui est lié dynamiquement à MFC.|
|[AfxNetInitModule](#afxnetinitmodule)|Fournit des que sockets MFC prend en charge à partir d’une DLL régulière MFC qui est lié dynamiquement à MFC.|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|Obtient l’état actuel de l’indicateur d’état par module.|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|Définit l’état du module avant l’initialisation ou de restaurer l’état du module précédent après le nettoyage.|
|[AfxInitExtensionModule]()#afxinitextensionmodule|Initialise la DLL.|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|Définissez l’indicateur d’état par module, ce qui affecte le comportement de WinSxS de MFC.|
|[AfxTermExtensionModule]()#afxtermextensionmodule)|Permet de MFC nettoyer la DLL d’extension MFC lorsque chaque processus se détache de la DLL.|


## <a name="afx_ext_class"></a>  AFX_EXT_CLASS
[DLL d’extension MFC](../../build/extension-dlls.md) utiliser la macro **AFX_EXT_CLASS** pour exporter des classes ; les exécutables liés à la DLL d’extension MFC utilisent la macro pour importer des classes.  
   
### <a name="remarks"></a>Notes  
 Avec la **AFX_EXT_CLASS** (macro), le même en-tête utilisé pour générer la DLL d’extension MFC (s) peut être utilisé avec les exécutables liés à la DLL.  
  
 Dans le fichier d’en-tête pour votre DLL, ajoutez le **AFX_EXT_CLASS** (mot clé) à la déclaration de votre classe, comme suit :  
  
```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
``` 
  
 Pour plus d’informations, consultez [AFX_EXT_CLASS à l’aide d’importation et exportation](../../build/exporting-and-importing-using-afx-ext-class.md).  
   
### <a name="requirements"></a>Spécifications  
 En-tête : **afxv_** dll.h  
   
## <a name="afx_manage_state"></a>  AFX_MANAGE_STATE
Appelez cette macro pour protéger une fonction exportée dans une DLL.  
   
### <a name="syntax"></a>Syntaxe    
```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )  
```
### <a name="parameters"></a>Paramètres  
 `pModuleState`  
 Un pointeur vers un `AFX_MODULE_STATE` structure.  
   
### <a name="remarks"></a>Notes  
 Lorsque cette macro est appelée, `pModuleState` est l’état du module effectif pour le reste de l’exécution étendue contenante. À la sortie de la portée, l’état du module effectif précédent sera restauré automatiquement.    
 Le `AFX_MODULE_STATE` structure contient les données globales pour le module, autrement dit, la partie de l’état du module qui est envoyée ou dépilé.    
 Par défaut, MFC utilise le handle de ressource d'application principale pour charger le modèle de ressources. Si vous avez une fonction exportée dans une DLL, tel que celui qui lance une boîte de dialogue dans la DLL, ce modèle est réellement stocké dans le module DLL. Vous devez basculer l’état du module pour le handle correct à utiliser. Vous pouvez le faire en ajoutant le code suivant au début de la fonction :    
```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```
 Cela permute l’état du module en cours avec l’état retourné à partir de [AfxGetStaticModuleState](#afxgetstaticmodulestate) jusqu'à la fin de la portée actuelle.    
 Pour plus d’informations sur les États des modules et MFC, consultez « Gestion les données d’état des Modules MFC » dans [création de nouveaux Documents, fenêtres et de vues](../creating-new-documents-windows-and-views.md) et [Technical Note 58](../tn058-mfc-module-state-implementation.md).    
> [!NOTE]
>  Lorsque MFC crée un contexte d’activation pour un assembly, il utilise [AfxWinInit](#afxwininit) pour créer le contexte et `AFX_MANAGE_STATE` pour activer et désactiver. Notez également que `AFX_MANAGE_STATE` est activé pour statique bibliothèques MFC, ainsi que les DLL MFC, afin de permettre à du code MFC à exécuter dans le contexte d’activation appropriée sélectionné par la DLL de l’utilisateur. Pour plus d’informations, consultez [prise en charge des contextes d’Activation dans l’état du Module MFC](../support-for-activation-contexts-in-the-mfc-module-state.md).     
### <a name="requirements"></a>Spécifications  
 **En-tête :** afxstat_.h  
   
### <a name="see-also"></a>Voir aussi  
 [AfxGetStaticModuleState](#afxgetstaticmodulestate)

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> AfxOleInitModule
Pour la prise en charge OLE à partir d’une DLL MFC normale liée de manière dynamique aux MFC, appelez cette fonction dans votre MFC DLL régulière `CWinApp::InitInstance` fonction pour initialiser la OLE DLL MFC.  
   
### <a name="syntax"></a>Syntaxe    
```
void AFXAPI AfxOleInitModule( );  
```  
   
### <a name="remarks"></a>Notes  
 La OLE DLL MFC est une extension MFC DLL ; pour une DLL d’extension MFC puisse être raccordée à un **CDynLinkLibrary** chaîne, il doit créer un **CDynLinkLibrary** objet dans le contexte de chaque module l’utiliserez. `AfxOleInitModule` crée le **CDynLinkLibrary** de l’objet dans le contexte de votre MFC DLL régulière afin qu’il obtient câblé dans le **CDynLinkLibrary** objet de chaîne de la DLL régulière MFC.  
  
 Si vous générez un contrôle OLE et utilisez `COleControlModule`, vous ne devez pas appeler **AfxOleInitModule** , car le `InitInstance` fonction membre pour `COleControlModule` appelle `AfxOleInitModule`.  
   
### <a name="requirements"></a>Spécifications  
 **En-tête**: < afxdll_.h >  
   
### <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](mfc-macros-and-globals.md)   
 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxnetinitmodule"></a>  AfxNetInitModule
Pour les Sockets MFC prend en charge à partir d’une DLL MFC normale liée de manière dynamique aux MFC, ajoutez un appel à cette fonction dans votre MFC DLL régulière **CWinApp::InitInstance** fonction pour initialiser la DLL de Sockets de MFC.  
   
### <a name="syntax"></a>Syntaxe    
```
void AFXAPI AfxNetInitModule( );  
```  
   
### <a name="remarks"></a>Notes  
 La DLL de Sockets MFC est une extension MFC DLL ; pour une DLL d’extension MFC puisse être raccordée à un **CDynLinkLibrary** chaîne, il doit créer un **CDynLinkLibrary** objet dans le contexte de chaque module l’utiliserez. `AfxNetInitModule` crée le **CDynLinkLibrary** de l’objet dans le contexte de votre MFC DLL régulière afin qu’il obtient câblé dans le **CDynLinkLibrary** objet de chaîne de la DLL régulière MFC.  
   
### <a name="requirements"></a>Spécifications  
 **En-tête :** < afxdll_.h >  
   
### <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](mfc-macros-and-globals.md)   
 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxgetambientactctx"></a> AfxGetAmbientActCtx
Utilisez cette fonction pour obtenir l’état actuel de l’indicateur d’état par module, ce qui affecte le comportement de WinSxS de MFC.  
   
### <a name="syntax"></a>Syntaxe    
```  
BOOL AFXAPI AfxGetAmbientActCtx();   
```  
   
### <a name="return-value"></a>Valeur de retour  
 Valeur actuelle de module état indicateur.  
   
### <a name="remarks"></a>Notes  
 Lorsque l’indicateur est défini (qui est la valeur par défaut) et un thread entre dans un module MFC (consultez [AFX_MANAGE_STATE](#afx_manage_state)), le contexte du module est activé.  
  
 Si l’indicateur n’est pas défini, le contexte du module n’est pas activé sur l’entrée.  
  
 Le contexte d’un module est déterminé à partir de son manifeste généralement incorporé dans les ressources de module.  
   
### <a name="requirements"></a>Spécifications  
 **En-tête :** afxcomctl32.h  
   
### <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](mfc-macros-and-globals.md)   
 [AFX_MANAGE_STATE](#afx_manage_state)   
 [Gestion des données d’état des Modules MFC](../managing-the-state-data-of-mfc-modules.md)   
 [AfxSetAmbientActCtx](#setambientactctx)
 
## <a name="afxgetstaticmodulestate"></a> AfxGetStaticModuleState
Appelez cette fonction pour définir l’état du module avant l’initialisation ou de restaurer l’état du module précédent après le nettoyage.  
   
### <a name="syntax"></a>Syntaxe    
```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );  
```  
   
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `AFX_MODULE_STATE` structure.  
   
### <a name="remarks"></a>Notes  
 Le `AFX_MODULE_STATE` structure contient les données globales pour le module, autrement dit, la partie de l’état du module qui est envoyée ou dépilé.  
  
 Par défaut, MFC utilise le handle de ressource d'application principale pour charger le modèle de ressources. Si vous avez une fonction exportée dans une DLL, tel que celui qui lance une boîte de dialogue dans la DLL, ce modèle est réellement stocké dans le module DLL. Vous devez basculer l’état du module pour le handle correct à utiliser. Vous pouvez le faire en ajoutant le code suivant au début de la fonction :  
  
```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```
  
 Cela permute l’état du module en cours avec l’état retourné à partir de `AfxGetStaticModuleState` jusqu'à la fin de la portée actuelle.  
  
 Pour plus d’informations sur les États des modules et MFC, consultez « Gestion les données d’état des Modules MFC » dans [création de nouveaux Documents, fenêtres et de vues](../creating-new-documents-windows-and-views.md) et [Technical Note 58](../tn058-mfc-module-state-implementation.md).  
   
### <a name="requirements"></a>Spécifications  
 **En-tête :** afxstat_.h  
   

## <a name="afxinitextensionmodule"></a> AfxInitExtensionModule
Appelez cette fonction dans une DLL d’extension MFC `DllMain` pour initialiser la DLL.  
   
### <a name="syntax"></a>Syntaxe    
```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );  
```
### <a name="parameters"></a>Paramètres  
 `state`  
 Une référence à la [AFX_EXTENSION_MODULE, Structure](afx-extension-module-structure.md) structure qui contient l’état du module DLL d’extension MFC après l’initialisation. L’état inclut une copie des objets de classe runtime qui ont été initialisé par la DLL d’extension MFC dans le cadre de la construction d’objet statique normal exécutée avant `DllMain` est entré.  
  
 `hModule`  
 Handle du module DLL d’extension MFC.  
   
### <a name="return-value"></a>Valeur de retour  
 **TRUE** si la DLL d’extension MFC est correctement initialisé ; sinon, **FALSE**.  
   
### <a name="remarks"></a>Notes  
 Par exemple :  
  
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

```
  
 `AfxInitExtensionModule` effectue une copie de la DLL **HMODULE** et capture les classes d’exécution de la DLL (`CRuntimeClass` structures), ainsi que ses fabriques d’objets (`COleObjectFactory` objets) à utiliser ultérieurement, lorsque le **CDynLinkLibrary**objet est créé.    
 L’extension MFC DLL devoir faire deux choses dans leur `DllMain` (fonction) :    
-   Appelez [AfxInitExtensionModule](#_mfc_afxinitextensionmodule) et vérifiez la valeur de retour.   
-   Créer un **CDynLinkLibrary** exportez si la DLL de l’objet [CRuntimeClass Structure](cruntimeclass-structure.md) des objets ou possède ses propres ressources personnalisées.    
 Vous pouvez appeler `AfxTermExtensionModule` pour nettoyer la DLL d’extension MFC lorsque chaque processus se détache de la DLL d’extension MFC (ce qui se produit quand le processus se termine, ou lorsque la DLL est déchargée à la suite d’un `AfxFreeLibrary` appeler).     

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxdll_.h     

### <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](mfc-macros-and-globals.md)   
 [AfxTermExtensionModule](#afxtermextensionmodule)

 ## <a name="afxsetambientactctx"></a>  AfxSetAmbientActCtx
Cette fonction permet de définir l’indicateur d’état par module, ce qui affecte le comportement de WinSxS de MFC.  
   
### <a name="syntax"></a>Syntaxe  
  ```
   void AFXAPI AfxSetAmbientActCtx( BOOL bSet  
);  
```
### <a name="parameters"></a>Paramètres  
 `bSet`  
 Nouvelle valeur de l’indicateur d’état de module.  
   
### <a name="remarks"></a>Notes  
 Lorsque l’indicateur est défini (qui est la valeur par défaut) et un thread entre dans un module MFC (consultez [AFX_MANAGE_STATE](#afx_manage_state)), le contexte du module est activé.    
 Si l’indicateur n’est pas défini, le contexte du module n’est pas activé sur l’entrée.    
 Le contexte d’un module est déterminé à partir de son manifeste généralement incorporé dans les ressources de module.  
   
### <a name="example"></a>Exemple  
 ```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
```
   
### <a name="requirements"></a>Spécifications  
 **En-tête :** afxcomctl32.h  
   
### <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](mfc-macros-and-globals.md)   
 [AfxGetAmbientActCtx](#afxgetambientactctx)   
 [AFX_MANAGE_STATE](#afx_manage_state)   
 [Gestion des données d’état des modules MFC](../managing-the-state-data-of-mfc-modules.md) 

## <a name="afxtermextensionmodule"></a>  AfxTermExtensionModule

Appelez cette fonction pour permettre des MFC nettoyage de la DLL d’extension MFC lorsque chaque processus se détache de la DLL (ce qui se produit quand le processus se termine, ou lorsque la DLL est déchargée à la suite d’un `AfxFreeLibrary` appeler).  
   
### <a name="syntax"></a>Syntaxe  
  ```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );  
```
### <a name="parameters"></a>Paramètres  
 `state`  
 Une référence à la [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) structure qui contient l’état du module DLL d’extension MFC.  
  
 *Boule*  
 Si **TRUE**, nettoyer tous les modules DLL d’extension MFC. Sinon, nettoyage uniquement le module DLL en cours.  
   
### <a name="remarks"></a>Notes  
 `AfxTermExtensionModule` Supprime tout attaché au module de stockage local et supprimer toutes les entrées du cache de mappage de message. Par exemple :  
  
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
  
 Si votre application est chargée et libère dynamiquement la DLL d’extension MFC, veillez à appeler `AfxTermExtensionModule`. Depuis la plupart des DLL ne sont pas chargées dynamiquement d’extension MFC (en règle générale, ils sont liés via leurs bibliothèques d’importation), l’appel à `AfxTermExtensionModule` est généralement pas nécessaire.  
  
 Besoin de DLL d’extension MFC appeler [AfxInitExtensionModule](#afxinitextensionmodule) dans leurs `DllMain`. Si l’exportation de la DLL [CRuntimeClass](cruntimeclass-structure.md) des objets ou possède ses propres ressources personnalisées, vous devez également créer un **CDynLinkLibrary** dans l’objet `DllMain`.  
   
### <a name="requirements"></a>Spécifications  
 **En-tête :** afxdll_.h  
   
### <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](mfc-macros-and-globals.md)   
 [AfxInitExtensionModule](#afxinitextensionmodule)
 




