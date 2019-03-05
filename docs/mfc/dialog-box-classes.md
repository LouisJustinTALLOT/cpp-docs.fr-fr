---
title: Classes de boîte de dialogue
ms.date: 11/04/2016
f1_keywords:
- vc.classes.dialog
helpviewer_keywords:
- property sheet classes
- dialog box classes
- OLE common dialog classes
- common dialog classes [MFC]
- tab dialog boxes
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
ms.openlocfilehash: 5747e4450816b803f97ad5ff6338b9e01ad41bca
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264038"
---
# <a name="dialog-box-classes"></a>Classes de boîte de dialogue

Classe `CDialog` et ses classes dérivées encapsulent les fonctionnalités de la boîte de dialogue. Dans la mesure où une boîte de dialogue est un type spécial de fenêtre, `CDialog` est dérivée de `CWnd`. Dériver vos classes de boîte de dialogue à partir de `CDialog` ou utilisez une des classes de boîte de dialogue commune pour les boîtes de dialogue standard, telles que l’ouverture ou de l’enregistrement d’un fichier, l’impression, en sélectionnant une police ou la couleur, lancer une opération de recherche et remplacement, ou effectuer des liées à OLE opérations.

[CDialog](../mfc/reference/cdialog-class.md)<br/>
La classe de base pour toutes les boîtes de dialogue, modales et non modales.

[CDataExchange](../mfc/reference/cdataexchange-class.md)<br/>
Fournit des informations d’échange et validation des données pour les boîtes de dialogue.

## <a name="common-dialogs"></a>Boîtes de dialogue communes

Ces classes de boîte de dialogue encapsulent les boîtes de dialogue communes Windows. Elles fournissent des implémentations de facile à utiliser des boîtes de dialogue complexe.

[CCommonDialog](../mfc/reference/ccommondialog-class.md)<br/>
Classe de base pour toutes les boîtes de dialogue communes.

[CFileDialog](../mfc/reference/cfiledialog-class.md)<br/>
Fournit une boîte de dialogue standard pour ouvrir ou enregistrer un fichier.

[CColorDialog](../mfc/reference/ccolordialog-class.md)<br/>
Fournit une boîte de dialogue standard permettant de sélectionner une couleur.

[CFontDialog](../mfc/reference/cfontdialog-class.md)<br/>
Fournit une boîte de dialogue standard pour la sélection d’une police.

[CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)<br/>
Fournit une boîte de dialogue standard pour une opération de recherche et remplacement.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
Fournit une boîte de dialogue standard pour l’impression d’un fichier.

[CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)<br/>
Fournit une feuille de propriétés d’impression de Windows.

[CPageSetupDialog](../mfc/reference/cpagesetupdialog-class.md)<br/>
Encapsule les services fournis par la boîte de dialogue de mise en Page courante Windows avec prise en charge supplémentaire pour définir et modifier les marges d’impression.

## <a name="ole-common-dialogs"></a>Boîtes de dialogue communes OLE

OLE ajoute plusieurs boîtes de dialogue communes à Windows. Ces classes encapsulent les boîtes de dialogue communes OLE.

[COleDialog](../mfc/reference/coledialog-class.md)<br/>
Utilisé par l’infrastructure pour contenir les implémentations courantes pour toutes les boîtes de dialogue OLE. Toutes les classes de boîte de dialogue dans la catégorie de l’interface utilisateur sont dérivés de cette classe de base. `COleDialog` ne peut pas être utilisée directement.

[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)<br/>
Affiche la boîte de dialogue Insérer un objet, l’interface utilisateur standard pour l’insertion de nouvelles OLE éléments liés ou incorporés.

[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)<br/>
Affiche la boîte de dialogue Collage spécial, l’interface utilisateur standard pour l’implémentation de la commande modifier le collage spécial.

[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)<br/>
Affiche la boîte de dialogue Modifier les liens, l’interface utilisateur standard pour la modification des informations sur les éléments liés.

[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)<br/>
Affiche la boîte de dialogue Changer d’icône, l’interface utilisateur standard pour modifier l’icône associée à OLE incorporé ou un élément lié.

