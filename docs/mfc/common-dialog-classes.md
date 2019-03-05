---
title: Classes de boîtes de dialogue communes
ms.date: 11/04/2016
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
ms.openlocfilehash: 5efd885421d8c73c191e2a5603f37d1df85a5168
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303064"
---
# <a name="common-dialog-classes"></a>Classes de boîtes de dialogue communes

En plus de la classe [CDialog](../mfc/reference/cdialog-class.md), MFC fournit plusieurs classes dérivées de `CDialog` qui encapsulent des boîtes de dialogue couramment utilisées, comme indiqué dans le tableau suivant. Ces boîtes de dialogue sont appelés les « boîtes de dialogue communes » et font partie de la bibliothèque de boîte de dialogue commune Windows (COMMDLG. (DLL). Les ressources de modèle de boîte de dialogue et le code de ces classes sont fournis dans le Windows des boîtes de dialogue communes qui font partie de Windows versions 3.1 et version ultérieures.

### <a name="common-dialog-classes"></a>Classes de boîtes de dialogue communes

|Classe de boîte de dialogue dérivée|Objectif|
|--------------------------|-------------|
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|Permet de sélectionner les couleurs utilisateur.|
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|Permet à utilisateur de sélectionner un nom de fichier à ouvrir ou à enregistrer.|
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|Permet à utilisateur lancer une recherche ou d’opération dans un fichier texte de remplacement.|
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|Permet à utilisateur de spécifier une police.|
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|Permet à utilisateur de spécifier des informations pour un travail d’impression.|
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Feuille de propriétés d’impression de Windows.|

Pour plus d’informations sur les classes de boîte de dialogue courantes, consultez les noms de classe individuels dans le *référence MFC*. MFC fournit également un nombre de classes de boîte de dialogue standard utilisées pour OLE. Pour plus d’informations sur ces classes, consultez la classe de base, [COleDialog](../mfc/reference/coledialog-class.md), dans le *référence MFC*.

Trois autres classes dans MFC présentent des caractéristiques de boîtes de dialogue. Pour plus d’informations sur les classes [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md), et [CDaoRecordView](../mfc/reference/cdaorecordview-class.md), consultez les classes dans le *référence MFC*. Pour plus d’informations sur la classe [CDialogBar](../mfc/reference/cdialogbar-class.md), consultez [barres de boîte de dialogue](../mfc/dialog-bars.md).

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)<br/>
[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Boîtes de dialogue dans OLE](../mfc/dialog-boxes-in-ole.md)
