---
title: 'Procédure pas à pas : Ajout d’un objet D2D à un projet MFC | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7985b36c0eeaa7adf5441a7a6fbb3314bac8353f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384018"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>Procédure pas à pas : ajout d'un objet D2D à un projet MFC
Cette procédure pas à pas explique comment ajouter une base Direct2D (D2D) de l’objet à un Visual C++, le projet de bibliothèque de classes Microsoft Foundation (MFC) et ensuite générer le projet dans une application qui imprime « Hello, world » sur un arrière-plan dégradé.  
  
 La procédure pas à pas montre comment accomplir ces tâches :  
  
-   Créer une application MFC.  
  
-   Créer un pinceau de couleur unie et un pinceau de dégradé linéaire.  
  
-   Modifier le pinceau de dégradé afin qu’elle deviendra correctement lorsque la fenêtre est redimensionnée.  
  
-   Implémentez un gestionnaire de dessin D2D.  
  
-   Vérifier les résultats.  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure pas à pas, vous devez disposer de Visual Studio.  
  
### <a name="to-create-an-mfc-application"></a>Pour créer une application MFC  
  
1.  Dans le menu **Fichier** , pointez sur **Nouveau** , puis cliquez sur **Projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, dans le volet gauche sous **modèles installés**, développez **Visual C++** , puis sélectionnez **MFC**. Dans le volet central, sélectionnez **Application MFC**. Dans la zone **Nom**, tapez `MFCD2DWalkthrough`. Cliquez sur **OK**.  
  
3.  Dans le **Assistant Application MFC**, cliquez sur **Terminer** sans modifier les paramètres.  
  
### <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>Pour créer un pinceau de couleur unie et un pinceau de dégradé linéaire  
  
1.  Dans **l’Explorateur de solutions**, dans le **MFCD2DWalkthrough** de projet, dans le **fichiers d’en-tête** dossier, ouvrez MFCD2DWalkthroughView.h. Ajoutez le code suivant à la `CMFCD2DWalkthroughView` classe à créer trois variables de données.  
  
 ```  
    CD2DTextFormat* m_pTextFormat;  
    CD2DSolidColorBrush* m_pBlackBrush;  
    CD2DLinearGradientBrush* m_pLinearGradientBrush;  
 ```  
  
     Enregistrez le fichier et fermez-le.  
  
2.  Dans le **fichiers sources** dossier, ouvrez MFCD2DWalkthroughView.cpp. Dans le constructeur de la `CMFCD2DWalkthroughView` de classe, ajoutez le code suivant.  
  
 ''' * / / Activer la prise en charge D2D pour cette fenêtre :  
    EnableD2DSupport() ;

 * / / Initialiser les ressources D2D :  
    m_pBlackBrush = nouveau CD2DSolidColorBrush(GetRenderTarget(), D2D1::ColorF(D2D1::ColorF::Black)) ;

 
    m_pTextFormat = nouveau CD2DTextFormat(GetRenderTarget(), _T("Verdana"), 50) ;

    m_pTextFormat -> Get() -> SetTextAlignment(DWRITE_TEXT_ALIGNMENT_CENTER) ;

 m_pTextFormat -> Get() -> SetParagraphAlignment(DWRITE_PARAGRAPH_ALIGNMENT_CENTER) ;

 
    D2D1_GRADIENT_STOP gradientStops [2] ;  
 
    gradientStops [0] .color = D2D1::ColorF(D2D1::ColorF::White) ;

    gradientStops [0] .position = 0.f ;  
    gradientStops [1] .color = D2D1::ColorF(D2D1::ColorF::Indigo) ;

    gradientStops [1] .position = 1.f ne le ;  
 
    m_pLinearGradientBrush = CD2DLinearGradientBrush(GetRenderTarget() nouveau,   
    gradientStops, ARRAYSIZE(gradientStops),  
    D2D1::LinearGradientBrushProperties (D2D1::Point2F (0, 0), D2D1::Point2F (0, 0))) ;

 ```  
  
     Save the file and close it.  
  
### To modify the gradient brush so that it will change appropriately when the window is resized  
  
1.  On the **Project** menu, click **Class Wizard**.  
  
2.  In the **MFC Class Wizard**, under **Class name**, select `CMFCD2DWalkthroughView`.  
  
3.  On the **Messages** tab, in the **Messages** box, select `WM_SIZE` and then click **Add Handler**. This action adds the `OnSize` message handler to the `CMFCD2DWalkthroughView` class.  
  
4.  In the **Existing handlers** box, select `OnSize`. Click **Edit Code** to display the `CMFCD2DWalkthroughView::OnSize` method. At the end of the method, add the following code.  
  
 ```  
    m_pLinearGradientBrush -> SetEndPoint (CPoint (cx, cy)) ;

 ```  
  
     Save the file and close it.  
  
### To implement a D2D drawing handler  
  
1.  On the **Project** menu, click **Class Wizard**.  
  
2.  In the **MFC Class Wizard**, under **Class name**, select `CMFCD2DWalkthroughView`.  
  
3.  On the **Messages** tab, click **Add Custom Message**.  
  
4.  In the **Add Custom Message** dialog box, in the **Custom Windows Message** box, type `AFX_WM_DRAW2D`. In the **Message handler name** box, type `OnDraw2D`. Select the **Registered Message** option and then click **OK**. This action adds a message handler for the `AFX_WM_DRAW2D` message to the `CMFCD2DWalkthroughView` class.  
  
5.  In the **Existing handlers** box, select `OnDraw2D`. Click **Edit Code** to display the `CMFCD2DWalkthroughView::OnDraw2D` method. Use the following code for the `CMFCD2DWalkthroughView::OnDrawD2D` method.  
  
 ```  
    afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(WPARAM wParam, LPARAM lParam)  
    {  
 PRenderTarget CHwndRenderTarget * = (CHwndRenderTarget *) lParam ;  
    ASSERT_VALID(pRenderTarget) ;

 
    CRect rect ;  
    GetClientRect(rect) ;

 
    pRenderTarget -> FillRectangle (rect, m_pLinearGradientBrush) ;

    pRenderTarget -> DrawText (rect (« Hello, World ! ») de _T, m_pBlackBrush, m_pTextFormat) ;

 
    Renvoie la valeur TRUE ;  
 }  
 ```  
  
     Save the file and close it.  
  
### To verify the results  
  
1.  Build and run the application. It should have a gradient rectangle that changes when you resize the window. “Hello World!” should be displayed in the center of the rectangle.  
  
## See Also  
 [Walkthroughs](../mfc/walkthroughs-mfc.md)

