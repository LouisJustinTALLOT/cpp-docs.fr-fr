---
title: Cmfctabtooltipinfo, Structure
ms.date: 11/04/2016
f1_keywords:
- CMFCTabToolTipInfo
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
ms.openlocfilehash: b785754a7970573c42fcc1d0736541416f522c9a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429165"
---
# <a name="cmfctabtooltipinfo-structure"></a>Cmfctabtooltipinfo, Structure

Cette structure fournit des informations sur l’onglet MDI qui pointe sur l’utilisateur.

## <a name="syntax"></a>Syntaxe

```
struct CMFCTabToolTipInfo
```

## <a name="members"></a>Membres

### <a name="data-members"></a>Membres de données

|Name|Description|
|----------|-----------------|
|[CMFCTabToolTipInfo::m_nTabIndex](#m_ntabindex)|Spécifie l’index du contrôle onglet.|
|[CMFCTabToolTipInfo::m_pTabWnd](#m_ptabwnd)|Pointeur vers le contrôle onglet.|
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|Le texte info-bulle.|

## <a name="remarks"></a>Notes

Un pointeur vers un `CMFCTabToolTipInfo` structure est passée en tant que paramètre du message AFX_WM_ON_GET_TAB_TOOLTIP. Ce message est généré lorsque les onglets MDI sont activés et l’utilisateur pointe sur un contrôle onglet.

## <a name="example"></a>Exemple

L’exemple suivant montre comment `CMFCTabToolTipInfo` est utilisé dans le [exemple MDITabsDemo : MFC avec onglet MDI Application](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxbasetabctrl.h

##  <a name="m_ntabindex"></a>  CMFCTabToolTipInfo::m_nTabIndex

Spécifie l’index du contrôle onglet.

```
int m_nTabIndex;
```

### <a name="remarks"></a>Notes

Index de l’onglet sur laquelle l’utilisateur pointe.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `m_nTabIndex` est utilisé dans le [exemple MDITabsDemo : MFC avec onglet MDI Application](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_ptabwnd"></a>  CMFCTabToolTipInfo::m_pTabWnd

Pointeur vers le contrôle onglet.

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>Exemple

L’exemple suivant montre comment `m_pTabWnd` est utilisé dans le [exemple MDITabsDemo : MFC avec onglet MDI Application](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_strtext"></a>  CMFCTabToolTipInfo::m_strText

Le texte info-bulle.

```
CString m_strText;
```

### <a name="remarks"></a>Notes

Si la chaîne est vide, l’info-bulle n’est pas affichée.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `m_strText` est utilisé dans le [exemple MDITabsDemo : MFC avec onglet MDI Application](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
