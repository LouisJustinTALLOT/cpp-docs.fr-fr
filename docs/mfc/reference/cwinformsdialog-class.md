---
title: CWinFormsDialog, classe
ms.date: 03/27/2019
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
ms.openlocfilehash: a25823982b9276309e99a2a26cef8d6fe2e764bd
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040663"
---
# <a name="cwinformsdialog-class"></a>CWinFormsDialog, classe

Wrapper pour une classe de boîte de dialogue MFC qui héberge un contrôle utilisateur Windows Forms.

## <a name="syntax"></a>Syntaxe

```
template <typename TManagedControl>
class CWinFormsDialog :
    public CDialog
```

#### <a name="parameters"></a>Paramètres

*TManagedControl*<br/>
.NET Framework contrôle utilisateur à afficher dans l’application MFC.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CWinFormsDialog :: CWinFormsDialog](#cwinformsdialog)|Construit un objet `CWinFormsDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWinFormsDialog :: GetControl](#getcontrol)|Récupère une référence au contrôle utilisateur Windows Forms.|
|[CWinFormsDialog :: GetControlHandle](#getcontrolhandle)|Récupère un handle de fenêtre pour le contrôle utilisateur Windows Forms.|
|[CWinFormsDialog :: OnInitDialog](#oninitdialog)|Initialise la boîte de dialogue MFC en créant et en hébergeant un Windows Forms contrôle utilisateur sur celui-ci.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-|
|[CWinFormsDialog :: Operator-&gt;](#operator_-_gt)|Remplace [CWinFormsDialog :: GetControl](#getcontrol) dans les expressions.|
|[CWinFormsDialog :: Operator TManagedControl ^](#operator-tmanagedcontrol-hat)|Effectue un cast d’un type en une référence à un contrôle utilisateur Windows Forms.|

## <a name="remarks"></a>Remarques

`CWinFormsDialog` est un wrapper pour une classe de boîte de dialogue MFC ( [CDialog](../../mfc/reference/cdialog-class.md)) qui héberge un contrôle utilisateur Windows Forms. Cela permet l’affichage des contrôles de .NET Framework dans une boîte de dialogue MFC modale ou non modale.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) et [hébergement d’un contrôle utilisateur Windows Form en tant que boîte de dialogue MFC](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwinforms. h

## <a name="cwinformsdialogcwinformsdialog"></a><a name="cwinformsdialog"></a> CWinFormsDialog :: CWinFormsDialog

Construit un objet `CWinFormsDialog`.

```
CWinFormsDialog(UINT nIDTemplate = IDD);
```

### <a name="parameters"></a>Paramètres

*nIDTemplate*<br/>
Contient l’ID d’une ressource de modèle de boîte de dialogue. Utilisez l’éditeur de boîtes de dialogue pour créer le modèle de boîte de dialogue et le stocker dans le fichier de script de ressources de l’application. Pour plus d’informations sur les modèles de boîte de dialogue, consultez [CDialog, classe](../../mfc/reference/cdialog-class.md).

## <a name="cwinformsdialoggetcontrol"></a><a name="getcontrol"></a> CWinFormsDialog :: GetControl

Récupère une référence au contrôle utilisateur Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne une référence au contrôle Windows Forms dans la boîte de dialogue MFC.

## <a name="cwinformsdialoggetcontrolhandle"></a><a name="getcontrolhandle"></a> CWinFormsDialog :: GetControlHandle

Récupère un handle de fenêtre pour le contrôle utilisateur Windows Forms.

```
inline HWND GetControlHandle() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un handle de fenêtre pour le contrôle utilisateur Windows Forms.

## <a name="cwinformsdialogoninitdialog"></a><a name="oninitdialog"></a> CWinFormsDialog :: OnInitDialog

Initialise la boîte de dialogue MFC en créant et en hébergeant un Windows Forms contrôle utilisateur sur celui-ci.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valeur de retour

Valeur booléenne qui spécifie si l’application a défini le focus d’entrée sur l’un des contrôles de la boîte de dialogue. Si `OnInitDialog` retourne une valeur différente de zéro, Windows définit le focus d’entrée sur le premier contrôle de la boîte de dialogue. Cette méthode peut retourner 0 uniquement si l’application a explicitement défini le focus d’entrée sur l’un des contrôles de la boîte de dialogue.

### <a name="remarks"></a>Remarques

Quand la boîte de dialogue MFC est créée (à l’aide de la méthode [Create](../../mfc/reference/cdialog-class.md#create), [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect)ou [DoModal](../../mfc/reference/cdialog-class.md#domodal) héritée de [CDialog](../../mfc/reference/cdialog-class.md)), un message d’WM_INITDIALOG est envoyé et cette méthode est appelée. Elle crée une instance d’un contrôle Windows Forms sur la boîte de dialogue et ajuste la taille de la boîte de dialogue en fonction de la taille du contrôle utilisateur. Il héberge ensuite le nouveau contrôle dans la boîte de dialogue MFC.

Substituez cette fonction membre si vous devez effectuer un traitement spécial lorsque la boîte de dialogue est initialisée. Pour plus d’informations sur l’utilisation de cette méthode, consultez [CDialog :: OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).

## <a name="cwinformsdialogoperator--gt"></a><a name="operator_-_gt"></a> CWinFormsDialog :: Operator-&gt;

Remplace [CWinFormsDialog :: GetControl](#getcontrol) dans les expressions.

```
inline TManagedControl^  operator->() const throw();
```

### <a name="remarks"></a>Remarques

Cet opérateur fournit une syntaxe pratique qui remplace `GetControl` dans les expressions.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformsdialogoperator-tmanagedcontrol"></a><a name="operator-tmanagedcontrol-hat"></a> CWinFormsDialog :: Operator TManagedControl ^

Effectue un cast d’un type en une référence à un contrôle utilisateur Windows Forms.

```
inline operator TManagedControl^() const throw();
```

### <a name="remarks"></a>Remarques

Cet opérateur convertit un type en une référence à un contrôle Windows Forms. Il est utilisé pour passer une `CWinFormsDialog<TManagedControl>` boîte de dialogue aux fonctions qui acceptent un pointeur vers un objet de contrôle utilisateur Windows Forms.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CWinFormsView (classe)](../../mfc/reference/cwinformsview-class.md)<br/>
[CDialog (classe)](../../mfc/reference/cdialog-class.md)
