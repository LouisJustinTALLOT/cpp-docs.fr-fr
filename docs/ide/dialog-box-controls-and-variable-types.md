---
title: Contrôles de boîtes de dialogue et types de variables | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: f9cd9cea-45a6-4349-8358-e5efbcdcff76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6914ab8b5838ee6bc5bb7a74004ed986efe2fcda
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373985"
---
# <a name="dialog-box-controls-and-variable-types"></a>Contrôles de boîtes de dialogue et types de variables

Vous pouvez utiliser [l’Assistant Ajout de variable membre](../ide/add-member-variable-wizard.md) pour ajouter une variable membre à un contrôle de boîte de dialogue créé à l’aide de MFC. Le type de contrôle pour lequel vous ajoutez la variable membre détermine les options qui apparaissent dans la boîte de dialogue.

Le tableau suivant décrit tous les types de contrôles de boîtes de dialogue pris en charge dans MFC et dans [l’Éditeur de boîtes de dialogue](../windows/dialog-editor.md), ainsi que les types et valeurs disponibles.

|Contrôle|Type du contrôle|Type de variable de contrôle|Type de variable de valeur|Valeurs min/max (type valeur uniquement)|
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|
|Contrôle Animation|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Aucun ; contrôle uniquement|N/A|
|Bouton|BUTTON|[CButton](../mfc/reference/cbutton-class.md)|Aucun ; contrôle uniquement|N/A|
|Case à cocher|CHECK|[CButton](../mfc/reference/cbutton-class.md)|**BOOL**|Valeur min/Valeur max|
|Zone de liste modifiable|COMBOBOX|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|Nombre maximal de caractères|
|Contrôle Sélecteur de date et d’heure|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|Valeur min/Valeur max|
|Zone d’édition|EDITION|[CEdit](../mfc/reference/cedit-class.md)|`CString`, int, UINT, long, DWORD, float, double, BYTE, short, BOOL, `COleDateTime` ou **COleCurrency**|Valeur min/Valeur max ; certaines prennent en charge le nombre maximal de caractères|
|Contrôle de touche d’accès rapide|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Aucun ; contrôle uniquement|N/A|
|Zone de liste|LISTBOX|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|Nombre maximal de caractères|
|Contrôle List|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|Aucun ; contrôle uniquement|N/A|
|Contrôle Month Calendar|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|Valeur min/Valeur max|
|Contrôle Progress|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Aucun ; contrôle uniquement|N/A|
|Contrôle RichEdit 2|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|Nombre maximal de caractères|
|Contrôle RichEdit|RICHEDIT|`CRichEditCtrl`|`CString`|Nombre maximal de caractères|
|Barre de défilement (verticale ou horizontale)|SCROLLBAR|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|Valeur min/Valeur max|
|Contrôle Slider|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|Valeur min/Valeur max|
|Contrôle Spin|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Aucun ; contrôle uniquement|N/A|
|Contrôle Tab|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Aucun ; contrôle uniquement|N/A|
|Contrôle Tree|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Aucun ; contrôle uniquement|N/A|

## <a name="see-also"></a>Voir aussi

[Ajout d’une variable membre](../ide/adding-a-member-variable-visual-cpp.md)