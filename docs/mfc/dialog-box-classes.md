---
description: 'En savoir plus sur : classes de boîte de dialogue'
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
ms.openlocfilehash: 5c178bc6895e338bf4b2876be5233c1b80007abc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261552"
---
# <a name="dialog-box-classes"></a>Classes de boîte de dialogue

`CDialog`La classe et ses classes dérivées encapsulent la fonctionnalité de boîte de dialogue. Comme une boîte de dialogue est un type spécial de fenêtre, `CDialog` est dérivée de `CWnd` . Dérivez vos classes de boîtes de dialogue `CDialog` ou utilisez l’une des classes de boîtes de dialogue courantes pour les boîtes de dialogue standard, telles que l’ouverture ou l’enregistrement d’un fichier, l’impression, la sélection d’une police ou d’une couleur, le lancement d’une opération de recherche et de remplacement, ou l’exécution de diverses opérations liées à OLE.

[CDialog](reference/cdialog-class.md)<br/>
Classe de base pour toutes les boîtes de dialogue, modales et non modales.

[CDataExchange](reference/cdataexchange-class.md)<br/>
Fournit des informations d’échange de données et de validation pour les boîtes de dialogue.

## <a name="common-dialogs"></a>Boîtes de dialogue courantes

Ces classes de boîte de dialogue encapsulent les boîtes de dialogue communes de Windows. Ils fournissent des implémentations faciles à utiliser de boîtes de dialogue complexes.

[CCommonDialog](reference/ccommondialog-class.md)<br/>
Classe de base pour toutes les boîtes de dialogue courantes.

[CFileDialog](reference/cfiledialog-class.md)<br/>
Fournit une boîte de dialogue standard pour ouvrir ou enregistrer un fichier.

[CColorDialog](reference/ccolordialog-class.md)<br/>
Fournit une boîte de dialogue standard pour la sélection d’une couleur.

[CFontDialog](reference/cfontdialog-class.md)<br/>
Fournit une boîte de dialogue standard pour la sélection d’une police.

[CFindReplaceDialog](reference/cfindreplacedialog-class.md)<br/>
Fournit une boîte de dialogue standard pour une opération de recherche et de remplacement.

[CPrintDialog](reference/cprintdialog-class.md)<br/>
Fournit une boîte de dialogue standard pour l’impression d’un fichier.

[CPrintDialogEx](reference/cprintdialogex-class.md)<br/>
Fournit une feuille de propriétés d’impression Windows.

[CPageSetupDialog](reference/cpagesetupdialog-class.md)<br/>
Encapsule les services fournis par la boîte de dialogue mise en page commune de Windows avec une prise en charge supplémentaire pour définir et modifier les marges d’impression.

## <a name="ole-common-dialogs"></a>Boîtes de dialogue communes OLE

OLE ajoute plusieurs boîtes de dialogue courantes à Windows. Ces classes encapsulent les boîtes de dialogue communes OLE.

[COleDialog](reference/coledialog-class.md)<br/>
Utilisé par l’infrastructure pour contenir des implémentations courantes pour toutes les boîtes de dialogue OLE. Toutes les classes de boîte de dialogue de la catégorie interface utilisateur sont dérivées de cette classe de base. `COleDialog` ne peut pas être utilisé directement.

[COleInsertDialog](reference/coleinsertdialog-class.md)<br/>
Affiche la boîte de dialogue Insérer un objet, l’interface utilisateur standard qui permet d’insérer de nouveaux éléments OLE liés ou incorporés.

[COlePasteSpecialDialog](reference/colepastespecialdialog-class.md)<br/>
Affiche la boîte de dialogue Collage spécial, l’interface utilisateur standard pour l’implémentation de la commande Modifier Collage spécial.

[COleLinksDialog](reference/colelinksdialog-class.md)<br/>
Affiche la boîte de dialogue Modifier les liens, l’interface utilisateur standard permettant de modifier les informations relatives aux éléments liés.

[COleChangeIconDialog](reference/colechangeicondialog-class.md)<br/>
Affiche la boîte de dialogue changer d’icône, l’interface utilisateur standard pour modifier l’icône associée à un élément OLE incorporé ou lié.

