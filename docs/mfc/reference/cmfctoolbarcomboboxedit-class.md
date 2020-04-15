---
title: Classe CMFCToolBarComboBoxEdit
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit
helpviewer_keywords:
- CMFCToolBarComboBoxEdit [MFC], CMFCToolBarComboBoxEdit
ms.assetid: 4789c34a-ce58-48ba-a26f-38748b601352
ms.openlocfilehash: dfbf24f5833d143adc6d21b6cb54dd9ac81c2f0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372204"
---
# <a name="cmfctoolbarcomboboxedit-class"></a>Classe CMFCToolBarComboBoxEdit

Le cadre `CMFCToolBarComboBoxEdit` utilise la classe pour créer un bouton de barre d’outils qui se comporte comme un contrôle de boîte combo modifiable.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarComboBoxEdit : public CEdit
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit](#cmfctoolbarcomboboxedit)|Construit un objet `CMFCToolBarComboBoxEdit`.|
|`CMFCToolBarComboBoxEdit::~CMFCToolBarComboBoxEdit`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCToolBarComboBoxEdit::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils ne soient envoyés aux [fonctions De Windows De TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage) (Substitue [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|

### <a name="remarks"></a>Notes

Dérivez une `CMFCToolBarComboBoxEdit` classe de la classe pour personnaliser ses opérations d’édition.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxtoolbarcomboboxbutton.h

## <a name="cmfctoolbarcomboboxeditcmfctoolbarcomboboxedit"></a><a name="cmfctoolbarcomboboxedit"></a>CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit

Construit un objet `CMFCToolBarComboBoxEdit`.

```
CMFCToolBarComboBoxEdit(CMFCToolBarComboBoxButton& combo);
```

### <a name="parameters"></a>Paramètres

*combiné*<br/>
[dans] Une référence à un objet [CMFCToolBarComboBoxButton,](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) qui est un bouton de barre d’outils qui contient un contrôle de boîte combo.

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMFCToolBarComboBoxEdit` un objet de la classe. Cet extrait de code fait partie de [l’échantillon de démonstration IE](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#5](../../mfc/reference/codesnippet/cpp/cmfctoolbarcomboboxedit-class_1.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarComboBoxButton, classe](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)
