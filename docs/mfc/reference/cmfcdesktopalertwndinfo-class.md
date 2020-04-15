---
title: Classe CMFCDesktopAlertWndInfo
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
ms.openlocfilehash: f51c1b75e0c096a34b190e36e097aaca4109b5f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367587"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>Classe CMFCDesktopAlertWndInfo

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
|[CMFCDesktopAlertWndInfo::opérateur](#operator_eq)||

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo:m_hIcon](#m_hicon)|Une poignée à l’icône qui s’affiche.|
|[CMFCDesktopAlertWndInfo:m_nURLCmdID](#m_nurlcmdid)|L’ID de commande associé à un lien sur la fenêtre d’alerte de bureau.|
|[CMFCDesktopAlertWndInfo:m_strText](#m_strtext)|Le texte qui s’affiche sur la fenêtre d’alerte de bureau.|
|[CMFCDesktopAlertWndInfo:m_strURL](#m_strurl)|Le lien qui s’affiche sur la fenêtre d’alerte de bureau.|

## <a name="remarks"></a>Notes

La `CMFCDesktopAlertWndInfo` classe est transmise au [CMFCDesktopAlertWnd : : Créer](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) la méthode pour spécifier les éléments qui s’affichent sur le dialogue par défaut de la fenêtre d’alerte de bureau. Le dialogue par défaut peut contenir trois éléments :

- Une icône, qui est définie en appelant [CMFCDesktopAlertWndInfo:m_hIcon](#m_hicon).

- Une étiquette, ou message texte, qui est défini en appelant [CMFCDesktopAlertWndInfo:m_strText](#m_strtext).

- Un lien, qui est défini en appelant [CMFCDesktopAlertWndInfo:m_strURL](#m_strurl). Pour définir la commande qui est exécutée lorsque le lien est cliqué, appelez [CMFCDesktopAlertWndInfo:m_nURLCmdID](#m_nurlcmdid).

Si le dialogue par défaut n’est pas suffisant, vous pouvez créer un dialogue personnalisé et le transmettre au [CMFCDesktopAlertWnd : : Créez](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) la méthode au lieu d’utiliser cette classe. Pour plus d’informations, voir [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser `CMFCDesktopAlertWndInfo` divers membres de la classe. L’exemple montre comment définir la poignée à l’icône qui s’affiche, le texte qui s’affiche sur la fenêtre d’alerte de bureau, le lien qui s’affiche sur la fenêtre d’alerte de bureau, et l’ID de commande qui est associé à un lien sur la fenêtre d’alerte de bureau. Cet exemple fait partie de [l’échantillon de démonstration d’alerte de bureau](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxDesktopAlertDialog.h

## <a name="cmfcdesktopalertwndinfooperator"></a><a name="operator_eq"></a>CMFCDesktopAlertWndInfo::opérateur

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```

### <a name="parameters"></a>Paramètres

[dans] *src*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertwndinfom_hicon"></a><a name="m_hicon"></a>CMFCDesktopAlertWndInfo:m_hIcon

Une poignée à l’icône qui s’affiche.

```
HICON m_hIcon;
```

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertwndinfom_nurlcmdid"></a><a name="m_nurlcmdid"></a>CMFCDesktopAlertWndInfo:m_nURLCmdID

L’ID de commande associé à un lien sur la fenêtre d’alerte de bureau.

```
UINT m_nURLCmdID;
```

### <a name="remarks"></a>Notes

L’ID de commande est envoyé au propriétaire de la fenêtre popup lorsque l’utilisateur clique sur le lien spécifié par [CMFCDesktopAlertWndInfo:m_strURL](#m_strurl).

## <a name="cmfcdesktopalertwndinfom_strtext"></a><a name="m_strtext"></a>CMFCDesktopAlertWndInfo:m_strText

Le texte qui s’affiche sur la fenêtre d’alerte de bureau.

```
CString m_strText;
```

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertwndinfom_strurl"></a><a name="m_strurl"></a>CMFCDesktopAlertWndInfo:m_strURL

Le lien qui s’affiche sur la fenêtre d’alerte de bureau.

```
CString m_strURL;
```

### <a name="remarks"></a>Notes

Lorsque l’utilisateur clique sur le lien, la commande qui a le [CMFCDesktopAlertWndInfo::m_nURLCmdID’ID](#m_nurlcmdid) de commande sera envoyé au propriétaire de la fenêtre pop-up.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWnd::Créer](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)<br/>
[CMFCDesktopAlertDialog, classe](../../mfc/reference/cmfcdesktopalertdialog-class.md)
