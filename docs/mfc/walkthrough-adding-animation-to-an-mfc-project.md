---
description: 'En savoir plus sur : procédure pas à pas : ajout d’une animation à un projet MFC'
title: "Procédure pas à pas : ajout d'une animation à un projet MFC"
ms.date: 04/25/2019
helpviewer_keywords:
- animation [MFC]
- MFC, animation
ms.assetid: 004f832c-9fd5-4f88-9ca9-ae65dececdc2
ms.openlocfilehash: ef6d6fc8e17c8e6dc4c6f0f4e8d7407f2690927f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143115"
---
# <a name="walkthrough-adding-animation-to-an-mfc-project"></a>Procédure pas à pas : ajout d'une animation à un projet MFC

Cette procédure pas à pas explique comment ajouter un objet animé de base à un projet Visual C++, bibliothèque MFC (Microsoft Foundation Class) (MFC).

La procédure pas à pas montre comment accomplir ces tâches :

- Créez une application MFC.

- Ajoutez un menu, puis ajoutez des commandes pour démarrer et arrêter une animation.

- Créez des gestionnaires pour les commandes de démarrage et d’arrêt.

- Ajoutez un objet animé au projet.

- Centrez l’objet animé dans la fenêtre.

- Vérifiez les résultats.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prérequis

Pour effectuer cette procédure pas à pas, vous devez disposer de Visual Studio.

### <a name="to-create-an-mfc-application"></a>Pour créer une application MFC

1. Utilisez l' **Assistant Application MFC** pour créer une application MFC. Consultez [procédure pas à pas : utilisation des nouveaux contrôles de l’interpréteur de commandes MFC](walkthrough-using-the-new-mfc-shell-controls.md) pour obtenir des instructions sur l’ouverture de l’Assistant pour votre version de Visual Studio.

1. Dans la zone **nom** , tapez *MFCAnimationWalkthrough*. Cliquez sur **OK**.

1. Dans la boîte de dialogue **Assistant Application MFC** , vérifiez que le **type d’application** est **plusieurs documents**, que le **style de projet** est **Visual Studio** et que l’option **prise en charge de l’architecture document/vue** est sélectionnée. Cliquez sur **Terminer**.

### <a name="to-add-a-menu-and-then-add-commands-to-start-and-stop-an-animation"></a>Pour ajouter un menu, puis ajouter des commandes pour démarrer et arrêter une animation

1. Dans le menu **affichage** , pointez sur **autres fenêtres** , puis cliquez sur **affichage des ressources**.

1. Dans **affichage des ressources**, accédez au dossier **menu** et ouvrez-le. Double-cliquez sur la ressource **IDR_MFCAnimationWalkthroughTYPE** pour l’ouvrir en vue de sa modification.

1. Dans la barre de menus, dans la zone **Tapez ici** , tapez *un&nimation* pour créer un menu d’animation.

1. Sous **animation**, dans la zone **Tapez ici** , tapez *Start &Forward* pour créer une commande Start Forward.

1. Sous **Start Forward**, dans la zone **Tapez ici** , tapez *Start &Backward*.

1. Sous **Démarrer en arrière**, dans la zone **Tapez ici** , tapez *S&Top* pour créer une commande Stop.

1. Enregistrez MFCAnimationWalkthrough. RC et fermez-le.

1. Dans **Explorateur de solutions**, double-cliquez sur MainFrm. cpp pour l’ouvrir en vue de le modifier. Dans la `CMainFrame::OnCreate` méthode, recherchez la section qui a plusieurs appels à `lstBasicCommands.AddTail` . Juste après cette section, ajoutez le code suivant.

    ```cpp
    lstBasicCommands.AddTail(ID_ANIMATION_STARTFORWARD);
    lstBasicCommands.AddTail(ID_ANIMATION_STARTBACKWARD);
    lstBasicCommands.AddTail(ID_ANIMATION_STOP);
    ```

1. Enregistrez le fichier et fermez-le.

### <a name="to-create-handlers-for-the-start-and-stop-commands"></a>Pour créer des gestionnaires pour les commandes de démarrage et d’arrêt

