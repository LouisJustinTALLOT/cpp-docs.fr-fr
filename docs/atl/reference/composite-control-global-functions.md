---
title: Fonctions mondiales de contrôle composite
ms.date: 11/04/2016
f1_keywords:
- atlhost/ATL::AtlAxDialogBox
- atlhost/ATL::AtlAxCreateDialog
- atlhost/ATL::AtlAxCreateControl
- atlhost/ATL::AtlAxCreateControlEx
- atlhost/ATL::AtlAxCreateControlLic
- atlhost/ATL::AtlAxCreateControlLicEx
- atlhost/ATL::AtlAxAttachControl
- atlhost/ATL::AtlAxGetHost
- atlhost/ATL::AtlAxGetControl
- atlhost/ATL::AtlSetChildSite
- atlhost/ATL::AtlAxWinInit
- atlhost/ATL::AtlAxWinTerm
- atlhost/ATL::AtlGetObjectSourceInterface
helpviewer_keywords:
- composite controls, global functions
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
ms.openlocfilehash: 99ecd4cf04b3eb696f897d6ef5a5e3839d46ef17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331613"
---
# <a name="composite-control-global-functions"></a>Fonctions mondiales de contrôle composite

Ces fonctions fournissent un soutien pour la création de boîtes de dialogue, et pour la création, l’hébergement et l’octroi de licences activeX contrôles.

