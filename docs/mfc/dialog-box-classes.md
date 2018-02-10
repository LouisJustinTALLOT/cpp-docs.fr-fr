---
title: "Classes de boîte de dialogue | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.dialog
dev_langs:
- C++
helpviewer_keywords:
- property sheet classes
- dialog box classes
- OLE common dialog classes
- common dialog classes [MFC]
- tab dialog boxes
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d51529e5d04a8297c0d3824ab38c7d2045bc866
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="dialog-box-classes"></a>Classes de boîte de dialogue
Classe `CDialog` et ses classes dérivées encapsulent les fonctionnalités de la boîte de dialogue. Dans la mesure où une boîte de dialogue est un type spécial de fenêtre, `CDialog` est dérivée de `CWnd`. Dériver vos classes de boîte de dialogue à partir de `CDialog` ou utilisez une des classes de boîte de dialogue courantes pour les boîtes de dialogue standard, telles que l’ouverture ou de l’enregistrement d’un fichier, l’impression, en sélectionnant une police ou une couleur, lancer une opération de recherche et remplacement, ou effectuer diverses liées à OLE opérations.  
  
 [CDialog](../mfc/reference/cdialog-class.md)  
 La classe de base pour les boîtes de dialogue modales et non modales.  
  
 [CDataExchange](../mfc/reference/cdataexchange-class.md)  
 Fournit des informations d’échange et validation de données de boîtes de dialogue.  
  
## <a name="common-dialogs"></a>Boîtes de dialogue communes  
 Ces classes de boîte de dialogue encapsulent les boîtes de dialogue communes Windows. Elles fournissent des implémentations de facile à utiliser des boîtes de dialogue complexes.  
  
 [CCommonDialog](../mfc/reference/ccommondialog-class.md)  
 Classe de base pour toutes les boîtes de dialogue communes.  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 Fournit une boîte de dialogue standard d’ouverture ou de l’enregistrement d’un fichier.  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 Fournit une boîte de dialogue standard permettant de sélectionner une couleur.  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 Fournit une boîte de dialogue standard pour la sélection d’une police.  
  
 [CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)  
 Fournit une boîte de dialogue standard pour une opération de recherche et remplacement.  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 Fournit une boîte de dialogue standard pour l’impression d’un fichier.  
  
 [CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)  
 Fournit une feuille de propriétés d’impression Windows.  
  
 [CPageSetupDialog](../mfc/reference/cpagesetupdialog-class.md)  
 Encapsule les services fournis par la boîte de dialogue Mise en Page courante Windows avec prise en charge supplémentaire pour définir et modifier les marges d’impression.  
  
## <a name="ole-common-dialogs"></a>Boîtes de dialogue communes OLE  
 OLE ajoute plusieurs boîtes de dialogue communes Windows. Ces classes encapsulent les boîtes de dialogue communes OLE.  
  
 [COleDialog](../mfc/reference/coledialog-class.md)  
 Utilisé par l’infrastructure pour contenir les implémentations courantes pour toutes les boîtes de dialogue OLE. Toutes les classes de boîte de dialogue dans la catégorie de l’interface utilisateur sont dérivées de cette classe de base. `COleDialog`ne peut pas être utilisée directement.  
  
 [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)  
 Affiche la boîte de dialogue Insérer un objet, l’interface utilisateur standard pour l’insertion de nouvelles OLE éléments liés ou incorporés.  
  
 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)  
 Affiche la boîte de dialogue Collage spécial, l’interface utilisateur standard pour l’implémentation de la commande modifier le collage spécial.  
  
 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md)  
 Affiche la boîte de dialogue Modifier les liaisons, l’interface utilisateur standard pour la modification des informations sur les éléments liés.  
  
 [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)  
 Affiche la boîte de dialogue Changer d’icône, l’interface utilisateur standard pour la modification de l’icône associée à une OLE incorporé ou lié un élément.  
  
 [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)  
 Affiche la boîte de dialogue de conversion, l’interface utilisateur standard pour la conversion des éléments OLE à partir d’un type.  
  
 [COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)  
 Encapsule la boîte de dialogue de propriétés OLE commune Windows. Boîtes de dialogue communes OLE propriétés fournissent un moyen simple pour afficher et modifier les propriétés d’un élément de document OLE de manière cohérente avec les normes de Windows.  
  
 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)  
 Affiche la boîte de dialogue de mise à jour, l’interface utilisateur standard pour mettre à jour tous les liens dans un document. La boîte de dialogue contient un indicateur de progression pour indiquer comment fermer la procédure de mise à jour est terminée.  
  
 [COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)  
 Affiche la boîte de dialogue Modifier la Source, l’interface utilisateur standard pour la modification de la source d’un lien ou de destination.  
  
 [COleBusyDialog](../mfc/reference/colebusydialog-class.md)  
 Affiche les boîtes de dialogue serveur occupé et serveur ne répond pas, l’interface utilisateur standard pour gérer les appels aux applications occupées. Généralement affiché automatiquement par le [intermédiaire de COleMessageFilter](../mfc/reference/colemessagefilter-class.md) implémentation.  
  
