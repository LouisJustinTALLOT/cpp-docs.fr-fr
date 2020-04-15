---
title: "Procédure pas à pas : mise à jour de l'application Scribble MFC (partie 2)"
ms.date: 04/25/2019
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
ms.openlocfilehash: bc204a152168accf3731eede8ca9ef960ab121d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360225"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>Procédure pas à pas : mise à jour de l'application Scribble MFC (partie 2)

[La partie 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) de cette procédure pas à pas a montré comment ajouter un ruban de bureau couramment à l’application classique Scribble. Cette partie montre comment ajouter des panneaux de ruban et des contrôles que les utilisateurs peuvent utiliser au lieu de menus et de commandes.

## <a name="prerequisites"></a>Prérequis

[Exemples Visual C++](../overview/visual-cpp-samples.md)

## <a name="sections"></a><a name="top"></a>Sections

Cette partie de la procédure pas à pas a les sections suivantes:

- [Ajout de nouveaux panneaux au ruban](#addnewpanel)

- [Ajout d’un panneau d’aide au ruban](#addhelppanel)

- [Ajout d’un panneau de stylo au ruban](#addpenpanel)

- [Ajout d’un bouton couleur au ruban](#addcolorbutton)

- [Ajout d’un membre couleur à la classe de documents](#addcolormember)

- [Initialiser les stylos et les préférences d’épargne](#initpensave)

## <a name="adding-new-panels-to-the-ribbon"></a><a name="addnewpanel"></a>Ajout de nouveaux panneaux au ruban

Ces étapes montrent comment ajouter un panneau **De vue** qui contient deux cases à cocher qui contrôlent la visibilité de la barre d’outils et de la barre d’état, ainsi qu’un panneau **de fenêtre** qui contient un bouton split orienté verticalement qui contrôle la création et l’arrangement des fenêtres à interface multi-documents (MDI).

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>Pour ajouter un panneau de vue et un panneau de fenêtre à la barre de ruban

1. Créez un `View`panneau nommé , qui dispose de deux cases à cocher qui basculent la barre d’état et la barre d’outils.

   1. De la **boîte à outils,** faites glisser un **panneau** à la catégorie **Accueil.** Ensuite, faites glisser deux cases à **cocher** sur le panneau.

   1. Cliquez sur le panneau pour modifier ses propriétés. Légende **Caption** de `View`changement pour .

   1. Cliquez sur la première case à cocher pour modifier ses propriétés. Modifier **ID** ID `ID_VIEW_TOOLBAR` et `Toolbar` **caption** à .

   1. Cliquez sur la deuxième case à cocher pour modifier ses propriétés. Modifier **ID** ID `ID_VIEW_STATUS_BAR` et `Status Bar` **caption** à .

1. Créez un `Window` panneau nommé qui a un bouton split. Lorsqu’un utilisateur clique sur le bouton split, un menu raccourci affiche trois commandes déjà définies dans l’application Scribble.

   1. De la **boîte à outils,** faites glisser un **panneau** à la catégorie **Accueil.** Ensuite, faites glisser un **bouton** sur le panneau.

   1. Cliquez sur le panneau pour modifier ses propriétés. Légende **Caption** de `Window`changement pour .

   1. Cliquez sur le bouton correspondant. Légende **Caption** de `Windows`changement `w`à , **Keys** to , `False`Large Image **Index** à `1`, et Split **Mode** à . Cliquez ensuite sur l’ellipsis (**...**) à côté **des éléments** de menu pour ouvrir la boîte de dialogue **De l’éditeur d’articles.**

   1. Cliquez **sur Ajouter** trois fois pour ajouter trois boutons.

   1. Cliquez sur le premier bouton, puis `ID_WINDOW_NEW`changer **caption** pour `New Window`, et **ID** à .

   1. Cliquez sur le deuxième bouton, puis `ID_WINDOW_CASCADE`changer **caption** pour `Cascade`, et **ID** à .

   1. Cliquez sur le troisième bouton, puis `ID_WINDOW_TILE_HORZ`changer **caption** pour `Tile`, et **ID** à .

1. Enregistrer les modifications, puis construire et exécuter l’application. Les panneaux **De vue** et **de fenêtre** doivent être affichés. Cliquez sur les boutons pour confirmer qu’ils fonctionnent correctement.

## <a name="adding-a-help-panel-to-the-ribbon"></a><a name="addhelppanel"></a>Ajout d’un panneau d’aide au ruban

Maintenant, vous pouvez attribuer deux éléments de menu qui sont définis dans l’application Scribble aux boutons ruban qui sont nommés **Sujets d’aide** et **à propos de Scribble**. Les boutons sont ajoutés à un nouveau panneau nommé **Help**.

### <a name="to-add-a-help-panel"></a>Pour ajouter un panneau d’aide

1. De la **boîte à outils,** faites glisser un **panneau** à la catégorie **Accueil.** Ensuite, faites glisser deux **boutons** sur le panneau.

1. Cliquez sur le panneau pour modifier ses propriétés. Légende **Caption** de `Help`changement pour .

1. Cliquez sur le premier bouton. Légende **Caption** de `Help Topics`changement pour `ID_HELP_FINDER`, et **ID** à .

1. Cliquez sur le deuxième bouton. Légende **Caption** de `About Scribble...`changement pour `ID_APP_ABOUT`, et **ID** à .

1. Enregistrer les modifications, puis construire et exécuter l’application. Un panneau **d’aide** qui contient deux boutons ruban doit être affiché.

   > [!IMPORTANT]
   > Lorsque vous cliquez sur le bouton **Sujets d’aide,** l’application Scribble ouvre un fichier d’aide HTML compressé (.chm) nommé *your_project_name*.chm. Par conséquent, si votre projet n’est pas nommé Scribble, vous devez renommer le fichier d’aide à votre nom de projet.

## <a name="adding-a-pen-panel-to-the-ribbon"></a><a name="addpenpanel"></a>Ajout d’un panneau de stylo au ruban

Maintenant, ajoutez un panneau pour afficher les boutons qui contrôlent l’épaisseur et la couleur du stylo. Ce panneau contient une case à cocher qui bascule entre les stylos épais et minces. Sa fonctionnalité ressemble à celle de l’élément de menu **Thick Line** dans l’application Scribble.

L’application Scribble d’origine permet à l’utilisateur de sélectionner les largeurs de stylet à partir d’une boîte de dialogue qui apparaît lorsque l’utilisateur clique sur **les largeurs de stylo** sur le menu. Parce que la barre de ruban a amplement de place pour de nouveaux contrôles, vous pouvez remplacer la boîte de dialogue en utilisant deux boîtes combo sur le ruban. Une boîte combo ajuste la largeur du stylo mince et l’autre boîte combo ajuste la largeur du stylo épais.

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Pour ajouter un panneau de stylo et des boîtes combo au ruban

1. De la **boîte à outils,** faites glisser un **panneau** à la catégorie **Accueil.** Ensuite, faites glisser une **case à cocher** et deux **boîtes Combo** sur le panneau.

1. Cliquez sur le panneau pour modifier ses propriétés. Légende **Caption** de `Pen`changement pour .

1. Cliquez sur la case à cocher. Légende **Caption** de `Use Thick`changement pour `ID_PEN_THICK_OR_THIN`, et **ID** à .

1. Cliquez sur la première boîte combo. Légende **Caption** de `Thin Pen`changement `ID_PEN_THIN_WIDTH`à , **ID** `1;2;3;4;5;6;7;8;9;`à , `2` **Type** à `Drop List`, **Données** à , et **Texte** à .

1. Cliquez sur la deuxième boîte combo. Légende **Caption** de `Thick Pen`changement `ID_PEN_THICK_WIDTH`à , **ID** `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`à , `5` **Type** à `Drop List`, **Données** à , et **Texte** à .

1. Les nouvelles boîtes combo ne correspondent pas à des éléments de menu existants, vous devez donc créer un élément de menu pour chaque option de stylo.

   1. Dans la fenêtre **Resource View,** ouvrez la ressource de menu **IDR_SCRIBBTYPE.**

   1. Cliquez sur **Stylo** pour ouvrir le menu stylo. Cliquez ensuite sur `Thi&n Pen`Type **Ici** et tapez .

   1. Cliquez à droite sur le texte que vous avez tapé pour `ID_PEN_THIN_WIDTH`ouvrir la fenêtre **propriété,** puis changez la propriété ID à .

   1. Créez un gestionnaire d’événements pour chaque élément de menu de stylo. Cliquez à droite sur l’élément de menu **Thi&n Pen** que vous avez créé, puis cliquez sur Add Event **Handler**. Le **Wizard De gestionnaire d’événements** est affiché.

   1. Dans la **case de la liste de classe** dans l’assistant, sélectionnez **CScribbleDoc,** puis cliquez sur **Ajouter et modifier**. La commande crée un `CScribbleDoc::OnPenThinWidth`gestionnaire d’événements nommé .

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

1. Ensuite, créez un élément de menu et des gestionnaires d’événements pour le stylo épais.

   1. Dans la fenêtre **Resource View,** ouvrez la ressource de menu **IDR_SCRIBBTYPE.**

   1. Cliquez sur **Stylo** pour ouvrir le menu stylo. Cliquez ensuite sur `Thic&k Pen`Type **Ici** et tapez .

   1. Cliquez à droite sur le texte que vous avez tapé pour afficher la fenêtre **propriété.** Modifier la propriété `ID_PEN_THICK_WIDTH`ID à .

   1. Cliquez à droite sur l’élément du menu **Thick Pen** que vous avez créé, puis cliquez sur Ajouter **Event Handler**. Le **Wizard De gestionnaire d’événements** est affiché.

   1. Dans la **case de classe** de l’assistant, sélectionnez **CScribbleDoc,** puis cliquez sur **Ajouter et modifier**. La commande crée un `CScribbleDoc::OnPenThickWidth`gestionnaire d’événements nommé .

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

1. Enregistrer les modifications, puis construire et exécuter l’application. De nouveaux boutons et boîtes combo doivent être affichés. Essayez d’utiliser différentes largeurs de stylo pour griffonner.

## <a name="adding-a-color-button-to-the-pen-panel"></a><a name="addcolorbutton"></a>Ajout d’un bouton couleur au panneau de stylo

Ensuite, ajoutez un objet [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) qui permet à l’utilisateur de griffonner en couleur.

### <a name="to-add-a-color-button-to-the-pen-panel"></a>Pour ajouter un bouton de couleur au panneau De stylo

1. Avant d’ajouter le bouton couleur, créez un élément de menu pour cela. Dans la fenêtre **Resource View,** ouvrez la ressource de menu **IDR_SCRIBBTYPE.** Cliquez sur l’élément du menu **Pen** pour ouvrir le menu du stylo. Cliquez ensuite sur `&Color`Type **Ici** et tapez . Cliquez à droite sur le texte que vous avez tapé pour afficher la fenêtre **propriété.** Modifiez l’ID en lui attribuant la valeur `ID_PEN_COLOR`.

1. Maintenant, ajoutez le bouton de couleur. De la **boîte à outils,** faites glisser un **bouton de couleur** au panneau de **stylo.**

1. Cliquez sur le bouton couleur. Légende **Caption** de `Color`changement `ID_PEN_COLOR`à , **ID** à , `1` **Simple Look** to `True`, **Large Image Index** à , et Split **Mode** à `False`.

1. Enregistrer les modifications, puis construire et exécuter l’application. Le nouveau bouton couleur doit être affiché sur le panneau **De** stylo. Cependant, il ne peut pas être utilisé parce qu’il n’a pas encore un gestionnaire d’événements. Les prochaines étapes montrent comment ajouter un gestionnaire d’événements pour le bouton de couleur.

## <a name="adding-a-color-member-to-the-document-class"></a><a name="addcolormember"></a>Ajout d’un membre couleur à la classe de documents

Parce que l’application originale Scribble n’a pas de stylos couleur, vous devez écrire une implémentation pour eux. Pour stocker la couleur du stylo du document, ajoutez `CscribbleDoc`un nouveau membre à la classe de documents, .

### <a name="to-add-a-color-member-to-the-document-class"></a>Pour ajouter un membre couleur à la classe de documents

1. Dans scribdoc.h, `CScribbleDoc` dans la `// Attributes` classe, trouver la section. Ajoutez les lignes de code suivantes `m_nThickWidth` après la définition du membre des données.

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. Chaque document contient une liste de stokes que l’utilisateur a déjà dessiné. Chaque course est `CStroke` définie par un objet. La `CStroke` classe n’inclut pas d’informations sur la couleur du stylo, vous devez donc modifier la classe. Dans scribdoc.h, `CStroke` dans la classe, ajouter les lignes `m_nPenWidth` de code suivantes après la définition du membre de données.

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. Dans scribdoc.h, ajoutez `CStroke` un nouveau constructeur dont les paramètres spécifient une largeur et une couleur. Ajoutez la ligne de `CStroke(UINT nPenWidth);` code suivante après la déclaration.

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. Dans scribdoc.cpp, ajoutez la `CStroke` mise en œuvre du nouveau constructeur. Ajoutez le code suivant après `CStroke::CStroke(UINT nPenWidth)` la mise en œuvre du constructeur.

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

1. Modifier la deuxième `CStroke::DrawStroke` ligne de la méthode comme suit.

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

1. Définissez la couleur du stylo par défaut pour la classe de documents. Dans scribdoc.cpp, ajoutez les `CScribbleDoc::InitDocument`lignes `m_nThickWidth = 5;` suivantes à , après la déclaration.

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. Dans scribdoc.cpp, changez la `CScribbleDoc::NewStroke` première ligne de la méthode en ce qui suit.

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. Changez la dernière `CScribbleDoc::ReplacePen` ligne de la méthode en ce qui suit.

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. Vous avez `m_penColor` ajouté le membre dans une étape précédente. Maintenant, créez un gestionnaire d’événement pour le bouton de couleur qui définit le membre.

   1. Dans la fenêtre **Resource View,** ouvrez la ressource de menu IDR_SCRIBBTYPE.

   1. Cliquez à droite sur l’élément du menu **Couleur** et cliquez sur **Ajouter Event Handler**. Le **Magicien de gestionnaire d’événements** apparaît.

   1. Dans la **case de la liste de classe** de l’assistant, sélectionnez **CScribbleDoc,** puis cliquez sur le bouton **Ajouter et modifier.** La commande `CScribbleDoc::OnPenColor` crée le talon de gestionnaire d’événement.

1. Remplacez le talon `CScribbleDoc::OnPenColor` pour le gestionnaire de l’événement par le code suivant.

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

1. Enregistrer les modifications, puis construire et exécuter l’application. Vous pouvez maintenant appuyer sur le bouton de couleur et changer la couleur du stylo.

## <a name="initializing-pens-and-saving-preferences"></a><a name="initpensave"></a>Initialiser les stylos et les préférences d’épargne

Ensuite, initialiser la couleur et la largeur des stylos. Enfin, enregistrer et charger un dessin de couleur à partir d’un fichier.

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>Pour initialiser les contrôles sur la barre de ruban

1. Initialiser les stylos sur la barre de ruban.

   Ajoutez le code suivant à scribdoc.cpp, dans la `CScribbleDoc::InitDocument` méthode, après la `m_sizeDoc = CSize(200,200)` déclaration.

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

1. Enregistrez un dessin de couleur sur un fichier. Ajoutez la déclaration suivante à scribdoc.cpp, dans la `CStroke::Serialize` méthode, après la `ar << (WORD)m_nPenWidth;` déclaration.

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. Enfin, chargez un dessin de couleur à partir d’un fichier. Ajoutez la ligne de code `CStroke::Serialize` suivante, `m_nPenWidth = w;` dans la méthode, après la déclaration.

   ```cpp
   ar >> m_penColor;
   ```

1. Maintenant griffonner de couleur et enregistrer votre dessin à un fichier.

## <a name="conclusion"></a>Conclusion

Vous avez mis à jour l’application MFC Scribble. Utilisez cette procédure pas à pas comme guide lorsque vous modifiez vos applications existantes.

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas](../mfc/walkthroughs-mfc.md)<br/>
[Procédure pas à pas : mise à jour de l’application Scribble MFC (partie 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
