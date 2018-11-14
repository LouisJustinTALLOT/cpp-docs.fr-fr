---
title: "Procédure pas à pas : mise à jour de l'application Scribble MFC (partie 2)"
ms.date: 09/20/2018
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
ms.openlocfilehash: 6a52486658307f001001e91772dad1167730def2
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519267"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>Procédure pas à pas : mise à jour de l'application Scribble MFC (partie 2)

[Partie 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) de cette procédure pas à pas vous a montré comment ajouter un ruban d’Office Fluent à classique Scribble application. Cette partie montre comment ajouter des panneaux de ruban et les contrôles que les utilisateurs peuvent utiliser au lieu des menus et des commandes.

## <a name="prerequisites"></a>Prérequis

[Exemples Visual C++](../visual-cpp-samples.md)

##  <a name="top"></a> Sections

Cette partie de la procédure pas à pas comporte les sections suivantes :

- [Ajout de nouveaux panneaux au ruban](#addnewpanel)

- [Ajout d’un volet d’aide au ruban](#addhelppanel)

- [Ajout d’un panneau de stylet au ruban](#addpenpanel)

- [Ajout d’un bouton de couleur au ruban](#addcolorbutton)

- [Ajout d’un membre de la couleur à la classe de Document](#addcolormember)

- [Initialisation des stylets et l’enregistrement des préférences](#initpensave)

##  <a name="addnewpanel"></a> Ajout de nouveaux panneaux au ruban

Ces étapes montrent comment ajouter un **vue** panneau qui contient les deux cases à cocher qui contrôlent la visibilité de la barre d’outils et de la barre d’état, et également un **fenêtre** panneau qui contient un fractionnement orienté verticalement bouton qui contrôle la création et la disposition des fenêtres d’interface multidocument (MDI).

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>Pour ajouter un panneau d’affichage et le volet de fenêtre à la barre du ruban

1. Créer un panneau nommé `View`, qui a deux cases à cocher Activer/désactiver la barre d’état et la barre d’outils.

   1. À partir de la **boîte à outils**, faites glisser un **panneau** à la **accueil** catégorie. Puis faites glisser deux **cases à cocher** au panneau.

   1. Cliquez sur le panneau de configuration pour modifier ses propriétés. Modification **légende** à `View`.

   1. Cliquez sur la première case à cocher pour modifier ses propriétés. Modification **ID** à `ID_VIEW_TOOLBAR` et **légende** à `Toolbar`.

   1. Cliquez sur la deuxième case à cocher pour modifier ses propriétés. Modification **ID** à `ID_VIEW_STATUS_BAR` et **légende** à `Status Bar`.

1. Créer un panneau nommé `Window` qui a un bouton partagé. Lorsqu’un utilisateur clique sur le bouton partagé, un menu contextuel affiche les trois commandes qui sont déjà définis dans l’application Scribble.

   1. À partir de la **boîte à outils**, faites glisser un **panneau** à la **accueil** catégorie. Puis faites glisser un **bouton** au panneau.

   1. Cliquez sur le panneau de configuration pour modifier ses propriétés. Modification **légende** à `Window`.

   1. Cliquez sur le bouton. Modification **légende** à `Windows`, **clés** à `w`, **grande Image Index** à `1`, et **Mode fractionné** à `False`. Puis cliquez sur le bouton de sélection (**...** ) à côté **des éléments de Menu** pour ouvrir le **Éditeur d’éléments** boîte de dialogue.

   1. Cliquez sur **ajouter** trois fois pour ajouter trois boutons.

   1. Cliquez sur le premier bouton et redéfinissez **légende** à `New Window`, et **ID** à `ID_WINDOW_NEW`.

   1. Cliquez sur le deuxième bouton et redéfinissez **légende** à `Cascade`, et **ID** à `ID_WINDOW_CASCADE`.

   1. Cliquez sur le troisième bouton, puis modifiez **légende** à `Tile`, et **ID** à `ID_WINDOW_TILE_HORZ`.

1. Enregistrer les modifications, puis générer et exécuter l’application. Le **vue** et **fenêtre** panneaux doivent être affichés. Cliquez sur les boutons pour confirmer qu’ils fonctionnent correctement.

##  <a name="addhelppanel"></a> Ajout d’un volet d’aide au ruban

Maintenant, vous pouvez affecter deux éléments de menu qui sont définis dans l’application Scribble aux boutons de ruban qui sont nommés **rubriques d’aide** et **sur Scribble**. Les boutons sont ajoutés à un nouveau volet nommé **aide**.

### <a name="to-add-a-help-panel"></a>Pour ajouter un volet d’aide

1. À partir de la **boîte à outils**, faites glisser un **panneau** à la **accueil** catégorie. Puis faites glisser deux **boutons** au panneau.

1. Cliquez sur le panneau de configuration pour modifier ses propriétés. Modification **légende** à `Help`.

1. Cliquez sur le premier bouton. Modification **légende** à `Help Topics`, et **ID** à `ID_HELP_FINDER`.

1. Cliquez sur le deuxième bouton. Modification **légende** à `About Scribble...`, et **ID** à `ID_APP_ABOUT`.

1. Enregistrer les modifications, puis générer et exécuter l’application. Un **aide** panneau qui contient deux boutons de ruban doit être affiché.

   > [!IMPORTANT]
   > Lorsque vous cliquez sur le **rubriques d’aide** bouton, l’application Scribble ouvre un fichier d’aide HTML (.chm) compressé nommé *your_project_name*. chm. Par conséquent, si votre projet n’est pas nommé Scribble, vous devez renommer le fichier d’aide pour le nom de votre projet.

##  <a name="addpenpanel"></a> Ajout d’un panneau de stylet au ruban

Maintenant, ajoutez un panneau pour afficher des boutons qui contrôlent l’épaisseur et la couleur du stylet. Ce volet contient une case à cocher qui fait basculer entre les stylets épaisses et légères. Sa fonctionnalité semblable à celle de la **trait épais** élément de menu dans l’application Scribble.

L’application Scribble d’origine permet à l’utilisateur de sélectionner les largeurs de stylet dans une boîte de dialogue qui s’affiche lorsque l’utilisateur clique sur **largeurs de stylet** dans le menu. Étant donné que la barre du ruban possède suffisamment d’espace libre pour les nouveaux contrôles, vous pouvez remplacer la boîte de dialogue à l’aide de deux zones de liste déroulante du ruban. Une zone de liste déroulante ajuste la largeur du stylet dynamique et l’autre zone de liste déroulante ajuste la largeur du stylet épaisse.

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Pour ajouter un panneau de stylet et de la liste déroulante des zones au ruban

1. À partir de la **boîte à outils**, faites glisser un **panneau** à la **accueil** catégorie. Puis faites glisser un **case à cocher** et deux **zones de liste déroulante** au panneau.

1. Cliquez sur le panneau de configuration pour modifier ses propriétés. Modification **légende** à `Pen`.

1. Cliquez sur la case à cocher. Modification **légende** à `Use Thick`, et **ID** à `ID_PEN_THICK_OR_THIN`.

1. Cliquez sur la première zone de liste déroulante. Modification **légende** à `Thin Pen`, **ID** à `ID_PEN_THIN_WIDTH`, **Type** à `Drop List`, **données** à `1;2;3;4;5;6;7;8;9;`, et **texte** à `2`.

1. Cliquez sur la deuxième zone de liste déroulante. Modification **légende** à `Thick Pen`, **ID** à `ID_PEN_THICK_WIDTH`, **Type** à `Drop List`, **données** à `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`, et **texte** à `5`.

1. Zones de liste déroulante nouveau ne correspondent pas à des éléments de menu existant, vous devez donc créer un élément de menu pour chaque option de stylet.

   1. Dans le **affichage des ressources** fenêtre, ouvrez le **IDR_SCRIBBTYPE** ressource de menu.

   1. Cliquez sur **stylet** pour ouvrir le menu de stylet. Puis cliquez sur **tapez ici** et type `Thi&n Pen`.

   1. Cliquez sur le texte que vous avez tapé pour ouvrir le **propriétés** fenêtre, puis modifier l’ID de la propriété à `ID_PEN_THIN_WIDTH`.

   1. Créer un gestionnaire d’événements pour chaque élément de menu de stylet. Avec le bouton droit le **Thi & n stylet** élément de menu que vous avez créé et puis cliquez sur **ajouter un gestionnaire d’événements**. Le **Assistant Gestionnaire d’événements** s’affiche.

   1. Dans le **liste de classe** zone dans l’Assistant, sélectionnez **CScribbleDoc** puis cliquez sur **ajouter et modifier des**. La commande crée un gestionnaire d’événements nommé `CScribbleDoc::OnPenThinWidth`.

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

1. Ensuite, créez un menu élément et gestionnaires d’événements pour le stylet de type « définitif ».

   1. Dans le **affichage des ressources** fenêtre, ouvrez le **IDR_SCRIBBTYPE** ressource de menu.

   1. Cliquez sur **stylet** pour ouvrir le menu de stylet. Puis cliquez sur **tapez ici** et type `Thic&k Pen`.

   1. Cliquez sur le texte que vous avez tapé pour afficher le **propriétés** fenêtre. Affectez à la propriété ID `ID_PEN_THICK_WIDTH`.

   1. Avec le bouton droit le **Plume épaisse** élément de menu que vous avez créé et puis cliquez sur **ajouter un gestionnaire d’événements**. Le **Assistant Gestionnaire d’événements** s’affiche.

   1. Dans le **liste de classe** boîte de l’Assistant, sélectionnez **CScribbleDoc** puis cliquez sur **ajouter et modifier des**. La commande crée un gestionnaire d’événements nommé `CScribbleDoc::OnPenThickWidth`.

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

1. Enregistrer les modifications, puis générer et exécuter l’application. Nouveaux boutons et zones de liste déroulante doivent être affichés. Essayez d’utiliser les largeurs de stylet à dessin à main levée.

##  <a name="addcolorbutton"></a> Ajout d’un bouton de couleur dans le panneau de stylet

Ensuite, ajoutez un [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) objet qui permet à l’utilisateur de scribble en couleur.

### <a name="to-add-a-color-button-to-the-pen-panel"></a>Pour ajouter un bouton de couleur dans le panneau de stylet

1. Avant d’ajouter le bouton de couleur, créez un élément de menu pour celui-ci. Dans le **affichage des ressources** fenêtre, ouvrez le **IDR_SCRIBBTYPE** ressource de menu. Cliquez sur le **stylet** élément de menu pour ouvrir le menu de stylet. Puis cliquez sur **tapez ici** et type `&Color`. Cliquez sur le texte que vous avez tapé pour afficher le **propriétés** fenêtre. Modifiez l’ID en lui attribuant la valeur `ID_PEN_COLOR`.

1. Ajoutez maintenant le bouton de couleur. À partir de la **boîte à outils**, faites glisser un **bouton de couleur** à la **stylet** Panneau de configuration.

1. Cliquez sur le bouton de couleur. Modification **légende** à `Color`, **ID** à `ID_PEN_COLOR`, **Simple Look** à `True`, **grande Image Index** à `1`, et **Mode fractionné** à `False`.

1. Enregistrer les modifications, puis générer et exécuter l’application. Le nouveau bouton de couleur doit s’afficher sur le **stylet** Panneau de configuration. Toutefois, il ne peut pas être utilisé car il ne dispose pas encore un gestionnaire d’événements. Les étapes suivantes montrent comment ajouter un gestionnaire d’événements pour le bouton de couleur.

##  <a name="addcolormember"></a> Ajout d’un membre de la couleur à la classe de Document

Étant donné que l’application Scribble d’origine n’a pas les stylets de couleur, vous devez écrire une implémentation pour eux. Pour stocker la couleur du stylet du document, ajouter un nouveau membre à la classe de document, `CscribbleDoc`.

### <a name="to-add-a-color-member-to-the-document-class"></a>Pour ajouter un membre de couleur à la classe de document

1. Dans scribdoc.h, dans le `CScribbleDoc` classe, recherchez la `// Attributes` section. Ajoutez les lignes de code suivantes après la définition de la `m_nThickWidth` membre de données.

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. Chaque document contient une liste de stokes que l’utilisateur a déjà dessiné. Chaque trait est défini par un `CStroke` objet. Le `CStroke` classe n’inclut pas d’informations sur la couleur du stylet, vous devez modifier la classe. Dans scribdoc.h, dans le `CStroke` de classe, ajoutez les lignes de code suivantes après la définition de la `m_nPenWidth` membre de données.

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. Dans scribdoc.h, ajoutez un nouveau `CStroke` constructeur dont les paramètres spécifient une largeur et une couleur. Ajoutez la ligne suivante de code après la `CStroke(UINT nPenWidth);` instruction.

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. Dans scribdoc.cpp, ajoutez l’implémentation de la nouvelle `CStroke` constructeur. Ajoutez le code suivant après l’implémentation de la `CStroke::CStroke(UINT nPenWidth)` constructeur.

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

1. Modifier la deuxième ligne de la `CStroke::DrawStroke` méthode comme suit.

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

1. Définir la couleur du stylet par défaut pour la classe de document. Dans scribdoc.cpp, ajoutez les lignes suivantes à `CScribbleDoc::InitDocument`, après la `m_nThickWidth = 5;` instruction.

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. Dans scribdoc.cpp, modifiez la première ligne de la `CScribbleDoc::NewStroke` (méthode) à ce qui suit.

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. Modifier la dernière ligne de la `CScribbleDoc::ReplacePen` (méthode) à ce qui suit.

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. Vous avez ajouté le `m_penColor` membre à l’étape précédente. Maintenant, créez un gestionnaire d’événements pour le bouton de couleur qui définit le membre.

   1. Dans le **affichage des ressources** fenêtre, ouvrez la ressource de menu IDR_SCRIBBTYPE.

   1. Cliquez sur le **couleur** élément de menu et cliquez sur **ajouter un gestionnaire d’événements**. Le **Assistant Gestionnaire d’événements** s’affiche.

   1. Dans le **liste de classe** zone dans l’Assistant, sélectionnez **CScribbleDoc** puis cliquez sur le **ajouter et modifier des** bouton. La commande crée le `CScribbleDoc::OnPenColor` stub de gestionnaire d’événements.

1. Remplacer le stub pour la `CScribbleDoc::OnPenColor` Gestionnaire d’événements par le code suivant.

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

1. Enregistrer les modifications puis générer et exécuter l’application. Vous pouvez maintenant appuyer sur le bouton de couleur et modifier sa couleur.

##  <a name="initpensave"></a> Initialisation des stylets et l’enregistrement des préférences

Ensuite, initialisez la couleur et la largeur du stylet. Enfin, enregistrer et charger une couleur de dessin à partir d’un fichier.

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>Pour initialiser les contrôles sur la barre du ruban

1. Initialiser les stylets sur la barre du ruban.

   Ajoutez le code suivant à scribdoc.cpp, dans le `CScribbleDoc::InitDocument` (méthode), après la `m_sizeDoc = CSize(200,200)` instruction.

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

1. Enregistrer une couleur de dessin à un fichier. Ajoutez l’instruction suivante à scribdoc.cpp, dans le `CStroke::Serialize` (méthode), après la `ar << (WORD)m_nPenWidth;` instruction.

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. Enfin, chargez une couleur de dessin à partir d’un fichier. Ajoutez la ligne suivante de code, dans le `CStroke::Serialize` (méthode), après la `m_nPenWidth = w;` instruction.

   ```cpp
   ar >> m_penColor;
   ```

1. À présent scribble en couleur et enregistrer votre dessin dans un fichier.

## <a name="conclusion"></a>Conclusion

Vous avez mis à jour l’application Scribble MFC. Utilisez cette procédure pas à pas comme guide lorsque vous modifiez vos applications existantes.

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas](../mfc/walkthroughs-mfc.md)<br/>
[Procédure pas à pas : mise à jour de l’application Scribble MFC (partie 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
