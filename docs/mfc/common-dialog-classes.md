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
ms.openlocfilehash: d11d0978763d9599b0471a8e994f15a267f7cb8f
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685557"
---
# <a name="common-dialog-classes"></a>Classes de boîtes de dialogue communes

En plus de la classe [CDialog](../mfc/reference/cdialog-class.md), MFC fournit plusieurs classes dérivées de `CDialog` qui encapsulent les boîtes de dialogue couramment utilisées, comme indiqué dans le tableau suivant. Les boîtes de dialogue encapsulées sont appelées « boîtes de dialogue communes » et font partie de la bibliothèque de boîtes de dialogue communes de Windows (COMMDLG. DLL). Les ressources et le code de modèle de boîte de dialogue pour ces classes sont fournis dans les boîtes de dialogue courantes de Windows qui font partie des versions de Windows 3,1 et ultérieures.

### <a name="common-dialog-classes"></a>Classes de boîtes de dialogue communes

|Classe de boîte de dialogue dérivée|Objectif|
|--------------------------|-------------|
|[CColorDialog](../mfc/reference/ccolordialog-class.md)|Permet à l’utilisateur de sélectionner des couleurs.|
|[CFileDialog](../mfc/reference/cfiledialog-class.md)|Permet à l’utilisateur de sélectionner un nom de fichier à ouvrir ou à enregistrer.|
|[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)|Permet à l’utilisateur de lancer une opération de recherche ou de remplacement dans un fichier texte.|
|[CFontDialog](../mfc/reference/cfontdialog-class.md)|Permet à l’utilisateur de spécifier une police.|
|[CPrintDialog](../mfc/reference/cprintdialog-class.md)|Permet à l’utilisateur de spécifier des informations pour un travail d’impression.|
|[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)|Feuille de propriétés d’impression Windows.|

Pour plus d’informations sur les classes de boîtes de dialogue communes, consultez noms de classes individuels dans la *référence MFC*. MFC fournit également un certain nombre de classes de boîte de dialogue standard utilisées pour OLE. Pour plus d’informations sur ces classes, consultez la classe de base, [COleDialog](../mfc/reference/coledialog-class.md), dans la *référence MFC*.

Trois autres classes dans MFC ont des caractéristiques de type boîte de dialogue. Pour plus d’informations sur les classes [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md)et [CDaoRecordView](../mfc/reference/cdaorecordview-class.md), consultez les classes dans la *référence MFC*. Pour plus d’informations sur la classe [CDialogBar](../mfc/reference/cdialogbar-class.md), consultez [barres de boîte de dialogue](../mfc/dialog-bars.md).

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)<br/>
[Utilisation des boîtes de dialogue dans MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Boîtes de dialogue dans OLE](../mfc/dialog-boxes-in-ole.md)