> [!IMPORTANT]
> Les fonctions énumérées dans le tableau suivant ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|Crée une boîte de dialogue modale à partir d'un modèle de boîte de dialogue fourni par l'utilisateur. La boîte de dialogue qui en résulte peut contenir des commandes ActiveX.|
|[AtlAxCreateDialog](#atlaxcreatedialog)|Crée une boîte de dialogue non modale à partir d'un modèle de boîte de dialogue fourni par l'utilisateur. La boîte de dialogue qui en résulte peut contenir des commandes ActiveX.|
|[AtlAxCreateControl](#atlaxcreatecontrol)|Crée un contrôle ActiveX, puis initialise et héberge ce dernier dans la fenêtre spécifiée.|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|Crée un contrôle ActiveX, l’initialise, l’héberge dans la fenêtre spécifiée et récupère un pointeur d’interface (ou des pointeurs) du contrôle.|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|Crée un contrôle ActiveX sous licence, puis initialise et héberge ce dernier dans la fenêtre spécifiée.|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|Crée un contrôle ActiveX sous licence, l’initialise, l’héberge dans la fenêtre spécifiée et récupère un pointeur d’interface (ou des pointeurs) du contrôle.|
|[AtlAxAttachControl](#atlaxattachcontrol)|Joint un contrôle précédemment créé à la fenêtre spécifiée.|
|[AtlAxGetHost](#atlaxgethost)|Utilisé pour obtenir un pointeur d’interface directe sur le conteneur pour une fenêtre spécifiée (le cas échéant), compte tenu de sa poignée.|
|[AtlAxGetControl](#atlaxgetcontrol)|Utilisé pour obtenir un pointeur d’interface directe au contrôle contenu à l’intérieur d’une fenêtre spécifiée (le cas échéant), compte tenu de sa poignée.|
|[AtlSetChildSite](#atlsetchildsite)|Initialise le `IUnknown` site de l’enfant.|
|[AtlAxWinInit](#atlaxwininit)|Initialise le code d’hébergement des objets AxWin.|
|[AtlAxWinTerm](#atlaxwinterm)|Uninitialise le code d’hébergement des objets AxWin.|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|Renvoie des informations sur l’interface source par défaut d’un objet.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlhost.h

## <a name="atlaxdialogbox"></a><a name="atlaxdialogbox"></a>AtlAxDialogBox

Crée une boîte de dialogue modale à partir d'un modèle de boîte de dialogue fourni par l'utilisateur.

```
ATLAPI_(int) AtlAxDialogBox(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>Paramètres

*hInstance*<br/>
[dans] Identifie une instance du module dont le fichier exécutable contient le modèle de boîte de dialogue.

*lpTemplateName*<br/>
[dans] Identifie le modèle de boîte de dialogue. Ce paramètre est soit le pointeur d’une chaîne de caractères à durée nulle qui spécifie le nom du modèle de boîte de dialogue ou une valeur d’intégrage qui spécifie l’identifiant de ressource du modèle de boîte de dialogue. Si le paramètre spécifie un identifiant de ressource, son mot de haute commande doit être nul et son mot de faible ordre doit contenir l’identifiant. Vous pouvez utiliser la macro [MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew) pour créer cette valeur.

*hWndParent*<br/>
[dans] Identifie la fenêtre qui possède la boîte de dialogue.

*lpDialogProc*<br/>
[dans] Points à la procédure de boîte de dialogue. Pour plus d’informations sur la procédure de boîte de dialogue, voir [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
[dans] Spécifie la valeur de passer à la boîte de dialogue dans le paramètre *lParam* du message WM_INITDIALOG.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Pour `AtlAxDialogBox` utiliser avec un modèle de dialogue qui contient un contrôle ActiveX, spécifiez une chaîne CLSID, APPID ou URL valide comme champ *texte* de la section **CONTROL** de la ressource de dialogue, ainsi que "AtlAxWin80" comme champ *de nom de classe* sous la même section. Ce qui suit démontre à quoi pourrait ressembler une section **CONTROL** valide :

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

Pour plus d’informations sur l’édition de scripts de ressources, voir [Comment : Ouvrir un fichier de script de ressource dans le format de texte](../../windows/how-to-open-a-resource-script-file-in-text-format.md). Pour plus d’informations sur les instructions de contrôle de définition des ressources, voir [Paramètres de contrôle commun](/windows/win32/menurc/common-control-parameters) sous Windows SDK: SDK Tools.

Pour plus d’informations sur les boîtes de dialogue en général, consultez [DialogBox](/windows/win32/api/winuser/nf-winuser-dialogboxw) et [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) dans le Windows SDK.

## <a name="atlaxcreatedialog"></a><a name="atlaxcreatedialog"></a>AtlAxCreateDialog

Crée une boîte de dialogue non modale à partir d'un modèle de boîte de dialogue fourni par l'utilisateur.

```
ATLAPI_(HWND) AtlAxCreateDialog(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>Paramètres

*hInstance*<br/>
[dans] Identifie une instance du module dont le fichier exécutable contient le modèle de boîte de dialogue.

*lpTemplateName*<br/>
[dans] Identifie le modèle de boîte de dialogue. Ce paramètre est soit le pointeur d’une chaîne de caractères à durée nulle qui spécifie le nom du modèle de boîte de dialogue ou une valeur d’intégrage qui spécifie l’identifiant de ressource du modèle de boîte de dialogue. Si le paramètre spécifie un identifiant de ressource, son mot de haute commande doit être nul et son mot de faible ordre doit contenir l’identifiant. Vous pouvez utiliser la macro [MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew) pour créer cette valeur.

*hWndParent*<br/>
[dans] Identifie la fenêtre qui possède la boîte de dialogue.

*lpDialogProc*<br/>
[dans] Points à la procédure de boîte de dialogue. Pour plus d’informations sur la procédure de boîte de dialogue, voir [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
[dans] Spécifie la valeur de passer à la boîte de dialogue dans le paramètre *lParam* du message WM_INITDIALOG.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

La boîte de dialogue qui en résulte peut contenir des commandes ActiveX.

Voir [CreateDialog](/windows/win32/api/winuser/nf-winuser-createdialogw) et [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) dans le SDK Windows.

## <a name="atlaxcreatecontrol"></a><a name="atlaxcreatecontrol"></a>AtlAxCreateControl

Crée un contrôle ActiveX, puis initialise et héberge ce dernier dans la fenêtre spécifiée.

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Un pointeur à une corde à passer au contrôle. Doit être formaté de l’une des façons suivantes :

- Un ProgID tel que`"MSCAL.Calendar.7"`

- Un CLSID tel que`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Une URL telle que`"<https://www.microsoft.com>"`

- Une référence à un document actif tel que`"file://\\\Documents\MyDoc.doc"`

- Un fragment de HTML tel que`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`doit précéder le fragment HTML afin qu’il soit désigné comme étant un flux MSHTML.

*hWnd*<br/>
[dans] Manipulez la fenêtre à laquelle le contrôle sera fixé.

*pStream*<br/>
[dans] Un pointeur à un flux qui est utilisé pour initialiser les propriétés du contrôle. Sa valeur peut être NULL.

*ppUnkContainer*<br/>
[out] L’adresse d’un pointeur qui recevra le `IUnknown` du conteneur. Sa valeur peut être NULL.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction globale vous donne le même résultat que l’appel [AtlAxCreateControlEx](#atlaxcreatecontrolex)(*lpszName*, *hWnd*, *pStream*, NULL, NULL, NULL, NULL, NULL);.

Pour créer un contrôle ActiveX sous licence, voir [AtlAxCreateControlLic](#atlaxcreatecontrollic).

## <a name="atlaxcreatecontrolex"></a><a name="atlaxcreatecontrolex"></a>AtlAxCreateControlEx

Crée un contrôle ActiveX, puis initialise et héberge ce dernier dans la fenêtre spécifiée. Un pointeur d'interface et un récepteur d'événements du nouveau contrôle peuvent également être créés.

```
ATLAPI AtlAxCreateControlEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Un pointeur à une corde à passer au contrôle. Doit être formaté de l’une des façons suivantes :

- Un ProgID tel que`"MSCAL.Calendar.7"`

- Un CLSID tel que`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Une URL telle que`"<https://www.microsoft.com>"`

- Une référence à un document actif tel que`"file://\\\Documents\MyDoc.doc"`

- Un fragment de HTML tel que`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`doit précéder le fragment HTML afin qu’il soit désigné comme étant un flux MSHTML.

*hWnd*<br/>
[dans] Manipulez la fenêtre à laquelle le contrôle sera fixé.

*pStream*<br/>
[dans] Un pointeur à un flux qui est utilisé pour initialiser les propriétés du contrôle. Sa valeur peut être NULL.

*ppUnkContainer*<br/>
[out] L’adresse d’un pointeur qui recevra le `IUnknown` du conteneur. Sa valeur peut être NULL.

*ppUnkControl*<br/>
[out] L’adresse d’un pointeur qui recevra le `IUnknown` contrôle créé. Sa valeur peut être NULL.

*iidSink iidSink*<br/>
L’identifiant d’interface d’une interface sortante sur l’objet contenu.

*punkSink punkSink*<br/>
Un pointeur `IUnknown` à l’interface de l’objet de l’évier à connecter au point de connexion spécifié par *iidSink* sur l’objet contenu après la création réussie de l’objet contenu.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

`AtlAxCreateControlEx`est similaire à [AtlAxCreateControl,](#atlaxcreatecontrol) mais vous permet également de recevoir un pointeur d’interface pour le contrôle nouvellement créé et mettre en place un évier d’événement pour recevoir des événements tirés par le contrôle.

Pour créer un contrôle ActiveX sous licence, voir [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex).

## <a name="atlaxcreatecontrollic"></a><a name="atlaxcreatecontrollic"></a>AtlAxCreateControlLic

Crée un contrôle ActiveX sous licence, puis initialise et héberge ce dernier dans la fenêtre spécifiée.

```
ATLAPI AtlAxCreateControlLic(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Un pointeur à une corde à passer au contrôle. Doit être formaté de l’une des façons suivantes :

- Un ProgID tel que`"MSCAL.Calendar.7"`

- Un CLSID tel que`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Une URL telle que`"<https://www.microsoft.com>"`

- Une référence à un document actif tel que`"file://\\\Documents\MyDoc.doc"`

- Un fragment de HTML tel que`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`doit précéder le fragment HTML afin qu’il soit désigné comme étant un flux MSHTML.

*hWnd*<br/>
Manipulez la fenêtre à laquelle le contrôle sera fixé.

*pStream*<br/>
Un pointeur à un flux qui est utilisé pour initialiser les propriétés du contrôle. Sa valeur peut être NULL.

*ppUnkContainer*<br/>
L’adresse d’un pointeur qui recevra le `IUnknown` du conteneur. Sa valeur peut être NULL.

*bstrLic bstrLic*<br/>
Le BSTR contenant la licence pour le contrôle.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="example"></a>Exemple

Voir [Hosting ActiveX Controls À l’aide d’ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour un échantillon de la façon d’utiliser `AtlAxCreateControlLic`.

## <a name="atlaxcreatecontrollicex"></a><a name="atlaxcreatecontrollicex"></a>AtlAxCreateControlLicEx

Crée un contrôle ActiveX sous licence, puis initialise et héberge ce dernier dans la fenêtre spécifiée. Un pointeur d'interface et un récepteur d'événements du nouveau contrôle peuvent également être créés.

```
ATLAPI AtlAxCreateControlLicEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Un pointeur à une corde à passer au contrôle. Doit être formaté de l’une des façons suivantes :

- Un ProgID tel que`"MSCAL.Calendar.7"`

- Un CLSID tel que`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Une URL telle que`"<https://www.microsoft.com>"`

- Une référence à un document actif tel que`"file://\\\Documents\MyDoc.doc"`

- Un fragment de HTML tel que`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`doit précéder le fragment HTML afin qu’il soit désigné comme étant un flux MSHTML.

*hWnd*<br/>
Manipulez la fenêtre à laquelle le contrôle sera fixé.

*pStream*<br/>
Un pointeur à un flux qui est utilisé pour initialiser les propriétés du contrôle. Sa valeur peut être NULL.

*ppUnkContainer*<br/>
L’adresse d’un pointeur qui recevra le `IUnknown` du conteneur. Sa valeur peut être NULL.

*ppUnkControl*<br/>
[out] L’adresse d’un pointeur qui recevra le `IUnknown` contrôle créé. Sa valeur peut être NULL.

*iidSink iidSink*<br/>
L’identifiant d’interface d’une interface sortante sur l’objet contenu.

*punkSink punkSink*<br/>
Un pointeur `IUnknown` à l’interface de l’objet de l’évier à connecter au point de connexion spécifié par *iidSink* sur l’objet contenu après la création réussie de l’objet contenu.

*bstrLic bstrLic*<br/>
Le BSTR contenant la licence pour le contrôle.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

`AtlAxCreateControlLicEx`est similaire à [AtlAxCreateControlLic,](#atlaxcreatecontrollic) mais vous permet également de recevoir un pointeur d’interface pour le contrôle nouvellement créé et mettre en place un évier d’événement pour recevoir les événements tirés par le contrôle.

### <a name="example"></a>Exemple

Voir [Hosting ActiveX Controls À l’aide d’ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour un échantillon de la façon d’utiliser `AtlAxCreateControlLicEx`.

## <a name="atlaxattachcontrol"></a><a name="atlaxattachcontrol"></a>AtlAxAttachControl

Joint un contrôle précédemment créé à la fenêtre spécifiée.

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Paramètres

*pControl*<br/>
[dans] Un pointeur `IUnknown` au contrôle.

*hWnd*<br/>
[dans] Manipulez la fenêtre qui accueillera le contrôle.

*ppUnkContainer*<br/>
[out] Un pointeur à `IUnknown` un pointeur de l’objet de conteneur.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Utilisez [AtlAxCreateControlEx](#atlaxcreatecontrolex) et [AtlAxCreateControl](#atlaxcreatecontrol) pour créer et attacher simultanément un contrôle.

> [!NOTE]
> L’objet de commande attaché doit `AtlAxAttachControl`être correctement initialisé avant d’appeler .

## <a name="atlaxgethost"></a><a name="atlaxgethost"></a>AtlAxGetHost

Obtient un pointeur d'interface direct vers le conteneur d'une fenêtre spécifique (le cas échéant), en fonction de son handle.

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
[dans] Une poignée à la fenêtre qui héberge le contrôle.

*Pp*<br/>
[out] Le `IUnknown` conteneur du contrôle.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="atlaxgetcontrol"></a><a name="atlaxgetcontrol"></a>AtlAxGetControl

Obtient un pointeur d'interface direct vers le contrôle contenu dans une fenêtre spécifique en fonction de son handle.

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
[dans] Une poignée à la fenêtre qui héberge le contrôle.

*Pp*<br/>
[out] Le `IUnknown` contrôle hébergé.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

## <a name="atlsetchildsite"></a><a name="atlsetchildsite"></a>AtlSetChildSite

Appelez cette fonction pour définir le site `IUnknown` de l’objet de l’enfant à l’objet parent.

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>Paramètres

*punkChild (en)*<br/>
[dans] Un pointeur `IUnknown` à l’interface de l’enfant.

*punkParent (punkParent)*<br/>
[dans] Un pointeur `IUnknown` à l’interface du parent.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="atlaxwininit"></a><a name="atlaxwininit"></a>AtlAxWinInit

Cette fonction est para parasitaire du code d’hébergement de contrôle d’ATL en enregistrant les classes de fenêtre **"AtlAxWin80"** et **"AtlAxWinLic80"** ainsi que quelques messages de fenêtre personnalisés.

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’initialisation du code d’hébergement de contrôle a été couronnée de succès; autrement FALSE.

### <a name="remarks"></a>Notes

Cette fonction doit être appelée avant d’utiliser l’API d’hébergement de contrôle ATL. Suite à un appel à cette fonction, la classe de fenêtre **"AtlAxWin"** peut être utilisée dans les appels à [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) ou [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw), tel que décrit dans le Windows SDK.

## <a name="atlaxwinterm"></a><a name="atlaxwinterm"></a>AtlAxWinTerm

Cette fonction uninitialise le code d’hébergement de contrôle d’ATL en non-enregistré les classes de fenêtre **"AtlAxWin80"** et **"AtlAxWinLic80".**

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours VRAI.

### <a name="remarks"></a>Notes

Cette fonction appelle simplement [UnregisterClass](/windows/win32/api/winuser/nf-winuser-unregisterclassw) comme décrit dans le SDK Windows.

Appelez cette fonction pour nettoyer après que toutes les fenêtres hôtes existantes ont été détruites si vous avez appelé [AtlAxWinInit](#atlaxwininit) et vous n’avez plus besoin de créer des fenêtres d’hôte. Si vous n’appelez pas cette fonction, la classe de fenêtre ne sera pas enregistrée automatiquement lorsque le processus prendra fin.

## <a name="atlgetobjectsourceinterface"></a><a name="atlgetobjectsourceinterface"></a>AtlGetObjectSourceInterface

Appelez cette fonction pour récupérer des informations sur l'interface source par défaut d'un objet.

```
ATLAPI AtlGetObjectSourceInterface(
    IUnknown* punkObj,
    GUID* plibid,
    IID* piid,
    unsigned short* pdwMajor,
    unsigned short* pdwMinor);
```

### <a name="parameters"></a>Paramètres

*punkObj (punkObj)*<br/>
[dans] Un pointeur de l’objet pour lequel l’information doit être retournée.

*plibid*<br/>
[out] Un pointeur sur le LIBID de la bibliothèque de type contenant la définition de l’interface source.

*piid*<br/>
[out] Un pointeur sur l’interface ID de l’interface source par défaut de l’objet.

*pdwMajor*<br/>
[out] Un pointeur sur le numéro de version principal de la bibliothèque de type contenant la définition de l’interface source.

*pdwMinor*<br/>
[out] Un pointeur sur le numéro de version mineur de la bibliothèque de type contenant la définition de l’interface source.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

`AtlGetObjectSourceInterface`peut vous fournir l’interface ID de l’interface source par défaut, ainsi que le LIBID et les numéros de version majeur et mineurs de la bibliothèque de type décrivant cette interface.

> [!NOTE]
> Pour que cette fonction récupère avec succès les informations demandées, l’objet représenté par *punkObj* doit implémenter `IDispatch` (et retourner des informations de type à `IDispatch::GetTypeInfo`travers ) plus il doit également implémenter soit `IProvideClassInfo2` ou `IPersist`. Les informations de type pour l’interface source doivent être `IDispatch`dans la bibliothèque de même type que les informations de type pour .

### <a name="example"></a>Exemple

L’exemple ci-dessous montre comment vous `CEasySink`pourriez définir une classe d’évier d’événement, , qui réduit le nombre d’arguments de modèle que vous pouvez passer à `IDispEventImpl` l’essentiel nu. `EasyAdvise`et `EasyUnadvise` `AtlGetObjectSourceInterface` utiliser pour initialiser les membres [IDispEventImpl](../../atl/reference/idispeventimpl-class.md) avant d’appeler [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) ou [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise).

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)<br/>
[Macro de contrôle composite](../../atl/reference/composite-control-macros.md)
