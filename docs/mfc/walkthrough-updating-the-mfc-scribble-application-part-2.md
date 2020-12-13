---
description: 'En savoir plus sur : procédure pas à pas : mise à jour de l’application Scribble MFC (partie 2)'
title: "Procédure pas à pas : mise à jour de l'application Scribble MFC (partie 2)"
ms.date: 04/25/2019
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
ms.openlocfilehash: 2520ac8fc1c66a2fc388738d22f4851547b6d03b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142959"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>Procédure pas à pas : mise à jour de l'application Scribble MFC (partie 2)

La [première partie](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) de cette procédure pas à pas a montré comment ajouter un ruban Office Fluent à l’application Scribble classique. Cette partie montre comment ajouter des panneaux et des contrôles de ruban que les utilisateurs peuvent utiliser à la place des menus et des commandes.

## <a name="prerequisites"></a>Prérequis

[Exemples Visual C++](../overview/visual-cpp-samples.md)

## <a name="sections"></a><a name="top"></a> Sections

Cette partie de la procédure pas à pas contient les sections suivantes :

- [Ajout de nouveaux panneaux au ruban](#addnewpanel)

- [Ajout d’un panneau d’aide au ruban](#addhelppanel)

- [Ajout d’un panneau de stylet au ruban](#addpenpanel)

- [Ajout d’un bouton de couleur au ruban](#addcolorbutton)

- [Ajout d’un membre Color à la classe document](#addcolormember)

- [Initialisation des stylets et enregistrement des préférences](#initpensave)

## <a name="adding-new-panels-to-the-ribbon"></a><a name="addnewpanel"></a> Ajout de nouveaux panneaux au ruban

Ces étapes montrent comment ajouter un panneau d' **affichage** qui contient deux cases à cocher qui contrôlent la visibilité de la barre d’outils et de la barre d’État, ainsi qu’un panneau de **fenêtre** qui contient un bouton partagé orienté verticalement qui contrôle la création et la configuration de fenêtres d’interface multidocument (MDI, multiple-document interface).

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>Pour ajouter un panneau d’affichage et un panneau de fenêtre à la barre du ruban

1. Créez un panneau nommé `View` , qui comporte deux cases à cocher qui basculent vers la barre d’État et la barre d’outils.

   1. À partir de la **boîte à outils**, faites glisser un **panneau** vers la catégorie d' **hébergement** . Ensuite, faites glisser deux **cases à cocher** vers le panneau.

   1. Cliquez sur le panneau pour modifier ses propriétés. Remplacez **Caption** par `View` .

   1. Activez la première case à cocher pour modifier ses propriétés. Remplacez l' **ID** par `ID_VIEW_TOOLBAR` et la **légende** par `Toolbar` .

   1. Activez la deuxième case à cocher pour modifier ses propriétés. Remplacez l' **ID** par `ID_VIEW_STATUS_BAR` et la **légende** par `Status Bar` .

1. Créez un panneau nommé `Window` qui a un bouton partagé. Quand un utilisateur clique sur le bouton partagé, un menu contextuel affiche trois commandes qui sont déjà définies dans l’application Scribble.

   1. À partir de la **boîte à outils**, faites glisser un **panneau** vers la catégorie d' **hébergement** . Ensuite, faites glisser un **bouton** sur le panneau.

   1. Cliquez sur le panneau pour modifier ses propriétés. Remplacez **Caption** par `Window` .

   1. Cliquez sur le bouton correspondant. Remplacez **Caption** par `Windows` , **Keys** to `w` , **large image index** par `1` et **mode fractionné** par `False` . Cliquez ensuite sur les points de suspension (**...**) en regard des **éléments de menu** pour ouvrir la boîte de dialogue **éditeur d’éléments** .

   1. Cliquez trois fois sur **Ajouter** pour ajouter trois boutons.

   1. Cliquez sur le premier bouton, puis remplacez **Caption** par `New Window` et **ID** par `ID_WINDOW_NEW` .

   1. Cliquez sur le deuxième bouton, puis remplacez **Caption** par `Cascade` et **ID** par `ID_WINDOW_CASCADE` .

   1. Cliquez sur le troisième bouton, puis remplacez **Caption** par `Tile` et **ID** par `ID_WINDOW_TILE_HORZ` .

1. Enregistrez les modifications, puis générez et exécutez l’application. Les panneaux de **vue** et de **fenêtre** doivent être affichés. Cliquez sur les boutons pour confirmer qu’ils fonctionnent correctement.

## <a name="adding-a-help-panel-to-the-ribbon"></a><a name="addhelppanel"></a> Ajout d’un panneau d’aide au ruban

À présent, vous pouvez assigner deux éléments de menu définis dans l’application Scribble aux boutons du ruban qui sont des **rubriques d’aide** nommées et **à propos de Scribble**. Les boutons sont ajoutés à un nouveau panneau nommé **aide**.

### <a name="to-add-a-help-panel"></a>Pour ajouter un panneau d’aide

1. À partir de la **boîte à outils**, faites glisser un **panneau** vers la catégorie d' **hébergement** . Ensuite, faites glisser deux **boutons** sur le panneau.

1. Cliquez sur le panneau pour modifier ses propriétés. Remplacez **Caption** par `Help` .

1. Cliquez sur le premier bouton. Remplacez **Caption** par `Help Topics` et **ID** par `ID_HELP_FINDER` .

1. Cliquez sur le deuxième bouton. Remplacez **Caption** par `About Scribble...` et **ID** par `ID_APP_ABOUT` .

1. Enregistrez les modifications, puis générez et exécutez l’application. Un panneau **d’aide** qui contient deux boutons de ruban doit s’afficher.

   > [!IMPORTANT]
   > Lorsque vous cliquez sur le bouton **rubriques d’aide** , l’application Scribble ouvre un fichier d’aide HTML (. chm) compressé nommé *your_project_name*. chm. Par conséquent, si votre projet n’est pas nommé Scribble, vous devez renommer le fichier d’aide avec le nom de votre projet.

## <a name="adding-a-pen-panel-to-the-ribbon"></a><a name="addpenpanel"></a> Ajout d’un panneau de stylet au ruban

À présent, ajoutez un panneau pour afficher les boutons qui contrôlent l’épaisseur et la couleur du stylet. Ce panneau contient une case à cocher qui permet de basculer entre les plumes épaisses et fines. Sa fonctionnalité ressemble à celle de l’élément de menu **trait épais** dans l’application Scribble.

L’application Scribble d’origine permet à l’utilisateur de sélectionner des largeurs de stylet dans une boîte de dialogue qui s’affiche quand l’utilisateur clique sur la **largeur du stylet** dans le menu. Étant donné que la barre du ruban dispose de suffisamment d’espace pour les nouveaux contrôles, vous pouvez remplacer la boîte de dialogue à l’aide de deux zones de liste déroulante sur le ruban. Une zone de liste modifiable ajuste la largeur de la plume fine et l’autre zone de liste déroulante ajuste la largeur du stylet épais.

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Pour ajouter un panneau de stylet et des zones de liste déroulante au ruban

1. À partir de la **boîte à outils**, faites glisser un **panneau** vers la catégorie d' **hébergement** . Ensuite, faites glisser une case **à cocher** et deux **zones de liste déroulante** vers le panneau.

1. Cliquez sur le panneau pour modifier ses propriétés. Remplacez **Caption** par `Pen` .

1. Cliquez sur la case à cocher. Remplacez **Caption** par `Use Thick` et **ID** par `ID_PEN_THICK_OR_THIN` .

1. Cliquez sur la première zone de liste déroulante. Remplacez **Caption** par `Thin Pen` , **ID** `ID_PEN_THIN_WIDTH` , **type** `Drop List` , **Data** par `1;2;3;4;5;6;7;8;9;` et **Text** par `2` .

1. Cliquez sur la deuxième zone de liste déroulante. Remplacez **Caption** par `Thick Pen` , **ID** `ID_PEN_THICK_WIDTH` , **type** `Drop List` , **Data** par `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;` et **Text** par `5` .

1. Les nouvelles zones de liste modifiable ne correspondent à aucun élément de menu existant. vous devez donc créer un élément de menu pour chaque option de stylet.

   1. Dans la fenêtre **affichage des ressources** , ouvrez la ressource de menu **IDR_SCRIBBTYPE** .

   1. Cliquez sur **stylet** pour ouvrir le menu du stylet. Cliquez ensuite sur **Tapez ici** et tapez `Thi&n Pen` .

   1. Cliquez avec le bouton droit sur le texte que vous avez tapé pour ouvrir la fenêtre **Propriétés** , puis remplacez la valeur de la propriété ID par `ID_PEN_THIN_WIDTH` .

   1. Créez un gestionnaire d’événements pour chaque élément de menu Pen. Cliquez avec le bouton droit sur l’élément de menu « **Thi&n PEN** » que vous avez créé, puis cliquez sur **Ajouter un gestionnaire d’événements**. L' **Assistant gestionnaire d’événements** s’affiche.

   1. Dans la zone de **liste classe** de l’Assistant, sélectionnez **CScribbleDoc** , puis cliquez sur **Ajouter et modifier**. La commande crée un gestionnaire d’événements nommé `CScribbleDoc::OnPenThinWidth` .

   1. Ajoutez le code suivant à `CScribbleDoc::OnPenThinWidth`.

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        // Get a pointer to the Thin Width combo box
        CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
        CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THIN_WIDTH));

        //Get the selected value
        int nCurSel = pThinComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThinWidth = atoi(CStringA(pThinComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. Ensuite, créez un élément de menu et des gestionnaires d’événements pour le stylet épais.

   1. Dans la fenêtre **affichage des ressources** , ouvrez la ressource de menu **IDR_SCRIBBTYPE** .

   1. Cliquez sur **stylet** pour ouvrir le menu du stylet. Cliquez ensuite sur **Tapez ici** et tapez `Thic&k Pen` .

   1. Cliquez avec le bouton droit sur le texte que vous avez tapé pour afficher la fenêtre **Propriétés** . Remplacez la valeur de la propriété ID par `ID_PEN_THICK_WIDTH` .

   1. Cliquez avec le bouton droit sur l’élément de menu **stylet épais** que vous avez créé, puis cliquez sur **Ajouter un gestionnaire d’événements**. L' **Assistant gestionnaire d’événements** s’affiche.

   1. Dans la zone de **liste classe** de l’Assistant, sélectionnez **CScribbleDoc** , puis cliquez sur **Ajouter et modifier**. La commande crée un gestionnaire d’événements nommé `CScribbleDoc::OnPenThickWidth` .

   1. Ajoutez le code suivant à `CScribbleDoc::OnPenThickWidth`.

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
            CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));
        // Get the selected value
        int nCurSel = pThickComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThickWidth = atoi(CStringA(pThickComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. Enregistrez les modifications, puis générez et exécutez l’application. De nouveaux boutons et zones de liste modifiable doivent s’afficher. Essayez d’utiliser différentes largeurs de stylet pour Scribbler.

## <a name="adding-a-color-button-to-the-pen-panel"></a><a name="addcolorbutton"></a> Ajout d’un bouton de couleur au panneau du stylet

Ensuite, ajoutez un objet [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) qui permet à l’utilisateur de créer un griffonnage en couleur.

### <a name="to-add-a-color-button-to-the-pen-panel"></a>Pour ajouter un bouton de couleur au panneau du stylet

1. Avant d’ajouter le bouton de couleur, créez un élément de menu pour celui-ci. Dans la fenêtre **affichage des ressources** , ouvrez la ressource de menu **IDR_SCRIBBTYPE** . Cliquez sur l’élément de menu **stylet** pour ouvrir le menu stylet. Cliquez ensuite sur **Tapez ici** et tapez `&Color` . Cliquez avec le bouton droit sur le texte que vous avez tapé pour afficher la fenêtre **Propriétés** . Modifiez l’ID en lui attribuant la valeur `ID_PEN_COLOR`.

1. À présent, ajoutez le bouton Color. À partir de la **boîte à outils**, faites glisser un **bouton de couleur** vers le panneau du **stylet** .

1. Cliquez sur le bouton couleur. Remplacez **Caption** par `Color` , **ID** par `ID_PEN_COLOR` , **simple look** to `True` , **large image index** par `1` et **mode fractionné** par `False` .

1. Enregistrez les modifications, puis générez et exécutez l’application. Le bouton nouvelle couleur doit être affiché sur le panneau du **stylet** . Toutefois, il ne peut pas être utilisé, car il n’a pas encore de gestionnaire d’événements. Les étapes suivantes montrent comment ajouter un gestionnaire d’événements pour le bouton de couleur.

## <a name="adding-a-color-member-to-the-document-class"></a><a name="addcolormember"></a> Ajout d’un membre Color à la classe document

Étant donné que l’application Scribble d’origine n’a pas de stylos de couleurs, vous devez écrire une implémentation pour ces dernières. Pour stocker la couleur du stylet du document, ajoutez un nouveau membre à la classe de document, `CscribbleDoc` .

### <a name="to-add-a-color-member-to-the-document-class"></a>Pour ajouter un membre Color à la classe document

1. Dans scribdoc. h, dans la `CScribbleDoc` classe, recherchez la `// Attributes` section. Ajoutez les lignes de code suivantes après la définition du `m_nThickWidth` membre de données.

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. Chaque document contient une liste de Stokes que l’utilisateur a déjà dessinés. Chaque trait est défini par un `CStroke` objet. La `CStroke` classe n’inclut pas d’informations sur la couleur du stylet. vous devez donc modifier la classe. Dans scribdoc. h, dans la `CStroke` classe, ajoutez les lignes de code suivantes après la définition du `m_nPenWidth` membre de données.

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. Dans scribdoc. h, ajoutez un nouveau `CStroke` constructeur dont les paramètres spécifient une largeur et une couleur. Ajoutez la ligne de code suivante après l' `CStroke(UINT nPenWidth);` instruction.

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. Dans scribdoc. cpp, ajoutez l’implémentation du nouveau `CStroke` constructeur. Ajoutez le code suivant après l’implémentation du `CStroke::CStroke(UINT nPenWidth)` constructeur.

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

1. Modifiez la deuxième ligne de la `CStroke::DrawStroke` méthode comme suit.

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

1. Définissez la couleur de plume par défaut pour la classe de document. Dans scribdoc. cpp, ajoutez les lignes suivantes à `CScribbleDoc::InitDocument` , après l' `m_nThickWidth = 5;` instruction.

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. Dans scribdoc. cpp, remplacez la première ligne de la `CScribbleDoc::NewStroke` méthode par la suivante.

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. Remplacez la dernière ligne de la `CScribbleDoc::ReplacePen` méthode par la ligne suivante.

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. Vous avez ajouté le `m_penColor` membre dans une étape précédente. À présent, créez un gestionnaire d’événements pour le bouton de couleur qui définit le membre.

   1. Dans la fenêtre **affichage des ressources** , ouvrez la ressource de menu IDR_SCRIBBTYPE.

   1. Cliquez avec le bouton droit sur l’élément de menu **couleur** , puis cliquez sur **Ajouter un gestionnaire d’événements**. L' **Assistant gestionnaire d’événements** s’affiche.

   1. Dans la zone de **liste classe** de l’Assistant, sélectionnez **CScribbleDoc** , puis cliquez sur le bouton **Ajouter et modifier** . La commande crée le `CScribbleDoc::OnPenColor` stub du gestionnaire d’événements.

1. Remplacez le stub du `CScribbleDoc::OnPenColor` Gestionnaire d’événements par le code suivant.

   ```cpp
   void CScribbleDoc::OnPenColor()
   {
       // Change pen color to reflect color button's current selection
       CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
       ASSERT_VALID(pRibbon);

       CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
           CMFCRibbonColorButton, pRibbon->FindByID(ID_PEN_COLOR));

       m_penColor = pColorBtn->GetColor();
       // Create new pen using the selected color
       ReplacePen();
   }
   ```

1. Enregistrez les modifications, puis générez et exécutez l’application. Vous pouvez maintenant appuyer sur le bouton de couleur et modifier la couleur du stylet.

## <a name="initializing-pens-and-saving-preferences"></a><a name="initpensave"></a> Initialisation des stylets et enregistrement des préférences

Ensuite, initialisez la couleur et la largeur des stylets. Enfin, enregistrez et chargez un dessin de couleur à partir d’un fichier.

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>Pour initialiser des contrôles sur la barre du ruban

1. Initialisez les stylets sur la barre du ruban.

   Ajoutez le code suivant à scribdoc. cpp, dans la `CScribbleDoc::InitDocument` méthode, après l' `m_sizeDoc = CSize(200,200)` instruction.

   ```cpp
   // Reset the ribbon UI to its initial values
   CMFCRibbonBar* pRibbon =
       ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
   ASSERT_VALID(pRibbon);

   CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
       CMFCRibbonColorButton,
       pRibbon->FindByID(ID_PEN_COLOR));

   // Set ColorButton to black
   pColorBtn->SetColor(RGB(0, 0, 0));

   CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THIN_WIDTH));

   // Set Thin pen combobox to 2
   pThinComboBox->SelectItem(1);

   CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THICK_WIDTH));

   // Set Thick pen combobox to 5
   pThickComboBox->SelectItem(0);
   ```

1. Enregistrer un dessin en couleur dans un fichier. Ajoutez l’instruction suivante à scribdoc. cpp, dans la `CStroke::Serialize` méthode, après l' `ar << (WORD)m_nPenWidth;` instruction.

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. Enfin, chargez un dessin de couleur à partir d’un fichier. Ajoutez la ligne de code suivante, dans la `CStroke::Serialize` méthode, après l' `m_nPenWidth = w;` instruction.

   ```cpp
   ar >> m_penColor;
   ```

1. À présent, dessinez en couleur et enregistrez votre dessin dans un fichier.

## <a name="conclusion"></a>Conclusion

Vous avez mis à jour l’application Scribble MFC. Utilisez cette procédure pas à pas comme guide lorsque vous modifiez vos applications existantes.

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas](../mfc/walkthroughs-mfc.md)<br/>
[Procédure pas à pas : mise à jour de l’application Scribble MFC (partie 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
