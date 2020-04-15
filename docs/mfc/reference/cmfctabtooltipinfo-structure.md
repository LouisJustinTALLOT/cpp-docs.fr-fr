---
title: CMFCTabToolTipInfo, structure
ms.date: 11/04/2016
f1_keywords:
- CMFCTabToolTipInfo
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
ms.openlocfilehash: a507d1e69b3524074e50fde0e87fc5ebb6e5ca03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367338"
---
# <a name="cmfctabtooltipinfo-structure"></a>CMFCTabToolTipInfo, structure

Cette structure fournit des informations sur l’onglet MDI que l’utilisateur survole.

## <a name="syntax"></a>Syntaxe

```
struct CMFCTabToolTipInfo
```

## <a name="members"></a>Membres

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCTabToolTipInfo:m_nTabIndex](#m_ntabindex)|Spécifie l’index du contrôle de l’onglet.|
|[CMFCTabToolTipInfo:m_pTabWnd](#m_ptabwnd)|Un pointeur pour le contrôle de l’onglet.|
|[CMFCTabToolTipInfo:m_strText](#m_strtext)|Texte info-bulle.|

## <a name="remarks"></a>Notes

Un pointeur `CMFCTabToolTipInfo` d’une structure est passé comme un paramètre du message AFX_WM_ON_GET_TAB_TOOLTIP. Ce message est généré lorsque les onglets MDI sont activés et que l’utilisateur plane au-dessus d’un contrôle de l’onglet.

## <a name="example"></a>Exemple

L’exemple suivant `CMFCTabToolTipInfo` montre comment est utilisé dans [l’échantillon MDITabsDemo: MFC Tabbed MDI Application](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxbasetabctrl.h

## <a name="cmfctabtooltipinfom_ntabindex"></a><a name="m_ntabindex"></a>CMFCTabToolTipInfo:m_nTabIndex

Spécifie l’index du contrôle de l’onglet.

```
int m_nTabIndex;
```

### <a name="remarks"></a>Notes

Index de l’onglet sur lequel l’utilisateur plane.

### <a name="example"></a>Exemple

L’exemple suivant `m_nTabIndex` montre comment est utilisé dans [l’échantillon MDITabsDemo: MFC Tabbed MDI Application](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_ptabwnd"></a><a name="m_ptabwnd"></a>CMFCTabToolTipInfo:m_pTabWnd

Un pointeur pour le contrôle de l’onglet.

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>Exemple

L’exemple suivant `m_pTabWnd` montre comment est utilisé dans [l’échantillon MDITabsDemo: MFC Tabbed MDI Application](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_strtext"></a><a name="m_strtext"></a>CMFCTabToolTipInfo:m_strText

Texte info-bulle.

```
CString m_strText;
```

### <a name="remarks"></a>Notes

Si la chaîne est vide, l’outil n’est pas affiché.

### <a name="example"></a>Exemple

L’exemple suivant `m_strText` montre comment est utilisé dans [l’échantillon MDITabsDemo: MFC Tabbed MDI Application](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