## <a name="property-sheet-classes"></a>Classes de feuille de propriétés  
 Les classes de feuille de propriétés permettent aux applications d’utiliser les feuilles de propriétés, également connu sous les onglets des boîtes de dialogue. Feuilles de propriétés sont un moyen efficace pour organiser un grand nombre de contrôles dans une boîte de dialogue.  
  
 [CPropertyPage](../mfc/reference/cpropertypage-class.md)  
 Fournit des pages individuelles dans une feuille de propriétés. Dérivez une classe de `CPropertyPage` pour chaque page à ajouter à votre feuille de propriétés.  
  
 [CPropertySheet](../mfc/reference/cpropertysheet-class.md)  
 Fournit le frame pour plusieurs pages de propriétés. Dérivez votre classe de feuille de propriétés de `CPropertySheet` pour implémenter rapidement de vos feuilles de propriétés.  
  
 [COlePropertyPage](../mfc/reference/colepropertypage-class.md)  
 Affiche les propriétés d'un contrôle OLE dans une interface graphique, similaire à une boîte de dialogue.  
  
## <a name="html-based-dialog-classes"></a>Classes de boîte de dialogue basé sur HTML  
 [CDHtmlDialog](../mfc/reference/cdhtmldialog-class.md)  
 Utilisé pour créer des boîtes de dialogue qui implémentent l’interface utilisateur avec des ressources HTML plutôt que de boîte de dialogue.  
  
 [CMultiPageDHtmlDialog](../mfc/reference/cmultipagedhtmldialog-class.md)  
 Affiche plusieurs pages HTML de manière séquentielle et gère les événements de chaque page.  
  
## <a name="related-classes"></a>Classes associées  
 Ces classes ne sont pas des boîtes de dialogue soi, mais s’ils utilisent les modèles de boîte de dialogue et que vous ont une grande partie du comportement de boîtes de dialogue.  
  
 [CDialogBar](../mfc/reference/cdialogbar-class.md)  
 Une barre de contrôle qui est basée sur un modèle de boîte de dialogue.  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 Une vue de défilement dont la disposition est définie dans un modèle de boîte de dialogue. Dérivez une classe de `CFormView` pour implémenter une interface utilisateur basée sur un modèle de boîte de dialogue.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Fournit une forme vue directement connectée à un objet de jeu d’enregistrements d’objet DAO (Data Access). Comme toutes les vues de l’écran, un `CDaoRecordView` est basé sur un modèle de boîte de dialogue.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Fournit une forme vue directement connectée à un objet de jeu d’enregistrements de base de données ODBC (Open Connectivity). Comme toutes les vues de l’écran, un `CRecordView` est basé sur un modèle de boîte de dialogue.  
  
 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)  
 Une structure contenant des informations sur un travail d’impression ou Aperçu avant impression. Utilisé par l’architecture d’impression de [CView](../mfc/reference/cview-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