[COleConvertDialog](reference/coleconvertdialog-class.md)<br/>
Affiche la boîte de dialogue convertir, l’interface utilisateur standard pour convertir les éléments OLE d’un type en un autre.

[COlePropertiesDialog](reference/colepropertiesdialog-class.md)<br/>
Encapsule la boîte de dialogue Propriétés communes de Windows OLE. Les boîtes de dialogue Propriétés OLE communes offrent un moyen simple d’afficher et de modifier les propriétés d’un élément de document OLE d’une manière cohérente avec les normes Windows.

[COleUpdateDialog](reference/coleupdatedialog-class.md)<br/>
Affiche la boîte de dialogue mettre à jour, l’interface utilisateur standard pour la mise à jour de tous les liens d’un document. La boîte de dialogue contient un indicateur de progression pour indiquer la fin de la procédure de mise à jour.

[COleChangeSourceDialog](reference/colechangesourcedialog-class.md)<br/>
Affiche la boîte de dialogue Modifier la source, l’interface utilisateur standard pour la modification de la destination ou de la source d’un lien.

[COleBusyDialog](reference/colebusydialog-class.md)<br/>
Affiche les boîtes de dialogue serveur occupé et serveur ne répond pas, l’interface utilisateur standard pour la gestion des appels aux applications occupées. Généralement affiché automatiquement par l’implémentation de [COleMessageFilter](reference/colemessagefilter-class.md) .

## <a name="property-sheet-classes"></a>Classes de feuille de propriétés

Les classes de feuille de propriétés permettent à vos applications d’utiliser des feuilles de propriétés, également appelées boîtes de dialogue à onglets. Les feuilles de propriétés sont un moyen efficace d’organiser un grand nombre de contrôles dans une seule boîte de dialogue.

[CPropertyPage](reference/cpropertypage-class.md)<br/>
Fournit les pages individuelles dans une feuille de propriétés. Dérivez une classe de `CPropertyPage` pour chaque page à ajouter à votre feuille de propriétés.

[CPropertySheet](reference/cpropertysheet-class.md)<br/>
Fournit le frame pour plusieurs pages de propriétés. Dérivez votre classe de feuille de propriétés de `CPropertySheet` pour implémenter vos feuilles de propriétés rapidement.

[COlePropertyPage](reference/colepropertypage-class.md)<br/>
Affiche les propriétés d'un contrôle OLE dans une interface graphique, similaire à une boîte de dialogue.

## <a name="html-based-dialog-classes"></a>Classes de boîtes de dialogue HTML

[CDHtmlDialog](reference/cdhtmldialog-class.md)<br/>
Utilisé pour créer des boîtes de dialogue qui implémentent leur interface utilisateur avec HTML plutôt que des ressources de boîte de dialogue.

[CMultiPageDHtmlDialog](reference/cmultipagedhtmldialog-class.md)<br/>
Affiche plusieurs pages HTML de manière séquentielle et gère les événements de chaque page.

## <a name="related-classes"></a>Classes connexes

Ces classes ne sont pas des boîtes de dialogue par se, mais elles utilisent des modèles de boîte de dialogue et présentent la majeure partie du comportement des boîtes de dialogue.

[CDialogBar](reference/cdialogbar-class.md)<br/>
Barre de contrôles basée sur un modèle de boîte de dialogue.

[CFormView](reference/cformview-class.md)<br/>
Vue de défilement dont la disposition est définie dans un modèle de boîte de dialogue. Dérivez une classe de `CFormView` pour implémenter une interface utilisateur basée sur un modèle de boîte de dialogue.

[CDaoRecordView](reference/cdaorecordview-class.md)<br/>
Fournit un mode formulaire directement connecté à un objet Recordset d’objet d’accès aux données (DAO). Comme tous les affichages de formulaire, un `CDaoRecordView` est basé sur un modèle de boîte de dialogue.

[CRecordView](reference/crecordview-class.md)<br/>
Fournit un mode formulaire directement connecté à un objet Recordset Open Database Connectivity (ODBC). Comme tous les affichages de formulaire, un `CRecordView` est basé sur un modèle de boîte de dialogue.

[CPrintInfo](reference/cprintinfo-structure.md)<br/>
Structure contenant des informations sur un travail d’impression ou d’aperçu avant impression. Utilisé par l’architecture d’impression de [CView](reference/cview-class.md).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