1. Dans le menu **projet** , cliquez sur **Assistant classe**.

1. Dans l' **Assistant classe MFC**, sous **nom** de la classe, sélectionnez **CMFCAnimationWalkthroughView**.

1. Sous l’onglet **commandes** , dans la zone **ID d’objet** , sélectionnez **ID_ANIMATION_STARTFORWARD**, puis dans la zone **messages** , sélectionnez **commande**. Cliquez sur **Ajouter un gestionnaire**.

1. Dans la boîte de dialogue **Ajouter une fonction membre** , cliquez sur **OK**.

1. Dans la zone **ID d’objet** , sélectionnez **ID_ANIMATION_STARTBACKWARD**, puis dans la zone **messages** , sélectionnez **commande**. Cliquez sur **Ajouter un gestionnaire**.

1. Dans la boîte de dialogue **Ajouter une fonction membre** , cliquez sur **OK**.

1. Dans la zone **ID d’objet** , sélectionnez **ID_ANIMATION_STOP**, puis dans la zone **messages** , sélectionnez **commande**. Cliquez sur **Ajouter un gestionnaire** , puis sur **OK**.

1. Dans la boîte de dialogue **Ajouter une fonction membre** , cliquez sur **OK**.

1. Dans l' **Assistant classe MFC**, cliquez sur **OK**.

1. Enregistrez MFCAnimationWalkthroughView. cpp, qui est ouvert dans l’éditeur, mais ne le fermez pas.

### <a name="to-add-an-animated-object-to-the-project"></a>Pour ajouter un objet animé au projet

1. Dans **Explorateur de solutions**, double-cliquez sur MFCAnimationWalkthroughView. h pour l’ouvrir en vue de le modifier. Juste avant la définition de la `CMFCAnimationWalkthroughView` classe, ajoutez le code suivant pour créer un contrôleur d’animation personnalisé qui gérera les conflits de planification avec l’objet d’animation.

    ```cpp
    class CCustomAnimationController : public CAnimationController
    {
    public:
        CCustomAnimationController()
        {
        }

        virtual BOOL OnHasPriorityTrim(CAnimationGroup* pGroupScheduled,
            CAnimationGroup* pGroupNew,
            UI_ANIMATION_PRIORITY_EFFECT priorityEffect)
        {
            return TRUE;
        }
    };
    ```

1. À la fin de la `CMFCAnimationWalkthroughView` classe, ajoutez le code suivant.

    ```cpp
    CCustomAnimationController m_animationController;
    CAnimationColor m_animationColor;
    CAnimationRect m_animationRect;
    ```

1. Après la `DECLARE_MESSAGE_MAP()` ligne, ajoutez le code suivant.

    ```cpp
    void Animate(BOOL bDirection);
    ```

1. Enregistrez le fichier et fermez-le.

1. Dans MFCAnimationWalkthroughView. cpp, en haut du fichier, après les `#include` instructions, mais avant toute méthode de classe, ajoutez le code suivant.

    ```cpp
    static int nAnimationGroup = 0;
    static int nInfoAreaHeight = 40;
    ```

1. À la fin du constructeur de `CMFCAnimationWalkthroughView` , ajoutez le code suivant.

    ```cpp
    m_animationController.EnableAnimationTimerEventHandler();
    m_animationController.EnablePriorityComparisonHandler(UI_ANIMATION_PHT_TRIM);
    m_animationColor = RGB(255, 255, 255);
    m_animationRect = CRect(0, 0, 0, 0);
    m_animationColor.SetID(-1, nAnimationGroup);
    m_animationRect.SetID(-1, nAnimationGroup);
    m_animationController.AddAnimationObject(&m_animationColor);
    m_animationController.AddAnimationObject(&m_animationRect);
    ```

1. Recherchez la `CAnimationWalthroughView::PreCreateWindow` méthode, puis remplacez-la par le code suivant.

    ```cpp
    BOOL CMFCAnimationWalkthroughView::PreCreateWindow(CREATESTRUCT& cs)
    {
        // TODO: Modify the Window class or styles here by modifying
        //       the CREATESTRUCT cs
        m_animationController.SetRelatedWnd(this);

        return CView::PreCreateWindow(cs);
    }
    ```

