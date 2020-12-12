---
description: 'En savoir plus sur : structure CMFCTabToolTipInfo'
title: CMFCTabToolTipInfo, structure
ms.date: 11/04/2016
f1_keywords:
- CMFCTabToolTipInfo
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
ms.openlocfilehash: ce9e9f4fdbcf367921e7f0559a4d04e66f4303dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164066"
---
# <a name="cmfctabtooltipinfo-structure"></a>CMFCTabToolTipInfo, structure

Cette structure fournit des informations sur l’onglet MDI sur lequel l’utilisateur pointe.

## <a name="syntax"></a>Syntaxe

```
struct CMFCTabToolTipInfo
```

## <a name="members"></a>Membres

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCTabToolTipInfo :: m_nTabIndex](#m_ntabindex)|Spécifie l’index du contrôle onglet.|
|[CMFCTabToolTipInfo :: m_pTabWnd](#m_ptabwnd)|Pointeur vers le contrôle onglet.|
|[CMFCTabToolTipInfo :: m_strText](#m_strtext)|Texte info-bulle.|

## <a name="remarks"></a>Notes

Un pointeur vers une `CMFCTabToolTipInfo` structure est passé en tant que paramètre du message AFX_WM_ON_GET_TAB_TOOLTIP. Ce message est généré lorsque les onglets MDI sont activés et que l’utilisateur pointe sur un contrôle Tab.

## <a name="example"></a>Exemple

L’exemple suivant montre comment `CMFCTabToolTipInfo` est utilisé dans l' [exemple MDITabsDemo : application MDI avec onglets MFC](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxbasetabctrl.h

## <a name="cmfctabtooltipinfom_ntabindex"></a><a name="m_ntabindex"></a> CMFCTabToolTipInfo :: m_nTabIndex

Spécifie l’index du contrôle onglet.

```
int m_nTabIndex;
```

### <a name="remarks"></a>Notes

Index de l’onglet sur lequel l’utilisateur pointe.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `m_nTabIndex` est utilisé dans l' [exemple MDITabsDemo : application MDI avec onglets MFC](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_ptabwnd"></a><a name="m_ptabwnd"></a> CMFCTabToolTipInfo :: m_pTabWnd

Pointeur vers le contrôle onglet.

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>Exemple

L’exemple suivant montre comment `m_pTabWnd` est utilisé dans l' [exemple MDITabsDemo : application MDI avec onglets MFC](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_strtext"></a><a name="m_strtext"></a> CMFCTabToolTipInfo :: m_strText

Texte info-bulle.

```
CString m_strText;
```

### <a name="remarks"></a>Notes

Si la chaîne est vide, l’info-bulle n’est pas affichée.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `m_strText` est utilisé dans l' [exemple MDITabsDemo : application MDI avec onglets MFC](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