[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)<br/>
Affiche la boîte de dialogue Convertir, l’interface utilisateur standard pour la conversion des éléments OLE à partir d’un type.

[COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)<br/>
Encapsule la boîte de dialogue de propriétés OLE commune Windows. Boîtes de dialogue communes OLE propriétés fournissent un moyen simple pour afficher et modifier les propriétés d’un élément de document OLE de manière cohérente avec les normes de Windows.

[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)<br/>
Affiche la boîte de dialogue de mise à jour, l’interface utilisateur standard pour la mise à jour tous les liens dans un document. La boîte de dialogue contient un indicateur de progression pour indiquer comment fermer la procédure de mise à jour est terminée.

[COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)<br/>
Affiche la boîte de dialogue Modifier la Source, l’interface utilisateur standard pour la modification de la source d’un lien ou de destination.

[COleBusyDialog](../mfc/reference/colebusydialog-class.md)<br/>
Affiche les boîtes de dialogue serveur occupé et serveur ne répond pas, l’interface utilisateur standard pour gérer les appels aux applications occupées. Généralement affiché automatiquement par le [intermédiaire de COleMessageFilter](../mfc/reference/colemessagefilter-class.md) implémentation.

## <a name="property-sheet-classes"></a>Classes de feuille de propriétés

Les classes de feuille de propriétés permettent à vos applications d’utiliser des feuilles de propriétés, également connu sous les onglets des boîtes de dialogue. Feuilles de propriétés sont un moyen efficace d’organiser un grand nombre de contrôles dans une boîte de dialogue.

[CPropertyPage](../mfc/reference/cpropertypage-class.md)<br/>
Fournit les pages individuelles au sein d’une feuille de propriétés. Dérivez une classe de `CPropertyPage` pour chaque page à ajouter à votre feuille de propriétés.

[CPropertySheet](../mfc/reference/cpropertysheet-class.md)<br/>
Fournit le frame pour plusieurs pages de propriétés. Dérivez votre classe de feuille de propriétés de `CPropertySheet` pour implémenter rapidement de vos feuilles de propriétés.

[COlePropertyPage](../mfc/reference/colepropertypage-class.md)<br/>
Affiche les propriétés d'un contrôle OLE dans une interface graphique, similaire à une boîte de dialogue.

## <a name="html-based-dialog-classes"></a>Classes de dialogue HTML

[CDHtmlDialog](../mfc/reference/cdhtmldialog-class.md)<br/>
Utilisé pour créer des boîtes de dialogue qui implémentent l’interface utilisateur avec des ressources HTML plutôt que de boîte de dialogue.

[CMultiPageDHtmlDialog](../mfc/reference/cmultipagedhtmldialog-class.md)<br/>
Affiche plusieurs pages HTML de manière séquentielle et gère les événements à partir de chaque page.

## <a name="related-classes"></a>Classes connexes

Ces classes ne sont pas des boîtes de dialogue proprement dite, mais elles utilisent les modèles de boîte de dialogue et ont une grande partie du comportement de boîtes de dialogue.

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
Une barre de contrôle qui est basée sur un modèle de boîte de dialogue.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Une vue de défilement dont la disposition est définie dans un modèle de boîte de dialogue. Dérivez une classe de `CFormView` pour implémenter une interface utilisateur basée sur un modèle de boîte de dialogue.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Fournit un formulaire de vue directement connecté à un objet de jeu d’enregistrements d’objet DAO (Data Access). Comme toutes les vues de formulaire, un `CDaoRecordView` est basé sur un modèle de boîte de dialogue.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Fournit un formulaire de vue directement connecté à un objet de jeu d’enregistrements Open Database Connectivity (ODBC). Comme toutes les vues de formulaire, un `CRecordView` est basé sur un modèle de boîte de dialogue.

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
Une structure contenant des informations sur un travail d’impression ou Aperçu avant impression. Utilisé par l’architecture d’impression de [CView](../mfc/reference/cview-class.md).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
