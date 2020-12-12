---
description: 'En savoir plus sur : contrôles ActiveX MFC : peinture d’un contrôle ActiveX'
title: "Contrôles ActiveX MFC : peinture d'un contrôle ActiveX"
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
ms.openlocfilehash: d9e6fb23deb701e32f1af6ff4bf4d79c7d9df085
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305271"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>Contrôles ActiveX MFC : peinture d'un contrôle ActiveX

Cet article décrit le processus de peinture du contrôle ActiveX et le mode de modification du code de peinture pour optimiser le processus. (Consultez [optimisation du dessin de contrôle](optimizing-control-drawing.md) pour connaître les techniques permettant d’optimiser le dessin en n’ayant pas de contrôles restaurer individuellement les objets GDI sélectionnés précédemment. Une fois que tous les contrôles sont dessinés, le conteneur peut automatiquement restaurer les objets d'origine).

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Les exemples dans cet article proviennent d'un contrôle créé par l'Assistant Contrôle ActiveX de MFC avec des paramètres par défaut. Pour plus d’informations sur la création d’une application de contrôle squelette à l’aide de l’Assistant contrôle ActiveX MFC, consultez l’article [Assistant contrôle ActiveX MFC](reference/mfc-activex-control-wizard.md).

Les rubriques suivantes sont traitées :

- [Le processus global pour peindre un contrôle et le code créé par l'Assistant Contrôle ActiveX pour prendre en charge la peinture](#_core_the_painting_process_of_an_activex_control)

- [Comment optimiser le processus de peinture ?](#_core_optimizing_your_paint_code)

- [Comment peindre votre contrôle à l'aide de métafichiers ?](#_core_painting_your_control_using_metafiles)

## <a name="the-painting-process-of-an-activex-control"></a><a name="_core_the_painting_process_of_an_activex_control"></a> Processus de peinture d’un contrôle ActiveX

Lorsque les contrôles ActiveX sont initialement affichés ou redessinés, ils suivent un processus de peinture semblable à d'autres applications développées à l'aide de MFC, avec une distinction importante : les contrôles ActiveX peuvent être dans un état actif ou inactif.

Un contrôle actif est représenté dans un conteneur de contrôles ActiveX par une fenêtre enfant. Comme les autres fenêtres, il est responsable de la peinture lorsqu’un message de WM_PAINT est reçu. La classe de base du contrôle, [COleControl](reference/colecontrol-class.md), gère ce message dans sa `OnPaint` fonction. Cette implémentation par défaut appelle la fonction `OnDraw` de votre contrôle.

Un contrôle inactif est peint différemment. Lorsque le contrôle est inactif, sa fenêtre est invisible ou inexistante, donc il ne peut pas recevoir de message de peinture. En revanche, le conteneur de contrôle appelle directement la fonction `OnDraw` du contrôle. Ceci diffère du processus de peinture actif d'un contrôle en ce que la fonction membre `OnPaint` n'est jamais appelée.

Comme décrit dans les paragraphes précédents, la manière dont un contrôle ActiveX est mis à jour dépend de l'état du contrôle. Toutefois, étant donné que le framework appelle la fonction membre `OnDraw` dans les deux cas, vous ajoutez la majorité de votre code de peinture dans cette fonction membre.

La fonction membre `OnDraw` gère la peinture du contrôle. Lorsqu'un contrôle est inactif, le conteneur de contrôle appelle `OnDraw`, en passant le contexte de périphérique du conteneur de contrôle et les coordonnées de la zone rectangulaire occupée par le contrôle.

Le rectangle passé par le framework à la fonction membre `OnDraw` contient la zone occupée par le contrôle. Si le contrôle est actif, l'angle supérieur gauche est (0, 0) et le contexte de périphérique est passé pour la fenêtre enfant qui contient le contrôle. Si le contrôle est inactif, la coordonnée supérieure gauche n'est pas nécessairement égale à 0, 0 et le contexte de périphérique est passé pour le conteneur de contrôle qui contient le contrôle.

> [!NOTE]
> Il est important que les modifications apportées à `OnDraw` ne dépendent pas du point supérieur gauche du rectangle qui est égal à (0,0) et que vous dessiniez uniquement à l’intérieur du rectangle passé à `OnDraw` . Des résultats inattendus peuvent se produire si vous dessinez au delà de la zone du rectangle.

L'implémentation par défaut fournie par l'Assistant Contrôle ActiveX MFC dans le fichier d'implémentation du contrôle (.CPP), comme indiqué ci-dessous, peint le rectangle avec un pinceau blanc et remplit l'ellipse avec la couleur d'arrière-plan actuelle.

[!code-cpp[NVC_MFC_AxUI#1](codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
> Lors de la peinture d’un contrôle, vous ne devez pas faire d’hypothèses concernant l’état du contexte de périphérique qui est passé comme paramètre de *contrôleur de domaine principal* à la `OnDraw` fonction. Occasionnellement le contexte de périphérique est fourni par l'application conteneur et n'est pas nécessairement initialisé à l'état par défaut. En particulier, sélectionnez explicitement les stylets, pinceaux, couleurs, polices et autres ressources dont votre code de dessin dépend.

## <a name="optimizing-your-paint-code"></a><a name="_core_optimizing_your_paint_code"></a> Optimisation de votre code de peinture

Lorsque le contrôle se peint avec succès, l'étape suivante consiste à optimiser la fonction `OnDraw`.

L'implémentation par défaut du contrôle de peinture ActiveX peint la zone de contrôle entière. Ceci suffit pour les contrôles simples, mais dans de nombreux cas, redessiner le contrôle serait plus rapide si seulement la partie qui nécessitait une mise à jour était repeinte, au lieu du contrôle entier.

La `OnDraw` fonction fournit une méthode simple d’optimisation en passant *rcInvalid*, la zone rectangulaire du contrôle qui doit être redessinée. Utilisez cette zone, généralement inférieure à la zone de contrôle entière, pour accélérer le processus de peinture.

## <a name="painting-your-control-using-metafiles"></a><a name="_core_painting_your_control_using_metafiles"></a> Peinture de votre contrôle à l’aide de safiles

Dans la plupart des cas, le paramètre *PDC* vers la `OnDraw` fonction pointe vers un contexte de périphérique (DC) d’écran. Toutefois, lors de l'impression d'images du contrôle ou lors d'une session d'aperçu avant impression, le contrôleur de domaine reçu pour affichage est un type spécial appelé "contexte de périphérique de métafichier". Contrairement à un écran contrôleur de domaine, qui gère à la fois les demandes qui lui sont envoyées, les métafichiers DC stocke les demandes qui doivent être traitées ultérieurement. Certaines applications conteneur peuvent également choisir d'afficher l'image de contrôle lorsqu'il se trouve en mode création à l'aide d'un métafichier DC.

Les demandes de dessin de métafichiers peuvent être effectuées par le conteneur à l’aide de deux fonctions d’interface : `IViewObject::Draw` (cette fonction peut également être appelée pour un dessin non-métafichier) et `IDataObject::GetData` . Quand un contexte de périphérique de métafichier est passé comme l’un des paramètres, l’infrastructure MFC effectue un appel à [COleControl :: OnDrawMetafile](reference/colecontrol-class.md#ondrawmetafile). Puisqu'il s'agit d'une fonction membre virtuelle, remplacez cette fonction dans la classe de contrôle pour effectuer tout traitement spécial. Le comportement par défaut appelle `COleControl::OnDraw`.

Pour garantir que le contrôle peut être dessiné à la fois sur l'écran et sur des contextes de périphérique de métafichier, vous ne devez utiliser que les fonctions membres qui sont prises en charge à la fois dans un écran et dans un contexte de périphérique de métafichier. Sachez que le système de coordonnées peut ne pas être exprimé en pixels.

Etant donné que l'implémentation par défaut de `OnDrawMetafile` appelle la fonction `OnDraw` du contrôle, n'utilisez que les fonctions membres qui conviennent à la fois pour un métafichier et pour un contexte de périphérique, sauf si vous remplacez `OnDrawMetafile`. Ce qui suit répertorie le sous-ensemble de fonctions membres `CDC` qui peuvent être utilisées à la fois dans un métafichier et dans écran de contexte de périphérique. Pour plus d’informations sur ces fonctions, consultez la classe [CDC](reference/cdc-class.md) dans la *référence MFC*.

|Arc|BibBlt|Chord|
|---------|------------|-----------|
|`Ellipse`|`Escape`|`ExcludeClipRect`|
|`ExtTextOut`|`FloodFill`|`IntersectClipRect`|
|`LineTo`|`MoveTo`|`OffsetClipRgn`|
|`OffsetViewportOrg`|`OffsetWindowOrg`|`PatBlt`|
|`Pie`|`Polygon`|`Polyline`|
|`PolyPolygon`|`RealizePalette`|`RestoreDC`|
|`RoundRect`|`SaveDC`|`ScaleViewportExt`|
|`ScaleWindowExt`|`SelectClipRgn`|`SelectObject`|
|`SelectPalette`|`SetBkColor`|`SetBkMode`|
|`SetMapMode`|`SetMapperFlags`|`SetPixel`|
|`SetPolyFillMode`|`SetROP2`|`SetStretchBltMode`|
|`SetTextColor`|`SetTextJustification`|`SetViewportExt`|
|`SetViewportOrg`|`SetWindowExt`|`SetWindowORg`|
|`StretchBlt`|`TextOut`||

Outre les fonctions membres `CDC`, il existe plusieurs autres fonctions compatibles dans un contexte de périphérique de métafichier. Citons notamment [cpalette :: AnimatePalette](reference/cpalette-class.md#animatepalette), [CFont :: CreateFontIndirect](reference/cfont-class.md#createfontindirect)et trois fonctions membres de `CBrush` : [CreateBrushIndirect](reference/cbrush-class.md#createbrushindirect), [CreateDIBPatternBrush](reference/cbrush-class.md#createdibpatternbrush)et [CreatePatternBrush](reference/cbrush-class.md#createpatternbrush).

Les fonctions qui ne sont pas enregistrées dans un métafichier sont les suivantes : [DrawFocusRect](reference/cdc-class.md#drawfocusrect), [DrawIcon](reference/cdc-class.md#drawicon), [DrawText](reference/cdc-class.md#drawtext), [ExcludeUpdateRgn](reference/cdc-class.md#excludeupdatergn), [fillRect](reference/cdc-class.md#fillrect), [FrameRect](reference/cdc-class.md#framerect), [GrayString](reference/cdc-class.md#graystring), [InvertRect](reference/cdc-class.md#invertrect), [ScrollDC](reference/cdc-class.md#scrolldc)et [TabbedTextOut](reference/cdc-class.md#tabbedtextout). Étant donné qu'un contexte de périphérique de métafichier n'est pas réellement associé à un périphérique, vous ne pouvez pas utiliser SetDIBits, GetDIBits et CreateDIBitmap avec un contexte de périphérique de métafichier. Vous pouvez utiliser SetDIBitsToDevice et StretchDIBits avec un contexte de périphérique de métafichier comme destination. [CreateCompatibleDC](reference/cdc-class.md#createcompatibledc), [CreateCompatibleBitmap](reference/cbitmap-class.md#createcompatiblebitmap)et [CreateDiscardableBitmap](reference/cbitmap-class.md#creatediscardablebitmap) ne sont pas significatifs avec un DC de métafichier.

Un autre point à prendre en considération lors de l'utilisation d'un contexte de périphérique de métafichier est que le système de coordonnées peut ne pas être exprimé en pixels. Pour cette raison, tout votre code de dessin doit être ajusté pour tenir dans le rectangle passé à `OnDraw` dans le paramètre *rcBounds* . Cela empêche la peinture accidentelle en dehors du contrôle, car *rcBounds* représente la taille de la fenêtre du contrôle.

Une fois que vous avez implémenté le rendu de métafichier pour le contrôle, utilisez le contrôleur de test pour tester le métafichier. Pour plus d’informations sur la façon d’accéder au conteneur de test, consultez la page [Test des propriétés et des événements avec le conteneur de test](testing-properties-and-events-with-test-container.md) .

#### <a name="to-test-the-controls-metafile-using-test-container"></a>Pour tester le métafichier du contrôle à l'aide du Contrôleur de test

1. Dans le menu **Edition** du conteneur de test, cliquez sur **Insérer un nouveau contrôle**.

1. Dans la zone **Insérer un nouveau contrôle** , sélectionnez le contrôle, puis cliquez sur **OK**.

   Le contrôle s'affiche dans le conteneur de test.

1. Dans le menu **contrôle** , cliquez sur **dessiner un métafichier**.

   Une fenêtre distincte apparaît dans laquelle le métafichier s'affiche. Vous pouvez modifier la taille de cette fenêtre pour voir comment la mise à l'échelle affecte un métafichier du contrôle. Vous pouvez fermer cette fenêtre à tout moment.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)
