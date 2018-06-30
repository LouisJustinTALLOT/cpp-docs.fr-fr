---
title: 'Procédure pas à pas : Ajout d’une Animation à un projet MFC | Documents Microsoft'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- animation [MFC]
- MFC, animation
ms.assetid: 004f832c-9fd5-4f88-9ca9-ae65dececdc2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f647c7621c01a18cedc8d08d1a3f344b19139a90
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121797"
---
# <a name="walkthrough-adding-animation-to-an-mfc-project"></a>Procédure pas à pas : ajout d'une animation à un projet MFC

Cette procédure pas à pas explique comment ajouter un objet animé base à un Visual C++, le projet de bibliothèque de classes Microsoft Foundation (MFC).

La procédure pas à pas montre comment accomplir ces tâches :

- Créer une application MFC.

- Ajouter un menu, puis ajouter des commandes pour démarrer et arrêter une animation.

- Créer des gestionnaires pour les commandes de démarrage et d’arrêt.

- Ajouter un objet animé au projet.

- Centre de l’objet animé dans la fenêtre.

- Vérifier les résultats.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prérequis

Pour effectuer cette procédure pas à pas, vous devez disposer de Visual Studio.

### <a name="to-create-an-mfc-application"></a>Pour créer une application MFC

1. Dans le menu **Fichier** , pointez sur **Nouveau** , puis cliquez sur **Projet**.

2. Dans le **nouveau projet** boîte de dialogue, dans le volet gauche sous **modèles installés**, développez **Visual C++** , puis sélectionnez **MFC**. Dans le volet central, sélectionnez **Application MFC**. Dans le **nom** , tapez *MFCAnimationWalkthrough*. Cliquez sur **OK**.

3. Dans le **Assistant Application MFC** boîte de dialogue zone, vérifiez que **Type d’Application** est **plusieurs Documents**, **Style de projet** est  **Visual Studio**et le **prise en charge de l’Architecture Document/vue** option est sélectionnée. Cliquez sur **Terminer**.

### <a name="to-add-a-menu-and-then-add-commands-to-start-and-stop-an-animation"></a>Pour ajouter un menu, puis ajouter des commandes pour démarrer et arrêter une animation

1. Sur le **vue** menu, pointez sur **autres fenêtres** puis cliquez sur **affichage des ressources**.

2. Dans **affichage des ressources**, accédez à la **Menu** dossier et ouvrez-le. Double-cliquez sur le `IDR_MFCAnimationWalTYPE` ressource pour l’ouvrir pour modification.

3. Dans la barre de menus, dans le **Type ici** , tapez *A & nimation* pour créer un Animation menu.

4. Sous **Animation**, dans le **Type ici** , tapez *Démarrer a & vant* pour créer une commande Démarrer en avant.

5. Sous **démarrer avant**, dans le **Type ici** , tapez *Démarrer & en arrière*.

6. Sous **démarrer descendante**, dans le **Type ici** , tapez *& rrêter* pour créer une commande d’arrêt.

7. Enregistrez le fichier MFCAnimationWalkthrough.rc et fermez-le.

8. Dans **l’Explorateur de solutions**, double-cliquez sur MainFrm.cpp pour l’ouvrir pour modification. Dans le `CMainFrame::OnCreate` (méthode), recherchez la section comportant plusieurs appels à `lstBasicCommands.AddTail`. Juste après cette section, ajoutez le code suivant.  

    ```cpp
    lstBasicCommands.AddTail(ID_ANIMATION_STARTFORWARD);
    lstBasicCommands.AddTail(ID_ANIMATION_STARTBACKWARD);
    lstBasicCommands.AddTail(ID_ANIMATION_STOP);
    ```

9. Enregistrez le fichier et fermez-le.

### <a name="to-create-handlers-for-the-start-and-stop-commands"></a>Pour créer des gestionnaires pour le démarrer et arrêter des commandes

1. Sur le **projet** menu, cliquez sur **Assistant classe**.

2. Dans le **Assistant classe MFC**, sous **nom de la classe**, sélectionnez `CMFCAnimationWalkthroughView`.

3. Sur le **commandes** sous l’onglet le **ID d’objet** boîte, sélectionnez `ID_ANIMATION_STARTFORWARD`, puis, dans le **Messages** boîte, sélectionnez `COMMAND`. Cliquez sur **Ajouter Gestionnaire**.

4. Dans le **ajouter une fonction membre** boîte de dialogue, cliquez sur **OK**.

5. Dans le **ID d’objet** boîte, sélectionnez `ID_ANIMATION_STARTBACKWARD`, puis, dans le **Messages** boîte, sélectionnez `COMMAND`. Cliquez sur **Ajouter Gestionnaire**.

6. Dans le **ajouter une fonction membre** boîte de dialogue, cliquez sur **OK**.

7. Dans le **ID d’objet** boîte, sélectionnez `ID_ANIMATION_STOP`, puis, dans le **Messages** boîte, sélectionnez `COMMAND`. Cliquez sur **ajouter un gestionnaire** puis cliquez sur **OK**.

8. Dans le **ajouter une fonction membre** boîte de dialogue, cliquez sur **OK**.

9. Dans le **Assistant classe MFC**, cliquez sur **OK**.

10. Enregistrez MFCAnimationWalkthroughView.cpp, qui est ouvert dans l’éditeur, mais ne le fermez pas.

### <a name="to-add-an-animated-object-to-the-project"></a>Pour ajouter un objet animé au projet

