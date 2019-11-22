---
title: "Procédure pas à pas : ajout d'un objet D2D à un projet MFC"
ms.date: 04/25/2019
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
ms.openlocfilehash: 5e1c75e32899ef9697025d662eeec4a6a2482f2b
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304303"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>Procédure pas à pas : ajout d'un objet D2D à un projet MFC

Cette procédure pas à pas explique comment ajouter un objet Direct2D (D2D) de base C++à un projet Visual, bibliothèque MFC (Microsoft Foundation Class) (MFC), puis générer le projet dans une application qui imprime « Hello, World ! » sur un arrière-plan dégradé.

La procédure pas à pas montre comment accomplir ces tâches :

- Créez une application MFC.

- Créez un pinceau de couleur unie et un pinceau de dégradé linéaire.

- Modifiez le pinceau de dégradé afin qu’il change de manière appropriée lorsque la fenêtre est redimensionnée.

- Implémentez un gestionnaire de dessin D2D.

- Vérifiez les résultats.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Configuration requise

Pour effectuer cette procédure pas à pas, vous devez avoir installé Visual Studio avec le **développement bureautique avec C++**  la charge de travail et le composant facultatif **Visual C++ MFC pour x86 et x64** .

## <a name="to-create-an-mfc-application"></a>Pour créer une application MFC

1. Utilisez l' **Assistant Application MFC** pour créer une application MFC. Consultez [procédure pas à pas : utilisation des nouveaux contrôles de l’interpréteur de commandes MFC](walkthrough-using-the-new-mfc-shell-controls.md) pour obtenir des instructions sur l’ouverture de l’Assistant pour votre version de Visual Studio.

1. Dans la zone **nom** , tapez *MFCD2DWalkthrough*. Cliquez sur **OK**.

1. Dans l' **Assistant Application MFC**, choisissez **Terminer** sans modifier les paramètres.

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>Pour créer un pinceau de couleur unie et un pinceau de dégradé linéaire

1. Dans **Explorateur de solutions**, dans le projet **MFCD2DWalkthrough** , dans le dossier **fichiers d’en-tête** , ouvrez MFCD2DWalkthroughView. h. Ajoutez ce code à la classe `CMFCD2DWalkthroughView` pour créer trois variables de données :

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   Enregistrez le fichier et fermez-le.

1. Dans le dossier **fichiers sources** , ouvrez MFCD2DWalkthroughView. cpp. Dans le constructeur de la classe `CMFCD2DWalkthroughView`, ajoutez le code suivant :

   ```cpp
   // Enable D2D support for this window:
   EnableD2DSupport();

   // Initialize D2D resources:
   m_pBlackBrush = new CD2DSolidColorBrush(
       GetRenderTarget(),
       D2D1::ColorF(D2D1::ColorF::Black));

   m_pTextFormat = new CD2DTextFormat(
       GetRenderTarget(),
       _T("Verdana"),
       50);

   m_pTextFormat->Get()->SetTextAlignment(
       DWRITE_TEXT_ALIGNMENT_CENTER);

   m_pTextFormat->Get()->SetParagraphAlignment(
       DWRITE_PARAGRAPH_ALIGNMENT_CENTER);

   D2D1_GRADIENT_STOP gradientStops[2];

   gradientStops[0].color =
       D2D1::ColorF(D2D1::ColorF::White);

   gradientStops[0].position = 0.f;
   gradientStops[1].color =
       D2D1::ColorF(D2D1::ColorF::Indigo);

   gradientStops[1].position = 1.f;

   m_pLinearGradientBrush = new CD2DLinearGradientBrush(
       GetRenderTarget(),
       gradientStops,
       ARRAYSIZE(gradientStops),
       D2D1::LinearGradientBrushProperties(
           D2D1::Point2F(0,0),
           D2D1::Point2F(0,0)));
   ```

   Enregistrez le fichier et fermez-le.

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>Pour modifier le pinceau de dégradé afin qu’il change de manière appropriée lorsque la fenêtre est redimensionnée

1. Dans le menu **projet** , choisissez **Assistant classe**.

1. Dans l' **Assistant classe MFC**, sous **nom**de la classe, sélectionnez `CMFCD2DWalkthroughView`.

1. Sous l’onglet **messages** , dans la zone **messages** , sélectionnez `WM_SIZE`, puis choisissez **Ajouter un gestionnaire**. Cette action ajoute le gestionnaire de messages `OnSize` à la classe `CMFCD2DWalkthroughView`.

1. Dans la zone **gestionnaires existants** , sélectionnez `OnSize`. Choisissez **modifier le code** pour afficher la méthode `CMFCD2DWalkthroughView::OnSize`. À la fin de la méthode, ajoutez le code suivant.

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   Enregistrez le fichier et fermez-le.

## <a name="to-implement-a-d2d-drawing-handler"></a>Pour implémenter un gestionnaire de dessin D2D

1. Dans le menu **projet** , choisissez **Assistant classe**.

1. Dans l' **Assistant classe MFC**, sous **nom**de la classe, sélectionnez `CMFCD2DWalkthroughView`.

1. Sous l’onglet **messages** , choisissez **Ajouter un message personnalisé**.

1. Dans la boîte de dialogue **Ajouter un message personnalisé** , dans la zone de **message Windows personnalisée** , tapez *AFX_WM_DRAW2D*. Dans la zone **nom du gestionnaire de messages** , tapez *OnDraw2D*. Sélectionnez l’option **message inscrit** , puis choisissez **OK**. Cette action ajoute un gestionnaire de messages pour le message AFX_WM_DRAW2D à la classe `CMFCD2DWalkthroughView`.

1. Dans la zone **gestionnaires existants** , sélectionnez `OnDraw2D`. Choisissez **modifier le code** pour afficher la méthode `CMFCD2DWalkthroughView::OnDraw2D`. Utilisez ce code pour la méthode `CMFCD2DWalkthroughView::OnDrawD2D` :

   ```cpp
   afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(
       WPARAM wParam,
       LPARAM lParam)
   {
       CHwndRenderTarget* pRenderTarget = (CHwndRenderTarget*)lParam;
       ASSERT_VALID(pRenderTarget);

       CRect rect;
       GetClientRect(rect);

       pRenderTarget->FillRectangle(rect, m_pLinearGradientBrush);

       pRenderTarget->DrawText(
           _T("Hello, World!"),
           rect,
           m_pBlackBrush,
           m_pTextFormat);

       return TRUE;
   }
   ```

   Enregistrez le fichier et fermez-le.

## <a name="to-verify-the-results"></a>Pour vérifier les résultats

Générez et exécutez l’application. Il doit comporter un rectangle de dégradé qui change lorsque vous redimensionnez la fenêtre. "Hello World!" doit être affiché au centre du rectangle.

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas](../mfc/walkthroughs-mfc.md)
