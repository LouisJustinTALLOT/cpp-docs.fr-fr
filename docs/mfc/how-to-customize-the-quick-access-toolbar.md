---
description: 'En savoir plus sur : Comment : personnaliser la barre d’outils accès rapide'
title: "Comment : personnaliser la barre d'outils Accès rapide"
ms.date: 09/07/2019
helpviewer_keywords:
- quick access toolbar [MFC], customization
ms.assetid: 2554099b-0c89-4605-9249-31bf9cbcefe0
ms.openlocfilehash: cb7935f9e340734f8af0e7ec9197e139c30af894
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330234"
---
# <a name="how-to-customize-the-quick-access-toolbar"></a>Comment : personnaliser la barre d'outils Accès rapide

La barre d’outils accès rapide (QAT) est une barre d’outils personnalisable qui contient un ensemble de commandes qui sont affichées en regard du bouton d’application ou sous les onglets de catégorie. L’illustration suivante montre une barre d’outils accès rapide classique.

![Barre d'outils Accès rapide de ruban MFC](../mfc/media/quick_access_toolbar.png "Barre d'outils Accès rapide de ruban MFC")

Pour personnaliser la barre d’outils accès rapide, ouvrez-la dans la fenêtre **Propriétés** , modifiez ses commandes, puis affichez un aperçu du contrôle du ruban.

### <a name="to-open-the-quick-access-toolbar-in-the-properties-window"></a>Pour ouvrir la barre d’outils accès rapide dans le Fenêtre Propriétés

1. Dans Visual Studio, dans le menu **affichage** , cliquez sur **affichage des ressources**.

1. Dans **affichage des ressources**, double-cliquez sur la ressource du ruban pour l’afficher sur l’aire de conception.

1. Dans l’aire de conception, cliquez avec le bouton droit sur le menu de la barre d’outils accès rapide, puis cliquez sur **Propriétés**.

## <a name="quick-access-toolbar-properties"></a>Propriétés de la barre d’outils accès rapide

Le tableau suivant définit les propriétés de la barre d’outils accès rapide.

|Propriété|Définition|
|--------------|----------------|
|Position du QAT|Spécifie la position de la barre d’outils accès rapide au démarrage de l’application. La position peut être **au-dessus** ou au **-dessous** du contrôle de ruban.|
|Éléments QAT|Spécifie les commandes disponibles pour la barre d’outils accès rapide.|

#### <a name="to-add-or-remove-commands-on-the-quick-access-toolbar"></a>Pour ajouter ou supprimer des commandes dans la barre d’outils accès rapide

1. Dans la fenêtre **Propriétés** , cliquez sur **éléments qat**, puis cliquez sur le bouton **de sélection (...)**.

1. Dans la boîte de dialogue **éditeur d’éléments qat** , utilisez les boutons **Ajouter** et **supprimer** pour modifier la liste des commandes dans la barre d’outils accès rapide.

1. Si vous souhaitez qu’une commande s’affiche à la fois dans la barre d’outils accès rapide et dans le menu de la barre d’outils accès rapide, activez la case à cocher en regard de la commande. Si vous souhaitez que la commande s’affiche uniquement dans le menu, décochez la case.

## <a name="previewing-the-ribbon"></a>Aperçu du ruban

Les commandes de la barre d’outils accès rapide n’apparaissent pas sur l’aire de conception. Pour les afficher, vous devez afficher un aperçu du ruban ou exécuter l’application.

#### <a name="to-preview-the-ribbon-control"></a>Pour afficher un aperçu du contrôle du ruban

- Dans la **barre d’outils** de l’éditeur de ruban, cliquez sur **tester le ruban**.

## <a name="see-also"></a>Voir aussi

[Concepteur de ruban (MFC)](ribbon-designer-mfc.md)
