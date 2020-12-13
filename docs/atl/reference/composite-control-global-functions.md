---
description: 'En savoir plus sur : fonctions globales de contrôle composite'
title: Fonctions globales de contrôle composite
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
ms.openlocfilehash: fa46cc46247d409b85772e6c1aab229d97fd1c36
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141243"
---
# <a name="composite-control-global-functions"></a>Fonctions globales de contrôle composite

Ces fonctions prennent en charge la création de boîtes de dialogue, ainsi que la création, l’hébergement et la gestion des licences des contrôles ActiveX.

> [!IMPORTANT]
> Les fonctions listées dans le tableau suivant ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|Fonction|Description|
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|Crée une boîte de dialogue modale à partir d'un modèle de boîte de dialogue fourni par l'utilisateur. La boîte de dialogue qui en résulte peut contenir des contrôles ActiveX.|
|[AtlAxCreateDialog](#atlaxcreatedialog)|Crée une boîte de dialogue non modale à partir d'un modèle de boîte de dialogue fourni par l'utilisateur. La boîte de dialogue qui en résulte peut contenir des contrôles ActiveX.|
|[AtlAxCreateControl](#atlaxcreatecontrol)|Crée un contrôle ActiveX, puis initialise et héberge ce dernier dans la fenêtre spécifiée.|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|Crée un contrôle ActiveX, l’initialise, l’héberge dans la fenêtre spécifiée et récupère un pointeur d’interface (ou des pointeurs) du contrôle.|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|Crée un contrôle ActiveX sous licence, puis initialise et héberge ce dernier dans la fenêtre spécifiée.|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|Crée un contrôle ActiveX sous licence, l’initialise, l’héberge dans la fenêtre spécifiée et récupère un pointeur d’interface (ou des pointeurs) du contrôle.|
|[AtlAxAttachControl](#atlaxattachcontrol)|Joint un contrôle précédemment créé à la fenêtre spécifiée.|
|[AtlAxGetHost](#atlaxgethost)|Utilisé pour obtenir un pointeur d’interface directe vers le conteneur pour une fenêtre spécifiée (le cas échéant), en fonction de son handle.|
|[AtlAxGetControl](#atlaxgetcontrol)|Utilisé pour obtenir un pointeur d’interface directe vers le contrôle contenu dans une fenêtre spécifiée (le cas échéant), en fonction de son handle.|
|[AtlSetChildSite](#atlsetchildsite)|Initialise le `IUnknown` du site enfant.|
|[AtlAxWinInit](#atlaxwininit)|Initialise le code d’hébergement pour les objets AxWin.|
|[AtlAxWinTerm](#atlaxwinterm)|Désinitialise le code d’hébergement pour les objets AxWin.|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|Retourne des informations sur l’interface source par défaut d’un objet.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlhost. h

## <a name="atlaxdialogbox"></a><a name="atlaxdialogbox"></a> AtlAxDialogBox

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
dans Identifie une instance du module dont le fichier exécutable contient le modèle de boîte de dialogue.

*lpTemplateName*<br/>
dans Identifie le modèle de boîte de dialogue. Ce paramètre est le pointeur vers une chaîne de caractères se terminant par un caractère null qui spécifie le nom du modèle de boîte de dialogue ou une valeur entière qui spécifie l’identificateur de ressource du modèle de boîte de dialogue. Si le paramètre spécifie un identificateur de ressource, son mot de poids fort doit être égal à zéro et son mot de poids faible doit contenir l’identificateur. Vous pouvez utiliser la macro [MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew) pour créer cette valeur.

*hWndParent*<br/>
dans Identifie la fenêtre propriétaire de la boîte de dialogue.

*lpDialogProc*<br/>
dans Pointe vers la procédure de la boîte de dialogue. Pour plus d’informations sur la procédure de boîte de dialogue, consultez [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
dans Spécifie la valeur à passer à la boîte de dialogue dans le paramètre *lParam* du message de WM_INITDIALOG.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Pour utiliser `AtlAxDialogBox` avec un modèle de boîte de dialogue qui contient un contrôle ActiveX, spécifiez une chaîne CLSID, AppID ou URL valide comme champ de *texte* de la section de **contrôle** de la ressource de boîte de dialogue, avec « AtlAxWin80 » comme champ de *nom de classe* sous la même section. L’exemple suivant montre à quoi peut ressembler une section de **contrôle** valide :

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

Pour plus d’informations sur la modification des scripts de ressources, consultez [Comment : créer des ressources](../../windows/how-to-create-a-resource-script-file.md). Pour plus d’informations sur le contrôle des instructions de définition de ressource, consultez [paramètres de contrôle communs](/windows/win32/menurc/common-control-parameters) sous SDK Windows : SDK Tools.

Pour plus d’informations sur les boîtes de dialogue en général, reportez-vous à [DialogBox](/windows/win32/api/winuser/nf-winuser-dialogboxw) et [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) dans le SDK Windows.

## <a name="atlaxcreatedialog"></a><a name="atlaxcreatedialog"></a> AtlAxCreateDialog

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
dans Identifie une instance du module dont le fichier exécutable contient le modèle de boîte de dialogue.

*lpTemplateName*<br/>
dans Identifie le modèle de boîte de dialogue. Ce paramètre est le pointeur vers une chaîne de caractères se terminant par un caractère null qui spécifie le nom du modèle de boîte de dialogue ou une valeur entière qui spécifie l’identificateur de ressource du modèle de boîte de dialogue. Si le paramètre spécifie un identificateur de ressource, son mot de poids fort doit être égal à zéro et son mot de poids faible doit contenir l’identificateur. Vous pouvez utiliser la macro [MAKEINTRESOURCE](/windows/win32/api/winuser/nf-winuser-makeintresourcew) pour créer cette valeur.

*hWndParent*<br/>
dans Identifie la fenêtre propriétaire de la boîte de dialogue.

*lpDialogProc*<br/>
dans Pointe vers la procédure de la boîte de dialogue. Pour plus d’informations sur la procédure de boîte de dialogue, consultez [DialogProc](/windows/win32/api/winuser/nc-winuser-dlgproc).

*dwInitParam*<br/>
dans Spécifie la valeur à passer à la boîte de dialogue dans le paramètre *lParam* du message de WM_INITDIALOG.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

La boîte de dialogue qui en résulte peut contenir des contrôles ActiveX.

Consultez [createDialog](/windows/win32/api/winuser/nf-winuser-createdialogw) et [CreateDialogParam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) dans le SDK Windows.

## <a name="atlaxcreatecontrol"></a><a name="atlaxcreatecontrol"></a> AtlAxCreateControl

Crée un contrôle ActiveX, puis initialise et héberge ce dernier dans la fenêtre spécifiée.

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
Pointeur vers une chaîne à passer au contrôle. Doit être mis en forme de l’une des manières suivantes :

- Un ProgID tel que `"MSCAL.Calendar.7"`

- Un CLSID tel que `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Une URL telle que `"<https://www.microsoft.com>"`

- Référence à un document actif tel que `"file://\\\Documents\MyDoc.doc"`

- Un fragment de code HTML tel que `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` doit précéder le fragment HTML afin qu’il soit désigné comme un flux MSHTML.

*hWnd*<br/>
dans Handle de la fenêtre à laquelle le contrôle sera attaché.

*pStream*<br/>
dans Pointeur vers un flux utilisé pour initialiser les propriétés du contrôle. Sa valeur peut être NULL.

*ppUnkContainer*<br/>
à Adresse d’un pointeur qui recevra le `IUnknown` du conteneur. Sa valeur peut être NULL.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction globale donne le même résultat que l’appel de [AtlAxCreateControlEx](#atlaxcreatecontrolex)(*lpszName*, *HWND*, *pStream*, NULL, NULL, NULL, null);.

Pour créer un contrôle ActiveX sous licence, consultez [AtlAxCreateControlLic](#atlaxcreatecontrollic).

## <a name="atlaxcreatecontrolex"></a><a name="atlaxcreatecontrolex"></a> AtlAxCreateControlEx

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

*lpszName*<br/>
Pointeur vers une chaîne à passer au contrôle. Doit être mis en forme de l’une des manières suivantes :

- Un ProgID tel que `"MSCAL.Calendar.7"`

- Un CLSID tel que `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Une URL telle que `"<https://www.microsoft.com>"`

- Référence à un document actif tel que `"file://\\\Documents\MyDoc.doc"`

- Un fragment de code HTML tel que `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` doit précéder le fragment HTML afin qu’il soit désigné comme un flux MSHTML.

*hWnd*<br/>
dans Handle de la fenêtre à laquelle le contrôle sera attaché.

*pStream*<br/>
dans Pointeur vers un flux utilisé pour initialiser les propriétés du contrôle. Sa valeur peut être NULL.

*ppUnkContainer*<br/>
à Adresse d’un pointeur qui recevra le `IUnknown` du conteneur. Sa valeur peut être NULL.

*ppUnkControl*<br/>
à Adresse d’un pointeur qui recevra le `IUnknown` du contrôle créé. Sa valeur peut être NULL.

*iidSink*<br/>
Identificateur d’interface d’une interface sortante sur l’objet contenu.

*punkSink*<br/>
Pointeur vers l' `IUnknown` interface de l’objet récepteur à connecter au point de connexion spécifié par *iidSink* sur l’objet contenu après la création réussie de l’objet contenu.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

`AtlAxCreateControlEx` est semblable à [AtlAxCreateControl](#atlaxcreatecontrol) , mais vous permet également de recevoir un pointeur d’interface vers le contrôle nouvellement créé et de configurer un récepteur d’événements pour recevoir des événements déclenchés par le contrôle.

Pour créer un contrôle ActiveX sous licence, consultez [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex).

## <a name="atlaxcreatecontrollic"></a><a name="atlaxcreatecontrollic"></a> AtlAxCreateControlLic

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

*lpszName*<br/>
Pointeur vers une chaîne à passer au contrôle. Doit être mis en forme de l’une des manières suivantes :

- Un ProgID tel que `"MSCAL.Calendar.7"`

- Un CLSID tel que `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Une URL telle que `"<https://www.microsoft.com>"`

- Référence à un document actif tel que `"file://\\\Documents\MyDoc.doc"`

- Un fragment de code HTML tel que `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` doit précéder le fragment HTML afin qu’il soit désigné comme un flux MSHTML.

*hWnd*<br/>
Handle de la fenêtre à laquelle le contrôle sera attaché.

*pStream*<br/>
Pointeur vers un flux utilisé pour initialiser les propriétés du contrôle. Sa valeur peut être NULL.

*ppUnkContainer*<br/>
Adresse d’un pointeur qui recevra le `IUnknown` du conteneur. Sa valeur peut être NULL.

*bstrLic*<br/>
BSTR contenant la licence du contrôle.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, consultez [Hébergement de contrôles ActiveX à l’aide d’ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `AtlAxCreateControlLic` .

## <a name="atlaxcreatecontrollicex"></a><a name="atlaxcreatecontrollicex"></a> AtlAxCreateControlLicEx

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

*lpszName*<br/>
Pointeur vers une chaîne à passer au contrôle. Doit être mis en forme de l’une des manières suivantes :

- Un ProgID tel que `"MSCAL.Calendar.7"`

- Un CLSID tel que `"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- Une URL telle que `"<https://www.microsoft.com>"`

- Référence à un document actif tel que `"file://\\\Documents\MyDoc.doc"`

- Un fragment de code HTML tel que `"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"` doit précéder le fragment HTML afin qu’il soit désigné comme un flux MSHTML.

*hWnd*<br/>
Handle de la fenêtre à laquelle le contrôle sera attaché.

*pStream*<br/>
Pointeur vers un flux utilisé pour initialiser les propriétés du contrôle. Sa valeur peut être NULL.

*ppUnkContainer*<br/>
Adresse d’un pointeur qui recevra le `IUnknown` du conteneur. Sa valeur peut être NULL.

*ppUnkControl*<br/>
à Adresse d’un pointeur qui recevra le `IUnknown` du contrôle créé. Sa valeur peut être NULL.

*iidSink*<br/>
Identificateur d’interface d’une interface sortante sur l’objet contenu.

*punkSink*<br/>
Pointeur vers l' `IUnknown` interface de l’objet récepteur à connecter au point de connexion spécifié par *iidSink* sur l’objet contenu après la création réussie de l’objet contenu.

*bstrLic*<br/>
BSTR contenant la licence du contrôle.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

`AtlAxCreateControlLicEx` est semblable à [AtlAxCreateControlLic](#atlaxcreatecontrollic) , mais vous permet également de recevoir un pointeur d’interface vers le contrôle nouvellement créé et de configurer un récepteur d’événements pour recevoir des événements déclenchés par le contrôle.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, consultez [Hébergement de contrôles ActiveX à l’aide d’ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `AtlAxCreateControlLicEx` .

## <a name="atlaxattachcontrol"></a><a name="atlaxattachcontrol"></a> AtlAxAttachControl

Joint un contrôle précédemment créé à la fenêtre spécifiée.

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>Paramètres

*pControl*<br/>
dans Pointeur vers le `IUnknown` du contrôle.

*hWnd*<br/>
dans Handle de la fenêtre qui hébergera le contrôle.

*ppUnkContainer*<br/>
à Pointeur vers un pointeur vers le `IUnknown` de l’objet conteneur.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Utilisez [AtlAxCreateControlEx](#atlaxcreatecontrolex) et [AtlAxCreateControl](#atlaxcreatecontrol) pour créer et attacher simultanément un contrôle.

> [!NOTE]
> L’objet de contrôle attaché doit être correctement initialisé avant d’appeler `AtlAxAttachControl` .

## <a name="atlaxgethost"></a><a name="atlaxgethost"></a> AtlAxGetHost

Obtient un pointeur d'interface direct vers le conteneur d'une fenêtre spécifique (le cas échéant), en fonction de son handle.

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
dans Handle de la fenêtre qui héberge le contrôle.

*p*<br/>
à `IUnknown` Du conteneur du contrôle.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

## <a name="atlaxgetcontrol"></a><a name="atlaxgetcontrol"></a> AtlAxGetControl

Obtient un pointeur d'interface direct vers le contrôle contenu dans une fenêtre spécifique en fonction de son handle.

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
dans Handle de la fenêtre qui héberge le contrôle.

*p*<br/>
à `IUnknown` Du contrôle hébergé.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

## <a name="atlsetchildsite"></a><a name="atlsetchildsite"></a> AtlSetChildSite

Appelez cette fonction pour définir le site de l’objet enfant sur le `IUnknown` de l’objet parent.

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>Paramètres

*punkChild*<br/>
dans Pointeur vers l' `IUnknown` interface de l’enfant.

*punkParent*<br/>
dans Pointeur vers l' `IUnknown` interface du parent.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="atlaxwininit"></a><a name="atlaxwininit"></a> AtlAxWinInit

Cette fonction initialise le code d’hébergement du contrôle de la bibliothèque ATL en inscrivant les classes de fenêtres **« AtlAxWin80 »** et **« AtlAxWinLic80 »** , ainsi que quelques messages de fenêtre personnalisés.

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’initialisation du code d’hébergement du contrôle a réussi ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette fonction doit être appelée avant d’utiliser l’API d’hébergement de contrôle ATL. Suite à un appel à cette fonction, la classe de fenêtre **« AtlAxWin »** peut être utilisée dans les appels à [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) ou [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw), comme décrit dans la SDK Windows.

## <a name="atlaxwinterm"></a><a name="atlaxwinterm"></a> AtlAxWinTerm

Cette fonction annule l’initialisation du code d’hébergement du contrôle ATL en annulant l’inscription des classes de fenêtres **« AtlAxWin80 »** et **« AtlAxWinLic80 »** .

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne toujours la valeur TRUE.

### <a name="remarks"></a>Notes

Cette fonction appelle simplement [UnregisterClass](/windows/win32/api/winuser/nf-winuser-unregisterclassw) comme décrit dans le SDK Windows.

Appelez cette fonction pour nettoyer une fois que toutes les fenêtres hôtes existantes ont été détruites si vous avez appelé [AtlAxWinInit](#atlaxwininit) et que vous n’avez plus besoin de créer des fenêtres hôtes. Si vous n’appelez pas cette fonction, la classe de fenêtre sera désinscrite automatiquement lorsque le processus se terminera.

## <a name="atlgetobjectsourceinterface"></a><a name="atlgetobjectsourceinterface"></a> AtlGetObjectSourceInterface

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

*punkObj*<br/>
dans Pointeur vers l’objet pour lequel les informations doivent être retournées.

*plibid*<br/>
à Pointeur vers le LIBID de la bibliothèque de types contenant la définition de l’interface source.

*piid*<br/>
à Pointeur vers l’ID d’interface de l’interface source par défaut de l’objet.

*pdwMajor*<br/>
à Pointeur vers le numéro de version principale de la bibliothèque de types contenant la définition de l’interface source.

*pdwMinor*<br/>
à Pointeur vers le numéro de version secondaire de la bibliothèque de types contenant la définition de l’interface source.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

`AtlGetObjectSourceInterface` peut vous fournir l’ID d’interface de l’interface source par défaut, ainsi que le LIBID et les numéros de version majeure et mineure de la bibliothèque de types décrivant cette interface.

> [!NOTE]
> Pour que cette fonction récupère correctement les informations demandées, l’objet représenté par *punkObj* doit implémenter `IDispatch` (et retourner des informations de type via `IDispatch::GetTypeInfo` ) plus il doit également implémenter `IProvideClassInfo2` ou `IPersist` . Les informations de type de l’interface source doivent se trouver dans la même bibliothèque de types que les informations de type pour `IDispatch` .

### <a name="example"></a>Exemple

L’exemple ci-dessous montre comment vous pouvez définir une classe de récepteur d’événements, `CEasySink` , qui réduit le nombre d’arguments de modèle que vous pouvez passer à `IDispEventImpl` la classe Bare Essentials. `EasyAdvise` et `EasyUnadvise` utilisent `AtlGetObjectSourceInterface` pour initialiser les membres [IDispEventImpl](../../atl/reference/idispeventimpl-class.md) avant d’appeler [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) ou [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise).

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)<br/>
[Macros de contrôle composite](../../atl/reference/composite-control-macros.md)