1. Recherchez la `CAnimationWalkthroughView::OnDraw` méthode, puis remplacez-la par le code suivant.

    ```cpp
    void CMFCAnimationWalkthroughView::OnDraw(CDC* pDC)
    {
        CMFCAnimationWalkthroughDoc* pDoc = GetDocument();
        ASSERT_VALID(pDoc);
        if (!pDoc)
            return;

        // TODO: add draw code for native data here
        CMemDC dcMem(*pDC, this);
        CDC& dc = dcMem.GetDC();
        CRect rect;
        GetClientRect(rect);

        dc.FillSolidRect(rect, GetSysColor(COLOR_WINDOW));

        CString strRGB;
        strRGB.Format(_T("Fill Color is: %d; %d; %d"),
            GetRValue(m_animationColor),
            GetGValue(m_animationColor),
            GetBValue(m_animationColor));

        dc.DrawText(strRGB, rect, DT_CENTER);
        rect.top += nInfoAreaHeight;

        CBrush br;
        br.CreateSolidBrush(m_animationColor);
        CBrush* pBrushOld = dc.SelectObject(&br);

        dc.Rectangle((CRect)m_animationRect);

        dc.SelectObject(pBrushOld);
    }
    ```

1. À la fin du fichier, ajoutez le code suivant.

    ```cpp
    void CMFCAnimationWalkthroughView::Animate(BOOL bDirection)
    {
        static UI_ANIMATION_SECONDS duration = 3;
        static DOUBLE dblSpeed = 35.;
        static BYTE nStartColor = 50;
        static BYTE nEndColor = 255;

        BYTE nRedColorFinal = bDirection ? nStartColor : nEndColor;
        BYTE nGreenColorFinal = bDirection ? nStartColor : nEndColor;
        BYTE nBlueColorFinal = bDirection ? nStartColor : nEndColor;

        CLinearTransition* pRedTransition =
            new CLinearTransition(duration, (DOUBLE)nRedColorFinal);

        CSmoothStopTransition* pGreenTransition =
            new CSmoothStopTransition(duration, (DOUBLE)nGreenColorFinal);

        CLinearTransitionFromSpeed* pBlueTransition =
            new CLinearTransitionFromSpeed(dblSpeed, (DOUBLE)nBlueColorFinal);

        m_animationColor.AddTransition(pRedTransition,
            pGreenTransition,
            pBlueTransition);

        CRect rectClient;
        GetClientRect(rectClient);

        rectClient.top += nInfoAreaHeight;

        int nLeftFinal = bDirection ? rectClient.left : rectClient.CenterPoint().x;
        int nTopFinal = bDirection ? rectClient.top : rectClient.CenterPoint().y;
        int nRightFinal = bDirection ? rectClient.right : rectClient.CenterPoint().x;
        int nBottomFinal = bDirection ? rectClient.bottom : rectClient.CenterPoint().y;

        CLinearTransition* pLeftTransition =
            new CLinearTransition(duration, nLeftFinal);

        CLinearTransition* pTopTransition =
            new CLinearTransition(duration, nTopFinal);

        CLinearTransition* pRightTransition =
            new CLinearTransition(duration, nRightFinal);

        CLinearTransition* pBottomTransition =
            new CLinearTransition(duration, nBottomFinal);

        m_animationRect.AddTransition(pLeftTransition,
            pTopTransition,
            pRightTransition,
            pBottomTransition);

        CBaseKeyFrame* pKeyframeStart =
            CAnimationController::GetKeyframeStoryboardStart();
        CKeyFrame* pKeyFrameEnd =
            m_animationController.CreateKeyframe(nAnimationGroup,
                pBlueTransition);

        pLeftTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pTopTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pRightTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pBottomTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);

        m_animationController.AnimateGroup(nAnimationGroup);
    }
    ```

1. Dans le menu **projet** , cliquez sur **Assistant classe**.

1. Dans l' **Assistant classe MFC**, sous **nom** de la classe, sélectionnez **CMFCAnimationWalkthroughView**.

