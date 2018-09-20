---
title: Cmfcdesktopalertwndinfo, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_hIcon
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_nURLCmdID
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strText
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strURL
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWndInfo [MFC], m_hIcon
- CMFCDesktopAlertWndInfo [MFC], m_nURLCmdID
- CMFCDesktopAlertWndInfo [MFC], m_strText
- CMFCDesktopAlertWndInfo [MFC], m_strURL
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5adc1e5a5df7a1c14a3af1e0f36718806497b682
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443812"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>Cmfcdesktopalertwndinfo, classe

Le `CMFCDesktopAlertWndInfo` classe est utilisée avec la [cmfcdesktopalertwnd, classe](../../mfc/reference/cmfcdesktopalertwnd-class.md). Elle spécifie les contrôles qui sont affichés si la fenêtre d'alerte sur le Bureau s'affiche.

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
|[CMFCDesktopAlertWndInfo::operator =](#operator_eq)||

### <a name="data-members"></a>Membres de données

|Name|Description|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)|Handle vers l’icône qui s’affiche.|
|[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)|L’ID de commande associé à un lien dans la fenêtre Bureau de l’alerte.|
|[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)|Le texte qui s’affiche dans la fenêtre Bureau de l’alerte.|
|[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)|Le lien s’affiche dans la fenêtre Bureau de l’alerte.|

## <a name="remarks"></a>Notes

Le `CMFCDesktopAlertWndInfo` classe est passée à la [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) méthode pour spécifier les éléments qui sont affichés dans la boîte de dialogue par défaut de la fenêtre Bureau de l’alerte. La boîte de dialogue par défaut peut contenir trois éléments :

- Une icône qui est définie en appelant [CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon).

- Une étiquette, ou un message texte, qui est défini en appelant [CMFCDesktopAlertWndInfo::m_strText](#m_strtext).

- Un lien, qui est défini en appelant [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl). Pour définir la commande est exécutée lorsque l’utilisateur clique sur le lien, appelez [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid).

Si la boîte de dialogue par défaut n’est pas suffisante, vous pouvez créer une boîte de dialogue personnalisée et transmettez-le à la [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) méthode au lieu d’utiliser cette classe. Pour plus d’informations, consultez [cmfcdesktopalertdialog, classe](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser les différents membres dans la `CMFCDesktopAlertWndInfo` classe. L’exemple montre comment définir le handle de l’icône qui s’affiche, le texte qui s’affiche dans la fenêtre d’alerte de bureau, le lien qui s’affiche dans la fenêtre d’alerte de bureau et l’ID de commande qui est associé à un lien dans la fenêtre Bureau de l’alerte. Cet exemple fait partie de la [exemple de démonstration alerte Desktop](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxDesktopAlertDialog.h

##  <a name="operator_eq"></a>  CMFCDesktopAlertWndInfo::operator =

Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.

```
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```

### <a name="parameters"></a>Paramètres

[in] *src*

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="m_hicon"></a>  CMFCDesktopAlertWndInfo::m_hIcon

Handle vers l’icône qui s’affiche.

```
HICON m_hIcon;
```

### <a name="remarks"></a>Notes

##  <a name="m_nurlcmdid"></a>  CMFCDesktopAlertWndInfo::m_nURLCmdID

L’ID de commande associé à un lien dans la fenêtre Bureau de l’alerte.

```
UINT m_nURLCmdID;
```

### <a name="remarks"></a>Notes

L’ID de commande est envoyé au propriétaire de la fenêtre contextuelle lorsque l’utilisateur clique sur le lien spécifié par [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl).

##  <a name="m_strtext"></a>  CMFCDesktopAlertWndInfo::m_strText

Le texte qui s’affiche dans la fenêtre Bureau de l’alerte.

```
CString m_strText;
```

### <a name="remarks"></a>Notes

##  <a name="m_strurl"></a>  CMFCDesktopAlertWndInfo::m_strURL

Le lien s’affiche dans la fenêtre Bureau de l’alerte.

```
CString m_strURL;
```

### <a name="remarks"></a>Notes

Lorsque l’utilisateur clique sur le lien, la commande qui a le [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid) ID de commande sera envoyé au propriétaire de la fenêtre contextuelle.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd, classe](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)<br/>
[CMFCDesktopAlertDialog, classe](../../mfc/reference/cmfcdesktopalertdialog-class.md)
