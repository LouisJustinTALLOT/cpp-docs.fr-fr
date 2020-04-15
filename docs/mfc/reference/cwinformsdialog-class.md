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
ms.openlocfilehash: 3772033df59e065cedca61012cd479c812cf5b66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367427"
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
Le contrôle utilisateur .NET Framework à afficher dans l’application MFC.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|Construit un objet `CWinFormsDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWinFormsDialog::GetControl](#getcontrol)|Récupère une référence au contrôle de l’utilisateur Windows Forms.|
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|Récupère une poignée de fenêtre sur le contrôle de l’utilisateur Windows Forms.|
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|Initialise la boîte de dialogue MFC en créant et en hébergeant un contrôle utilisateur Windows Forms sur elle.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom||
|----------|-|
|[CWinFormsDialog::opérateur -&gt;](#operator_-_gt)|Remplace [CWinFormsDialog::GetControl](#getcontrol) dans les expressions.|
|[CWinFormsDialog::opérateur TManagedControl](#operator-tmanagedcontrol-hat)|Lance un type comme référence à un contrôle utilisateur Windows Forms.|

## <a name="remarks"></a>Notes

`CWinFormsDialog`est un emballage pour une classe de dialogue MFC ( [CDialog](../../mfc/reference/cdialog-class.md)) qui héberge un contrôle utilisateur Windows Forms. Cela permet l’affichage de contrôles .NET Framework sur une boîte de dialogue MFC modale ou sans mode.

Pour plus d’informations sur l’utilisation des formulaires Windows, voir [à l’aide d’un contrôle de l’utilisateur de formulaire Windows dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) et [hébergez un contrôle de l’utilisateur de formulaire Windows comme une boîte de dialogue MFC](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).

## <a name="requirements"></a>Spécifications

**En-tête:** afxwinforms.h

## <a name="cwinformsdialogcwinformsdialog"></a><a name="cwinformsdialog"></a>CWinFormsDialog::CWinFormsDialog

Construit un objet `CWinFormsDialog`.

```
CWinFormsDialog(UINT nIDTemplate = IDD);
```

### <a name="parameters"></a>Paramètres

*nIDTemplate (en)*<br/>
Contient l’ID d’une ressource de modèle de boîte de dialogue. Utilisez l’éditeur de dialogue pour créer le modèle de dialogue et le stocker dans le fichier de script de ressources de l’application. Pour plus d’informations sur les modèles de dialogue, voir [CDialog Class](../../mfc/reference/cdialog-class.md).

## <a name="cwinformsdialoggetcontrol"></a><a name="getcontrol"></a>CWinFormsDialog::GetControl

Récupère une référence au contrôle de l’utilisateur Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Valeur de retour

Renvoie une référence au contrôle des formulaires Windows dans la boîte de dialogue MFC.

## <a name="cwinformsdialoggetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinFormsDialog::GetControlHandle

Récupère une poignée de fenêtre sur le contrôle de l’utilisateur Windows Forms.

```
inline HWND GetControlHandle() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une poignée de fenêtre au contrôle de l’utilisateur Windows Forms.

## <a name="cwinformsdialogoninitdialog"></a><a name="oninitdialog"></a>CWinFormsDialog::OnInitDialog

Initialise la boîte de dialogue MFC en créant et en hébergeant un contrôle utilisateur Windows Forms sur elle.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valeur de retour

Une valeur Boolean qui précise si l’application a défini l’accent sur l’entrée à l’un des contrôles dans la boîte de dialogue. Si `OnInitDialog` les retours non zéro, Windows définit la mise au point de l’entrée au premier contrôle dans la boîte de dialogue. Cette méthode ne peut retourner 0 que si l’application a explicitement défini l’accent sur l’entrée à l’un des contrôles dans la boîte de dialogue.

### <a name="remarks"></a>Notes

Lorsque la boîte de dialogue MFC est créée (en utilisant la [méthode Create](../../mfc/reference/cdialog-class.md#create), [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect), ou [DoModal](../../mfc/reference/cdialog-class.md#domodal) héritée de [CDialog](../../mfc/reference/cdialog-class.md)), un message WM_INITDIALOG est envoyé et cette méthode est appelée. Il crée une instance d’un contrôle des formulaires Windows sur la boîte de dialogue et ajuste la taille de la boîte de dialogue pour tenir compte de la taille du contrôle de l’utilisateur. Ensuite, il accueille le nouveau contrôle dans la boîte de dialogue MFC.

Remplacer cette fonction de membre si vous avez besoin d’effectuer un traitement spécial lorsque la boîte de dialogue est paralysée. Pour plus d’informations sur l’utilisation de cette méthode, voir [CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).

## <a name="cwinformsdialogoperator--gt"></a><a name="operator_-_gt"></a>CWinFormsDialog::opérateur -&gt;

Remplace [CWinFormsDialog::GetControl](#getcontrol) dans les expressions.

```
inline TManagedControl^  operator->() const throw();
```

### <a name="remarks"></a>Notes

Cet opérateur fournit une syntaxe pratique qui remplace dans les `GetControl` expressions.

Pour plus d’informations sur l’utilisation des formulaires Windows, voir [à l’aide d’un contrôle utilisateur de formulaire Windows dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformsdialogoperator-tmanagedcontrol"></a><a name="operator-tmanagedcontrol-hat"></a>CWinFormsDialog::opérateur TManagedControl

Lance un type comme référence à un contrôle utilisateur Windows Forms.

```
inline operator TManagedControl^() const throw();
```

### <a name="remarks"></a>Notes

Cet opérateur présente un type comme référence à un contrôle Windows Forms. Il est utilisé pour `CWinFormsDialog<TManagedControl>` passer une boîte de dialogue aux fonctions qui acceptent un pointeur à un objet de contrôle utilisateur Windows Forms.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CWinFormsView, classe](../../mfc/reference/cwinformsview-class.md)<br/>
[Classe CDialog](../../mfc/reference/cdialog-class.md)