1. Sous l’onglet **messages** , dans la zone **messages** , sélectionnez **WM_ERASEBKGND**, cliquez sur **Ajouter un gestionnaire**, puis cliquez sur **OK**.

1. Dans MFCAnimationWalkthroughView. cpp, remplacez l’implémentation de `OnEraseBkgnd` par le code suivant pour réduire le scintillement dans l’objet animé lorsqu’il est redessiné.

    ```cpp
    BOOL CMFCAnimationWalkthroughView::OnEraseBkgnd(CDC* /*pDC*/)
    {
        return TRUE;
    }
    ```

1. Remplacez les implémentations de `CMFCAnimationWalkthroughView::OnAnimationStartforward` , `CMFCAnimationWalkthroughView::OnAnimationStartbackward` et `CMFCAnimationWalkthroughView::OnAnimationStop` par le code suivant.

    ```cpp
    void CMFCAnimationWalkthroughView::OnAnimationStartforward()
    {
        Animate(TRUE);
    }

    void CMFCAnimationWalkthroughView::OnAnimationStartbackward()
    {
        Animate(FALSE);
    }

    void CMFCAnimationWalkthroughView::OnAnimationStop()
    {
        IUIAnimationManager* pManager = m_animationController.GetUIAnimationManager();
        if (pManager != NULL)
        {
            pManager->AbandonAllStoryboards();

        }
    }
    ```

1. Enregistrez le fichier et fermez-le.

### <a name="to-center-the-animated-object-in-the-window"></a>Pour centrer l’objet animé dans la fenêtre

1. Dans **Explorateur de solutions**, double-cliquez sur MFCAnimationWalkthroughView. h pour l’ouvrir en vue de le modifier. À la fin de la `CMFCAnimationWalkthroughView` classe, juste après la définition de `m_animationRect` , ajoutez le code suivant.

    ```cpp
    BOOL m_bCurrentDirection;
    ```

1. Enregistrez le fichier et fermez-le.

1. Dans le menu **projet** , cliquez sur **Assistant classe**.

1. Dans l' **Assistant classe MFC**, sous **nom** de la classe, sélectionnez **CMFCAnimationWalkthroughView**.

1. Sous l’onglet **messages** , dans la zone **messages** , sélectionnez **WM_SIZE**, cliquez sur **Ajouter un gestionnaire**, puis cliquez sur **OK**.

1. Dans MFCAnimationWalkthroughView. cpp, remplacez le code de `CMFCAnimationWalkthroughView::OnSize` par le code suivant.

    ```cpp
    void CMFCAnimationWalkthroughView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);
        CRect rect;
        GetClientRect(rect);

        rect.top += nInfoAreaHeight;

        CRect rectAnim = m_animationRect;
        m_animationRect = CRect(CPoint(rect.CenterPoint().x - rectAnim.Width() / 2,
        rect.CenterPoint().y - rectAnim.Height() / 2),
        rectAnim.Size());

        if (m_animationController.IsAnimationInProgress())
        {
            Animate(m_bCurrentDirection);
        }
    }
    ```

1. Au début du constructeur de `CMFCAnimationWalkthroughView` , ajoutez le code suivant.

    ```cpp
    m_bCurrentDirection = TRUE;
    ```

1. Au début de la `CMFCAnimationWalkthroughView::Animate` méthode, ajoutez le code suivant.

    ```cpp
    m_bCurrentDirection = bDirection;
    ```

1. Enregistrez le fichier et fermez-le.

### <a name="to-verify-the-results"></a>Pour vérifier les résultats

1. Générez et exécutez l’application. Dans le menu **animation** , cliquez sur **Démarrer vers l’avant**. Un rectangle doit apparaître, puis remplir la zone centrale. Lorsque vous cliquez sur **Démarrer en arrière**, l’animation doit être inversée et, lorsque vous cliquez sur **arrêter**, elle doit s’arrêter. La couleur de remplissage du rectangle doit changer à mesure que l’animation progresse, et la couleur actuelle doit s’afficher en haut de la fenêtre d’animation.

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas](../mfc/walkthroughs-mfc.md)
