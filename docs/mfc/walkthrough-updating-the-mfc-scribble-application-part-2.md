---
title: 'Procédure pas à pas : Mise à jour de l’Application de Scribble MFC (partie 2) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83caf353ca4a45e3ae834a41062de955a91dbb8a
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952428"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>Procédure pas à pas : mise à jour de l'application Scribble MFC (partie 2)
[Partie 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) de cette procédure pas à pas vous a montré comment ajouter un ruban Office Fluent classique Scribble application. Cette partie présente comment ajouter des panneaux de ruban et des contrôles qui permettent aux utilisateurs au lieu des menus et des commandes.  
  
## <a name="prerequisites"></a>Prérequis  
 [Exemples Visual C++](../visual-cpp-samples.md)  
  
##  <a name="top"></a> Sections  
 Cette partie de la procédure pas à pas comporte les sections suivantes :  
  
- [Ajout de nouveaux panneaux au ruban](#addnewpanel)  
  
- [Ajout d’un volet d’aide au ruban](#addhelppanel)  
  
- [Ajout d’un panneau de stylet au ruban](#addpenpanel)  
  
- [Ajout d’un bouton de couleur pour le ruban](#addcolorbutton)  
  
- [Ajout d’un membre de couleur à la classe de Document](#addcolormember)  
  
- [Initialisation des stylets et l’enregistrement des préférences](#initpensave)  
  
##  <a name="addnewpanel"></a> Ajout de nouveaux panneaux au ruban  
 Ces étapes indiquent comment ajouter un **vue** Panneau de configuration qui contient les deux cases à cocher qui contrôlent la visibilité de la barre d’outils et la barre d’état, et également un **fenêtre** panneau qui contient un fractionnement vertical bouton qui contrôle la création et la disposition des fenêtres de l’interface multidocument (MDI).  
  
#### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>Pour ajouter un panneau d’affichage et le volet de fenêtre à la barre du ruban  
  
1.  Créer un panneau de configuration nommé *vue*, qui a deux cases à cocher Activer/désactiver la barre d’état et la barre d’outils.  
  
    1.  À partir de la **boîte à outils**, faites glisser un **panneau** à la **accueil** catégorie. Puis faites glisser deux **cases à cocher** pour le panneau de configuration.  
  
    2.  Cliquez sur le panneau de configuration pour modifier ses propriétés. Modification **légende** à *vue*.  
  
    3.  Cliquez sur la première case à cocher pour modifier ses propriétés. Modification **ID** à *ID_VIEW_TOOLBAR* et **légende** à *barre d’outils*.  
  
    4.  Cliquez sur la deuxième case à cocher pour modifier ses propriétés. Modification **ID** à *ID_VIEW_STATUS_BAR* et **légende** à *barre d’état*.  
  
2.  Créer un panneau de configuration nommé *fenêtre* qui a un bouton partagé. Lorsqu’un utilisateur clique sur le bouton partagé, un menu contextuel affiche les trois commandes qui sont déjà définis dans l’application Scribble.  
  
    1.  À partir de la **boîte à outils**, faites glisser un **panneau** à la **accueil** catégorie. Puis faites glisser un **bouton** pour le panneau de configuration.  
  
    2.  Cliquez sur le panneau de configuration pour modifier ses propriétés. Modification **légende** à *fenêtre*.  
  
    3.  Cliquez sur le bouton. Modification **légende** à *Windows*, **clés** à *w*, **grande Image Index** à *1* , et **Mode fractionné** à *False*. Puis cliquez sur le bouton de sélection (**...** ) à côté **des éléments de Menu** pour ouvrir le **Éditeur d’éléments** boîte de dialogue.  
  
    4.  Cliquez sur **ajouter** trois fois pour ajouter trois boutons.  
  
    5.  Cliquez sur le premier bouton et redéfinissez **légende** à *nouvelle fenêtre*, et **ID** à *ID_WINDOW_NEW*.  
  
    6.  Cliquez sur le deuxième bouton et redéfinissez **légende** à *Cascade*, et **ID** à *ID_WINDOW_CASCADE*.  
  
    7.  Cliquez sur le troisième bouton et redéfinissez **légende** à *vignette*, et **ID** à *ID_WINDOW_TILE_HORZ*.  
  
3.  Enregistrer les modifications, puis créer et exécuter l’application. Le **vue** et **fenêtre** panneaux doit être affiché. Cliquez sur les boutons pour confirmer qu’ils fonctionnent correctement.  
  
 [[Sections](#top)]  
  
##  <a name="addhelppanel"></a> Ajout d’un volet d’aide au ruban  
 Maintenant, vous pouvez attribuer deux éléments de menu qui sont définis dans l’application Scribble aux boutons de ruban qui sont nommées **rubriques d’aide** et **sur Scribble**. Les boutons sont ajoutés à un nouveau volet nommé **aide**.  
  
#### <a name="to-add-a-help-panel"></a>Pour ajouter un volet d’aide  
  
1.  À partir de la **boîte à outils**, faites glisser un **panneau** à la **accueil** catégorie. Puis faites glisser deux **boutons** pour le panneau de configuration.  
  
2.  Cliquez sur le panneau de configuration pour modifier ses propriétés. Modification **légende** à *aide*.  
  
3.  Cliquez sur le premier bouton. Modification **légende** à *rubriques d’aide*, et **ID** à *ID_HELP_FINDER*.  
  
4.  Cliquez sur le deuxième bouton. Modification **légende** à *sur Scribble...* , et **ID** à *ID_APP_ABOUT*.  
  
5.  Enregistrer les modifications, puis créer et exécuter l’application. A **aide** Panneau de configuration qui contient deux boutons de ruban doit être affiché.  
  
    > [!IMPORTANT]
    >  Lorsque vous cliquez sur le **rubriques d’aide** bouton, l’application Scribble ouvre un fichier d’aide HTML (.chm) compressé nommé *your_project_name*. chm. Par conséquent, si votre projet n’est pas appelé Scribble, vous devez renommer le fichier d’aide pour le nom de votre projet.  
  
 [[Sections](#top)]  
  
##  <a name="addpenpanel"></a> Ajout d’un panneau de stylet au ruban  
 Maintenant, ajoutez un panneau de configuration pour afficher des boutons qui contrôlent l’épaisseur et la couleur du stylet. Ce volet contient une case à cocher qui bascule entre les stylets épais et dynamiques. Ses fonctionnalités semblable à celle de la **trait épais** élément de menu dans l’application Scribble.  
  
 L’application Scribble d’origine permet à l’utilisateur de sélectionner les largeurs de stylet à partir d’une boîte de dialogue qui s’affiche lorsque l’utilisateur clique sur **largeurs de stylet** dans le menu. Étant donné que la barre du ruban a suffisamment d’espace libre pour les nouveaux contrôles, vous pouvez remplacer la boîte de dialogue à l’aide de deux zones de liste déroulante du ruban. Une zone de liste déroulante ajuste la largeur du stylet dynamique et l’autre zone de liste déroulante ajuste la largeur du stylet épais.  
  
#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>Pour ajouter un panneau de configuration du stylet et de la liste déroulante des zones au ruban  
  
1.  À partir de la **boîte à outils**, faites glisser un **panneau** à la **accueil** catégorie. Puis faites glisser un **case à cocher** et deux **zones de liste déroulante** pour le panneau de configuration.  
  
2.  Cliquez sur le panneau de configuration pour modifier ses propriétés. Modification **légende** à *stylet*.  
  
3.  Cliquez sur la case à cocher. Modification **légende** à *utiliser épais*, et **ID** à *ID_PEN_THICK_OR_THIN*.  
  
4.  Cliquez sur la première zone de liste déroulante. Modification **légende** à *mince stylet*, **ID** à *ID_PEN_THIN_WIDTH*, **texte** à *2* , **Type** à *liste déroulante*, et **données** à *1 ; 2 ; 3 ; 4 ; 5 ; 6 ; 7 ; 8 ; 9 ;*.  
  
5.  Cliquez sur la deuxième zone de liste déroulante. Modification **légende** à *stylet épais*, **ID** à *ID_PEN_THICK_WIDTH*, **texte** à  *5*, **type** à *liste déroulante*, et **données** à *5 ; 6 ; 7 ; 8 ; 9 ; 10 ; 11 ; 12 ; 13 ; 14 ; 15 ; 16 ; 17 ; 18 ; 19 ; 20 ;*.  
  
6.  Zones de liste déroulante nouveau ne correspondent pas à tous les éléments de menu existants. Par conséquent, vous devez créer un élément de menu pour chaque option de stylet.  
  
    1.  Dans le **affichage des ressources** fenêtre, ouvrez la ressource de menu IDR_SCRIBBTYPE.  
  
    2.  Cliquez sur **stylet** pour ouvrir la p**en** menu. Puis cliquez sur **Type ici** et type *si & n stylet*.  
  
    3.  Cliquez sur le texte que vous venez de taper pour ouvrir la **propriétés** fenêtre, puis modifier l’ID de la propriété à *ID_PEN_THIN_WIDTH*.  
  
    4.  Vous devez également créer un gestionnaire d’événements pour chaque élément de menu du stylet. Cliquez sur le **si & n stylet** élément de menu que vous venez de créer, puis sur **ajouter un gestionnaire d’événements**. Le **Assistant Gestionnaire d’événements** s’affiche.  
  
    5.  Dans le **liste de classes** zone dans l’Assistant, sélectionnez **CScribbleDoc** puis cliquez sur **ajouter et modifier des**. Cette opération crée un gestionnaire d’événements nommé `CScribbleDoc::OnPenThinWidth`.  
  
    6.  Ajoutez le code suivant à `CScribbleDoc::OnPenThinWidth`.  
  
 ``` *Obtenir un pointeur vers le ruban barre CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd()) -> GetRibbonBar() ; ASSERT_VALID(pRibbon) ; */ / Obtenir un pointeur vers la zone de liste déroulante de largeur dynamique CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST (CMFCRibbonComboBox, pRibbon -> FindByID(ID_PEN_THIN_WIDTH)) ; * //Get la valeur sélectionnée  
    int nCurSel = pThinComboBox -> GetCurSel() ; Si (nCurSel > = 0)  
{  
m_nThinWidth = atoi (pThinComboBox -> GetItem(nCurSel)) ;

 } * / / Créer une nouvelle plume à l’aide de la largeur sélectionnée  
    ReplacePen() ;

 ```  
  
7.  Next, create a menu item and event handlers for the thick pen.  
  
    1.  In the **Resource View** window, open the IDR_SCRIBBTYPE menu resource.  
  
    2.  Click **Pen** to open the pen menu. Then click **Type Here** and type *Thic&k Pen*.  
  
    3.  Right-click the text that you just typed to display the **Properties** window. Change the ID property to *ID_PEN_THICK_WIDTH*.  
  
    4.  Right-click the **Thick Pen** menu item that you just created and then click **Add Event Handler**. The **Event Handler Wizard** is displayed.  
  
    5.  In the **Class list** box of the wizard, select **CScribbleDoc** and then click **Add and Edit**. This creates an event handler named `CScribbleDoc::OnPenThickWidth`.  
  
    6.  Add the following code to `CScribbleDoc::OnPenThickWidth`.  
  
 ``` *// Get a pointer to the ribbon bar  
    CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();
ASSERT_VALID(pRibbon);

 CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
    CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));
*// Get the selected value  
    int nCurSel = pThickComboBox->GetCurSel();
if (nCurSel>= 0)  
 {  
    m_nThickWidth = atoi(pThickComboBox->GetItem(nCurSel));

 } *// Create a new pen using the selected width  
    ReplacePen();

 ```  
  
8.  Enregistrer les modifications, puis créer et exécuter l’application. Des boutons et des zones de liste modifiable doivent être affichés. Essayez d’utiliser les largeurs de stylet de dessin à main levée.  
  
 [[Sections](#top)]  
  
##  <a name="addcolorbutton"></a> Ajout d’un bouton de couleur dans le panneau du stylet  
 Ensuite, ajoutez un [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md) objet qui permet à l’utilisateur de scribble en couleur.  
  
#### <a name="to-add-a-color-button-to-the-pen-panel"></a>Pour ajouter un bouton de couleur dans le panneau du stylet  
  
1.  Avant d’ajouter le bouton de couleur, créer un élément de menu pour celui-ci. Dans le **affichage des ressources** fenêtre, ouvrez la ressource de menu IDR_SCRIBBTYPE. Cliquez sur le **stylet** élément de menu pour ouvrir le menu de stylet. Puis cliquez sur **Type ici** et type *& couleur*. Cliquez sur le texte que vous venez de taper pour afficher le **propriétés** fenêtre. Modifier le code pour *ID_PEN_COLOR*.  
  
2.  Maintenant, ajoutez le bouton de couleur. À partir de la **boîte à outils**, faites glisser un **bouton de couleur** à la **stylet** Panneau de configuration.  
  
3.  Cliquez sur le bouton de couleur. Modification **légende** à *couleur*, **ID** à *ID_PEN_COLOR*, **SimpleLook** à  *True*, **grande Image Index** à *1*, et **Mode fractionné** à *False*.  
  
4.  Enregistrer les modifications, puis créer et exécuter l’application. Le nouveau bouton de couleur doit être affiché sur le **stylet** Panneau de configuration. Toutefois, il ne peut pas être utilisé car il n’a pas encore d’un gestionnaire d’événements. Les étapes suivantes montrent comment ajouter un gestionnaire d’événements pour le bouton de couleur.  
  
 [[Sections](#top)]  
  
##  <a name="addcolormember"></a> Ajout d’un membre de couleur à la classe de Document  
 Car l’application Scribble d’origine ne dispose pas des stylets de couleur, vous devez écrire une implémentation pour eux. Pour stocker la couleur du stylet du document, ajoutez un nouveau membre à la classe de document, `CscribbleDoc.`  
  
#### <a name="to-add-a-color-member-to-the-document-class"></a>Pour ajouter un membre de la couleur à la classe de document  
  
1.  Dans scribdoc.h, dans le `CScribbleDoc` classe, recherchez la `// Attributes` section. Ajoutez les lignes de code suivantes après la définition de la `m_nThickWidth` membre de données.  
  
 ''' * / / La couleur actuelle du stylet  
    COLORREF m_penColor ;  
 ```  
  
2.  Every document contains a list of stokes that the user has already drawn. Every stroke is defined by a `CStroke` object. The `CStroke` class does not include information about pen color. Therefore, you must modify the class. In scribdoc.h, in the `CStroke` class, add the following lines of code after the definition of the `m_nPenWidth` data member.  
  
 ``` *// Pen color for the stroke  
    COLORREF m_penColor;  
 ```  
  
3.  Dans scribdoc.h, ajoutez un nouveau `CStroke` constructeur dont les paramètres spécifient une largeur et une couleur. Ajoutez la ligne suivante de code après la `CStroke(UINT nPenWidth);` instruction.  
  
 ```  
    CStroke(UINT nPenWidth, COLORREF penColor);

 ```  
  
4.  Dans scribdoc.cpp, ajoutez l’implémentation de la nouvelle `CStroke` constructeur. Ajoutez le code suivant après l’implémentation de la `CStroke::CStroke(UINT nPenWidth)` constructeur.  
  
 ''' * / / Actuel du constructeur qui utilise le document largeur et la couleur  
    CStroke::CStroke (UINT nPenWidth, « PenColor » COLORREF)  
 {  
    m_nPenWidth = nPenWidth ;  
    m_penColor = « PenColor » ;  
    m_rectBounding.SetRectEmpty() ;

 }  
 ```  
  
5.  Change the second line of the `CStroke::DrawStroke` method as follows.  
  
 ```  
    Si ( ! penStroke.CreatePen (PS_SOLID, m_nPenWidth, m_penColor))  
 ```  
  
6.  Set the default pen color for the document class. In scribdoc.cpp, add the following lines to `CScribbleDoc::InitDocument`, after the `m_nThickWidth = 5;` statement.  
  
 ``` *// default pen color is black  
    m_penColor = RGB(0,
    0,
    0);

 ```  
  
7.  Dans scribdoc.cpp, modifiez la première ligne de la `CScribbleDoc::NewStroke` méthode à la suivante.  
  
 ```  
    CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);

 ```  
  
8.  Modifier la dernière ligne de la `CScribbleDoc::ReplacePen` méthode à la suivante.  
  
 ```  
    m_penCur.CreatePen(PS_SOLID,
    m_nPenWidth,
    m_penColor);

 ```  
  
9. Vous avez ajouté le `m_penColor` membre à l’étape précédente. À présent, créez un gestionnaire d’événements pour le bouton de couleur qui définit le membre.  
  
    1.  Dans le **affichage des ressources** fenêtre, ouvrez la ressource de menu IDR_SCRIBBTYPE.  
  
    2.  Cliquez sur le **couleur** élément de menu et cliquez sur **ajouter un gestionnaire d’événements**. Le **Assistant Gestionnaire d’événements** s’affiche.  
  
    3.  Dans le **liste de classes** zone dans l’Assistant, sélectionnez **CScribbleDoc** puis cliquez sur le **ajouter et modifier des** bouton. Cette opération crée le `CScribbleDoc::OnPenColor` stub de gestionnaire d’événements.  
  
10. Remplacer le stub pour le `CScribbleDoc::OnPenColor` Gestionnaire d’événements avec le code suivant.  
  
 ```  
    void CScribbleDoc::OnPenColor()  
 { *// Change pen color to reflect color button's current selection  
    CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
ASSERT_VALID(pRibbon);

 CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
    CMFCRibbonColorButton, pRibbon->FindByID(ID_PEN_COLOR));

    m_penColor = pColorBtn->GetColor();
*// Create new pen using the selected color  
    ReplacePen();

 }  
 ```  
  
11. Enregistrer les modifications puis générer et exécuter l’application. Vous devez être en mesure d’appuyer sur le bouton de couleur et de modifier sa couleur.  
  
 [[Sections](#top)]  
  
##  <a name="initpensave"></a> Initialisation des stylets et l’enregistrement des préférences  
 Ensuite, initialisez la couleur et la largeur du stylet. Enfin, enregistrer et charger une couleur de dessin à partir d’un fichier.  
  
#### <a name="to-initialize-controls-on-the-ribbon-bar"></a>Pour initialiser les contrôles sur la barre du ruban  
  
1.  Initialiser les stylets sur la barre du ruban.  
  
     Ajoutez le code suivant à scribdoc.cpp, dans le `CScribbleDoc::InitDocument` (méthode), après la `m_sizeDoc = CSize(200,200)` instruction.  
  
 ``` *Réinitialiser l’interface utilisateur du ruban sur ses valeurs initiales CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd()) -> GetRibbonBar() ; ASSERT_VALID(pRibbon) ;

 CMFCRibbonColorButton * pColorBtn = DYNAMIC_DOWNCAST (CMFCRibbonColorButton, pRibbon -> FindByID(ID_PEN_COLOR)) ; * / / Définir ColorButton noir  
    pColorBtn -> SetColor (RVB (0, 0, 0)) ;

 PThinComboBox CMFCRibbonComboBox * = DYNAMIC_DOWNCAST (CMFCRibbonComboBox, pRibbon -> FindByID(ID_PEN_THIN_WIDTH)) ; * / / Définir combobox Plume fin 2  
    pThinComboBox -> SelectItem(1) ;

 PThickComboBox CMFCRibbonComboBox * = DYNAMIC_DOWNCAST (CMFCRibbonComboBox, pRibbon -> FindByID(ID_PEN_THICK_WIDTH)) ; * / / Définir combobox stylet épais à 5  
    pThickComboBox -> SelectItem(0) ;

 ```  
  
2.  Save a color drawing to a file. Add the following statement to scribdoc.cpp, in the `CStroke::Serialize` method, after the `ar << (WORD)m_nPenWidth;` statement.  
  
 ```  
    ar << (COLORREF) m_penColor ;  
 ```  
  
3.  Finally, load a color drawing from a file. Add the following line of code, in the `CStroke::Serialize` method, after the `m_nPenWidth = w;` statement.  
  
 ```  
    ar >> m_penColor ;  
 ```  
  
4.  Now scribble in color and save your drawing to a file.  
  
 [[Sections](#top)]  
  
## Conclusion  
 You have updated the MFC Scribble application. Use this walkthrough as a guide when you modify your existing applications.  
  
## See Also  
 [Walkthroughs](../mfc/walkthroughs-mfc.md)   
 [Walkthrough: Updating the MFC Scribble Application (Part 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)