1. Dans l’Explorateur de solutions, double-cliquez sur MFCAnimationWalkthroughView.h pour l’ouvrir pour modification. Juste avant la définition de la `CMFCAnimationWalkthroughView` de classe, ajoutez le code suivant pour créer un contrôleur de l’animation personnalisée qui va gérer les conflits de planification avec l’objet d’animation.

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

2. À la fin de la `CMFCAnimationWalkthroughView` de classe, ajoutez le code suivant.

    ```cpp
    CCustomAnimationController m_animationController;
    CAnimationColor m_animationColor;
    CAnimationRect m_animationRect;
    ```

3. Après le `DECLARE_MESSAGE_MAP()` ligne, ajoutez le code suivant.

    ```cpp
    void Animate(BOOL bDirection);
    ```

4. Enregistrez le fichier et fermez-le.

5. Dans MFCAnimationWalkthroughView.cpp, en haut du fichier après le `#include` instructions mais avant les méthodes de classe, ajoutent le code suivant.

    ```cpp
    static int nAnimationGroup = 0;
    static int nInfoAreaHeight = 40;
    ```

6. À la fin du constructeur pour `CMFCAnimationWalkthroughView`, ajoutez le code suivant.

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

7. Recherchez le `CAnimationWalthroughView::PreCreateWindow` (méthode), puis la remplacer par le code suivant.

    ```cpp
    BOOL CMFCAnimationWalkthroughView::PreCreateWindow(CREATESTRUCT& cs)
    {
        // TODO: Modify the Window class or styles here by modifying
        //       the CREATESTRUCT cs
        m_animationController.SetRelatedWnd(this);

        return CView::PreCreateWindow(cs);
    }
    ```

8. Recherchez le `CAnimationWalkthroughView::OnDraw` (méthode), puis la remplacer par le code suivant.

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

9. À la fin du fichier, ajoutez le code suivant.

    ```cpp
    void CMFCAnimationWalkthroughView::Animate(BOOL bDirection)
    {
        static UI_ANIMATION_SECONDS duration = 3;
        static DOUBLE dblSpeed = 35.;
        static BYTE nStartColor = 50;
        static BYTE nEndColor = 255;

        BYTE nRedColorFinal = bDirection  nStartColor : nEndColor;
        BYTE nGreenColorFinal = bDirection  nStartColor : nEndColor;
        BYTE nBlueColorFinal = bDirection  nStartColor : nEndColor;

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

10. Sur le **projet** menu, cliquez sur **Assistant classe**.

11. Dans le **Assistant classe MFC**, sous **nom de la classe**, sélectionnez `CMFCAnimationWalkthroughView`.

12. Sur le **Messages** sous l’onglet du **Messages** boîte, sélectionnez `WM_ERASEBKGND`, cliquez sur **ajouter un gestionnaire**, puis cliquez sur **OK**.

13. Dans MFCAnimationWalkthroughView.cpp, remplacez l’implémentation de `OnEraseBkgnd` par le code suivant pour réduire le scintillement dans l’objet animé lorsqu’il est redessiné.

    ```cpp
    BOOL CMFCAnimationWalkthroughView::OnEraseBkgnd(CDC* /*pDC*/)
    {
        return TRUE;
    }
    ```

14. Remplacez les implémentations de `CMFCAnimationWalkthroughView::OnAnimationStartforward`, `CMFCAnimationWalkthroughView::OnAnimationStartbackward`, et `CMFCAnimationWalkthroughView::OnAnimationStop` par le code suivant.

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

15. Enregistrez le fichier et fermez-le.

### <a name="to-center-the-animated-object-in-the-window"></a>Pour centrer l’objet animé dans la fenêtre

1. Dans **l’Explorateur de solutions**, double-cliquez sur MFCAnimationWalkthroughView.h pour l’ouvrir pour modification. À la fin de la `CMFCAnimationWalkthroughView` (classe), juste après la définition de `m_animationRect`, ajoutez le code suivant.

    ```cpp
    BOOL m_bCurrentDirection;
    ```

2. Enregistrez le fichier et fermez-le.

3. Sur le **projet** menu, cliquez sur **Assistant classe**.

4. Dans le **Assistant classe MFC**, sous **nom de la classe**, sélectionnez `CMFCAnimationWalkthroughView`.

5. Sur le **Messages** sous l’onglet du **Messages** boîte, sélectionnez `WM_SIZE`, cliquez sur **ajouter un gestionnaire**, puis cliquez sur **OK**.

6. Dans MFCAnimationWalkthroughView.cpp, remplacez le code de `CMFCAnimationWalkthroughView::OnSize` avec le code suivant.

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

7. Au début du constructeur pour `CMFCAnimationWalkthroughView`, ajoutez le code suivant.

    ```cpp
    m_bCurrentDirection = TRUE;
    ```

8. Au début de la `CMFCAnimationWalkthroughView::Animate` méthode, ajoutez le code suivant.

    ```cpp
    m_bCurrentDirection = bDirection;
    ```

9. Enregistrez le fichier et fermez-le.

### <a name="to-verify-the-results"></a>Pour vérifier les résultats

1. Générez et exécutez l’application. Sur le **Animation** menu, cliquez sur **avant de démarrer**. Un rectangle doit apparaître et puis remplir la zone centrale. Lorsque vous cliquez sur **démarrer descendante**, l’animation doit inverser, et lorsque vous cliquez sur **arrêter**, il doit s’arrêter. La couleur de remplissage du rectangle doit modifier en tant que l’animation progresse et la couleur actuelle doit être affichée en haut de la fenêtre de l’animation.

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas](../mfc/walkthroughs-mfc.md)  
