---
title: Classes de boîte de dialogue communes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog classes [MFC]
- dialog boxes [MFC], Windows common dialogs
- common dialog boxes [MFC], common dialog classes
- common dialog classes [MFC]
- MFC dialog boxes [MFC], Windows common dialogs
- Windows common dialogs [MFC]
- dialog classes [MFC], common
- common dialog boxes [MFC]
ms.assetid: 5c4f6443-896c-4b05-a7df-8169fdadc71d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cb8a9bacf7414a5a2fff246d796c94a8a1598d7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342213"
---
# <a name="common-dialog-classes"></a>Classes de boîtes de dialogue communes
En plus de la classe [CDialog](../mfc/reference/cdialog-class.md), MFC fournit plusieurs classes dérivées de `CDialog` qui encapsulent des boîtes de dialogue couramment utilisées, comme indiqué dans le tableau suivant. Ces boîtes de dialogue sont appelées les « boîtes de dialogue communes » et font partie de la bibliothèque de boîte de dialogue commune Windows (COMMDLG.) (DLL). Les ressources de modèle de boîte de dialogue et d’un code de ces classes sont fournies dans les fenêtres de boîtes de dialogue communes qui font partie de Windows 3.1 et versions ultérieures.  
  
### <a name="common-dialog-classes"></a>Classes de boîtes de dialogue communes  
  
|Classe de boîte de dialogue dérivée|Objectif|  
|--------------------------|-------------|  
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|Permet de sélectionner les couleurs utilisateur.|  
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|Permet à utilisateur de sélectionner un nom de fichier à ouvrir ou à enregistrer.|  
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|Utilisateur permet de lancer une recherche ou d’opération dans un fichier texte de remplacement.|  
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|Permet à utilisateur de spécifier une police.|  
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|Permet à utilisateur de spécifier des informations pour un travail d’impression.|  
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Feuille de propriétés d’impression Windows.|  
  
 Pour plus d’informations sur les classes de boîte de dialogue commune, consultez les noms de classe individuels dans le *référence MFC*. MFC fournit également un nombre de classes de boîte de dialogue standard utilisées pour OLE. Pour plus d’informations sur ces classes, consultez la classe de base [COleDialog](../mfc/reference/coledialog-class.md), dans le *référence MFC*.  
  
 Trois autres classes dans MFC présentent des caractéristiques de boîtes de dialogue. Pour plus d’informations sur les classes [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md), et [CDaoRecordView](../mfc/reference/cdaorecordview-class.md), consultez les classes dans le *référence MFC*. Pour plus d’informations sur la classe [CDialogBar](../mfc/reference/cdialogbar-class.md), consultez [barres de boîte de dialogue](../mfc/dialog-bars.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Boîtes de dialogue](../mfc/dialog-boxes.md)   
 [Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)   
 [Boîtes de dialogue dans OLE](../mfc/dialog-boxes-in-ole.md)

