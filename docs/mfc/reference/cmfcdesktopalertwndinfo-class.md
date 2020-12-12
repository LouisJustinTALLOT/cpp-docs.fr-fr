---
description: 'En savoir plus sur : classe CMFCDesktopAlertWndInfo'
title: CMFCDesktopAlertWndInfo, classe
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_hIcon
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_nURLCmdID
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strText
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strURL
helpviewer_keywords:
- CMFCDesktopAlertWndInfo [MFC], m_hIcon
- CMFCDesktopAlertWndInfo [MFC], m_nURLCmdID
- CMFCDesktopAlertWndInfo [MFC], m_strText
- CMFCDesktopAlertWndInfo [MFC], m_strURL
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
ms.openlocfilehash: 1c23e5b890e892df9bccce51542f2d36b3d6f7d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250684"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>CMFCDesktopAlertWndInfo, classe

La `CMFCDesktopAlertWndInfo` classe est utilisée avec la [classe CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md). Elle spécifie les contrôles qui sont affichés si la fenêtre d'alerte sur le Bureau s'affiche.

## <a name="syntax"></a>Syntaxe

```
class CMFCDesktopAlertWndInfo
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo :: Operator =](#operator_eq)||

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo :: m_hIcon](#m_hicon)|Handle de l’icône qui est affichée.|
|[CMFCDesktopAlertWndInfo :: m_nURLCmdID](#m_nurlcmdid)|ID de commande associé à un lien dans la fenêtre d’alerte sur le bureau.|
|[CMFCDesktopAlertWndInfo :: m_strText](#m_strtext)|Texte affiché dans la fenêtre d’alerte sur le bureau.|
|[CMFCDesktopAlertWndInfo :: m_strURL](#m_strurl)|Lien affiché dans la fenêtre d’alerte sur le bureau.|

## <a name="remarks"></a>Notes

La `CMFCDesktopAlertWndInfo` classe est passée à la méthode [CMFCDesktopAlertWnd :: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) pour spécifier les éléments affichés dans la boîte de dialogue par défaut de la fenêtre d’alerte sur le bureau. La boîte de dialogue par défaut peut contenir trois éléments :

- Icône définie en appelant [CMFCDesktopAlertWndInfo :: m_hIcon](#m_hicon).

- Une étiquette, ou un message texte, qui est défini en appelant [CMFCDesktopAlertWndInfo :: m_strText](#m_strtext).

- Lien défini par l’appel de [CMFCDesktopAlertWndInfo :: m_strURL](#m_strurl). Pour définir la commande qui est exécutée lorsque l’utilisateur clique sur le lien, appelez [CMFCDesktopAlertWndInfo :: m_nURLCmdID](#m_nurlcmdid).

Si la boîte de dialogue par défaut n’est pas suffisante, vous pouvez créer une boîte de dialogue personnalisée et la passer à la méthode [CMFCDesktopAlertWnd :: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) au lieu d’utiliser cette classe. Pour plus d’informations, consultez [CMFCDesktopAlertDialog, classe](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser les différents membres de la `CMFCDesktopAlertWndInfo` classe. L’exemple montre comment définir le handle sur l’icône qui s’affiche, le texte affiché dans la fenêtre d’alerte sur le bureau, le lien affiché dans la fenêtre d’alerte sur le bureau et l’ID de commande associé à un lien dans la fenêtre d’alerte sur le bureau. Cet exemple fait partie de l' [exemple de démonstration](../../overview/visual-cpp-samples.md)de l’alerte sur le bureau.

[!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxDesktopAlertDialog. h

## <a name="cmfcdesktopalertwndinfooperator"></a><a name="operator_eq"></a> CMFCDesktopAlertWndInfo :: Operator =

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```

### <a name="parameters"></a>Paramètres

dans *src*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertwndinfom_hicon"></a><a name="m_hicon"></a> CMFCDesktopAlertWndInfo :: m_hIcon

Handle de l’icône qui est affichée.

```
HICON m_hIcon;
```

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertwndinfom_nurlcmdid"></a><a name="m_nurlcmdid"></a> CMFCDesktopAlertWndInfo :: m_nURLCmdID

ID de commande associé à un lien dans la fenêtre d’alerte sur le bureau.

```
UINT m_nURLCmdID;
```

### <a name="remarks"></a>Notes

L’ID de commande est envoyé au propriétaire de la fenêtre contextuelle lorsque l’utilisateur clique sur le lien spécifié par [CMFCDesktopAlertWndInfo :: m_strURL](#m_strurl).

## <a name="cmfcdesktopalertwndinfom_strtext"></a><a name="m_strtext"></a> CMFCDesktopAlertWndInfo :: m_strText

Texte affiché dans la fenêtre d’alerte sur le bureau.

```
CString m_strText;
```

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertwndinfom_strurl"></a><a name="m_strurl"></a> CMFCDesktopAlertWndInfo :: m_strURL

Lien affiché dans la fenêtre d’alerte sur le bureau.

```
CString m_strURL;
```

### <a name="remarks"></a>Notes

Lorsque l’utilisateur clique sur le lien, la commande avec l’ID de commande [CMFCDesktopAlertWndInfo :: m_nURLCmdID](#m_nurlcmdid) est envoyée au propriétaire de la fenêtre contextuelle.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd, classe](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWnd :: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)<br/>
[CMFCDesktopAlertDialog, classe](../../mfc/reference/cmfcdesktopalertdialog-class.md)
