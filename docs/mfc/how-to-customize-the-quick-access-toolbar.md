---
title: 'Comment : personnaliser la barre d’outils Accès rapide | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f3ec14971b69788892690c26ef2759f3b35d55f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419100"
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>Comment : personnaliser la barre d'outils Accès rapide

La barre d’outils d’accès (rapide) est une barre d’outils personnalisable qui contient un ensemble de commandes qui sont que soit affichée en regard du bouton de l’Application ou sous les onglets de catégorie. L’illustration suivante montre une barre d’outils Accès rapide typique.

![Barre d’outils Accès rapide MFC ruban](../mfc/media/quick_access_toolbar.png "quick_access_toolbar")

Pour personnaliser la barre d’outils Accès rapide, ouvrez-le dans le **propriétés** fenêtre, modifiez ses commandes, puis affichez l’aperçu du contrôle de ruban.

### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>Pour ouvrir la barre d’outils Accès rapide dans la fenêtre Propriétés

1. Dans Visual Studio, sur le **vue** menu, cliquez sur **affichage des ressources**.

1. Dans **affichage des ressources**, double-cliquez sur la ressource de ruban pour l’afficher sur l’aire de conception.

1. Dans l’aire de conception, cliquez sur le menu d’une barre d’outils Accès rapide, puis sur **propriétés**.

## <a name="quick-access-toolbar-properties"></a>Propriétés de barre d’outils Accès rapide

Le tableau suivant définit les propriétés de la barre d’outils Accès rapide.

|Propriété|Définition|
|--------------|----------------|
|QAT Position|Spécifie la position de la barre d’outils Accès rapide lorsque l’application démarre. La position peut être **ci-dessus** ou **ci-dessous** le contrôle de ruban.|
|QAT Items|Spécifie les commandes qui sont disponibles pour la barre d’outils Accès rapide.|

#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>Pour ajouter ou supprimer des commandes sur la barre d’outils Accès rapide

1. Dans le **propriétés** fenêtre, cliquez sur **QAT Items**, puis cliquez sur le bouton de sélection **(...)** .

1. Dans le **Éditeur d’éléments QAT** boîte de dialogue, utilisez le **ajouter** et **supprimer** boutons pour modifier la liste des commandes sur la barre d’outils Accès rapide.

1. Si vous souhaitez une commande apparaissent sur la barre d’outils Accès rapide et le menu d’une barre d’outils Accès rapide, sélectionnez la case en regard de la commande. Si vous voulez que la commande apparaît uniquement dans le menu, désactivez la case.

## <a name="previewing-the-ribbon"></a>L’aperçu du ruban

Les commandes de barre d’outils accès rapides n’apparaissent pas sur l’aire de conception. Pour les afficher, vous devez afficher un aperçu du ruban ou exécuter l’application.

#### <a name="to-preview-the-ribbon-control"></a>Pour afficher un aperçu du contrôle de ruban

- Sur le **barre d’outils Éditeur Ribbon**, cliquez sur **Test ruban**.

## <a name="see-also"></a>Voir aussi

[Concepteur de ruban (MFC)](../mfc/ribbon-designer-mfc.md)

