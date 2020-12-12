---
description: 'En savoir plus sur : fonctionnalités de l’interface utilisateur, Assistant Application MFC'
title: Fonctionnalités de l'interface utilisateur, Assistant Application MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.ui
helpviewer_keywords:
- MFC Application Wizard, user interface features
ms.assetid: 59e7b829-a665-42eb-be23-3f2a36eb2dad
ms.openlocfilehash: ac2c3dc7881fd5e931539224bed121c617b940a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218509"
---
# <a name="user-interface-features-mfc-application-wizard"></a>Fonctionnalités de l'interface utilisateur, Assistant Application MFC

Cette rubrique décrit les options que vous pouvez utiliser pour spécifier l’apparence de votre application. Les fonctionnalités d’interface utilisateur disponibles pour votre projet dépendent du type d’application que vous avez spécifié dans la page [type d’application, Assistant Application MFC](../../mfc/reference/application-type-mfc-application-wizard.md) de l’Assistant Application MFC. Par exemple, si vous créez une application d’interface de document unique, vous ne pouvez pas ajouter de styles de Frame enfant.

- **Styles du frame principal**

   Définit les fonctionnalités du frame de fenêtre principale de votre application.

   |Option|Description|
   |------------|-----------------|
   |**Cadre épais**|Crée une fenêtre qui a une bordure de redimensionnement. Valeur par défaut.|
   |**Réduire la zone**|Comprend une zone de réduction dans la fenêtre frame principale. Valeur par défaut.|
   |**Agrandir la zone**|Comprend une zone agrandir dans la fenêtre frame principale. Valeur par défaut.|
   |**Réduite**|Ouvre la fenêtre frame principale sous forme d’icône.|
   |**Agrandie**|Ouvre la fenêtre frame principale à la taille complète de l’affichage.|
   |**Menu système**|Comprend un menu système dans la fenêtre frame principale. Valeur par défaut.|
   |**Boîte à propos**|Contient une zone **à propos** de pour l’application. L’utilisateur peut accéder à cette zone à partir du menu **aide** de l’application. La valeur par défaut et non modifiable, sauf si vous sélectionnez **basée sur une boîte de dialogue**, dans la page [type d’application, Assistant Application MFC](../../mfc/reference/application-type-mfc-application-wizard.md) .<br /><br /> **Remarque** En règle générale, une option non disponible indique que l’Assistant n’applique pas l’option au projet, que la case à cocher de l’élément non disponible soit activée ou désactivée. Dans ce cas, l’Assistant ajoute toujours une zone à **propos** du projet, sauf si vous spécifiez d’abord le projet en tant que boîte de dialogue, puis décochez la case.|
   |**Barre d’État initiale**|Ajoute une barre d’État à votre application. La barre d’état contient des indicateurs automatiques pour les touches Verr. MAJ, Verr. NUM et Arrêt défil du clavier, ainsi qu’une ligne de message qui affiche des chaînes d’aide pour les commandes de menu et les boutons de la barre d’outils. Si vous cliquez sur cette option, vous pouvez également ajouter des commandes de menu pour afficher ou masquer la barre d’État. Par défaut, une application possède une barre d’État. Non disponible pour les types d’applications basés sur des boîtes de dialogue.|
   |**Fractionner la fenêtre**|Fournit une barre de fractionnement. La barre de fractionnement fractionne les vues principales de l’application. Dans une application d’interface multidocument (MDI, multiple document interface), la fenêtre client du Frame enfant MDI est une fenêtre fractionnée et, dans une application SDI (single document interface) et plusieurs applications de document de niveau supérieur, la fenêtre cliente du frame principal est une fenêtre fractionnée. Non disponible pour les types d’applications basés sur des boîtes de dialogue.|

- **Styles de Frame enfant**

   Spécifie l’apparence et l’état initial des frames enfants dans votre application. Les styles de Frame enfant sont uniquement disponibles pour les applications MDI.

   |Option|Description|
   |------------|-----------------|
   |**Zone réduire les enfants**|Spécifie si une fenêtre enfant a un bouton réduire (activé par défaut).|
   |**Zone agrandir enfant**|Spécifie si une fenêtre enfant a un bouton Agrandir (activé par défaut).|
   |**Enfant agrandi**|Spécifie si une fenêtre enfant est initialement agrandie en définissant l’indicateur cs. style WS_MAXIMIZE dans la fonction membre [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow) de `CChildFrame` .|

- **Barres de commandes (menu/barre d’outils/ruban)**

   Indique si votre application comprend des menus, des barres d’outils et/ou un ruban. Non disponible pour les applications basées sur des boîtes de dialogue.

   |Option|Description|
   |------------|-----------------|
   |**Utiliser un menu classique**|Spécifie que votre application contient un menu classique et ne pouvant pas être glissé.|
   |**Utiliser une barre d’outils d’ancrage classique**|Ajoute une barre d’outils Windows standard à votre application. La barre d’outils contient des boutons permettant de créer un nouveau document. ouverture et enregistrement des fichiers de documents ; couper le texte à copier, coller ou imprimer ; et en entrant le mode d’aide. L’activation de cette option ajoute également des commandes de menu pour afficher ou masquer la barre d’outils.|
   |**Utiliser une barre d’outils de style de navigateur**|Ajoute une barre d’outils de style Internet Explorer à votre application.|
   |**Utiliser une barre de menus et une barre d’outils**|Indique que votre application contient une barre de menus Glissable et une barre d’outils.|
   |**Barres d’outils et images définies par l’utilisateur**|Permet à l’utilisateur de personnaliser la barre d’outils et les images de barre d’outils au moment de l’exécution.|
   |**Comportement de menu personnalisé**|Spécifie si le menu contient la liste complète des éléments au moment de l’ouverture, ou s’il contient uniquement les commandes que l’utilisateur utilise le plus fréquemment.|
   |**Utiliser un ruban**|Utilise un ruban de type Office 2007 dans votre application au lieu d’une barre de menus ou d’une barre d’outils.|

- **Titre de la boîte de dialogue**

   Pour les applications basées sur une [classe CDialog](../../mfc/reference/cdialog-class.md)uniquement, ce titre s’affiche dans la barre de titre de la boîte de dialogue. Pour modifier ce champ, vous devez d’abord sélectionner l’option **basée sur une boîte de dialogue** sous **type d’application**. Pour plus d’informations, consultez [type d’application, Assistant Application MFC](../../mfc/reference/application-type-mfc-application-wizard.md).

## <a name="see-also"></a>Voir aussi

[Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)
