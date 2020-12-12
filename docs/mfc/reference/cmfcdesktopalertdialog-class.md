---
description: 'En savoir plus sur : classe CMFCDesktopAlertDialog'
title: CMFCDesktopAlertDialog, classe
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertDialog
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::CreateFromParams
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::GetDlgSize
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::HasFocus
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::PreTranslateMessage
helpviewer_keywords:
- CMFCDesktopAlertDialog [MFC], CreateFromParams
- CMFCDesktopAlertDialog [MFC], GetDlgSize
- CMFCDesktopAlertDialog [MFC], HasFocus
- CMFCDesktopAlertDialog [MFC], PreTranslateMessage
ms.assetid: a53c60aa-9607-485b-b826-ec64962075f6
ms.openlocfilehash: 327ec72b1e58d90e768f51c083ff9545f24f6f0b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193186"
---
# <a name="cmfcdesktopalertdialog-class"></a>CMFCDesktopAlertDialog, classe

La `CMFCDesktopAlertDialog` classe est utilisée conjointement avec la [classe CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md) pour afficher une boîte de dialogue personnalisée dans une fenêtre contextuelle.

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCDesktopAlertDialog : public CDialogEx
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCDesktopAlertDialog::CreateFromParams](#createfromparams)||
|[CMFCDesktopAlertDialog::GetDlgSize](#getdlgsize)||
|[CMFCDesktopAlertDialog::HasFocus](#hasfocus)||
|[CMFCDesktopAlertDialog::PreTranslateMessage](#pretranslatemessage)|(Substitue `CDialogEx::PreTranslateMessage`.)|

### <a name="remarks"></a>Notes

Pour afficher une boîte de dialogue personnalisé dans une fenêtre contextuelle, procédez comme suit :

1. Dérivez une classe de `CMFCDesktopAlertDialog`.

1. Créez un modèle de boîte de dialogue enfant dans les ressources du projet.

1. Appelez [CMFCDesktopAlertWnd :: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) avec l’ID de ressource du modèle de boîte de dialogue et un pointeur vers les informations de classe d’exécution de la classe dérivée en tant que paramètres.

1. Programmez la boîte de dialogue personnalisée de sorte qu'elle traite toutes les notifications en provenance des contrôles hébergés ou programmez les contrôles hébergés de sorte qu'ils traitent directement ces notifications.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxDesktopAlertDialog. h

## <a name="cmfcdesktopalertdialogcreatefromparams"></a><a name="createfromparams"></a> CMFCDesktopAlertDialog::CreateFromParams

```
BOOL CreateFromParams(
    CMFCDesktopAlertWndInfo& params,
    CMFCDesktopAlertWnd* pParent);
```

### <a name="parameters"></a>Paramètres

dans *paramètres*<br/>

dans *pParent*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertdialoggetdlgsize"></a><a name="getdlgsize"></a> CMFCDesktopAlertDialog::GetDlgSize

```
CSize GetDlgSize();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertdialoghasfocus"></a><a name="hasfocus"></a> CMFCDesktopAlertDialog :: HasFocus

```
BOOL HasFocus() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertdialogpretranslatemessage"></a><a name="pretranslatemessage"></a> CMFCDesktopAlertDialog ::P reTranslateMessage

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Paramètres

dans *PMSG*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd, classe](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWndInfo, classe](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[Cdialogex,, classe](../../mfc/reference/cdialogex-class.md)
