---
title: "Contrôles ActiveX MFC : peinture d'un contrôle ActiveX"
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
ms.openlocfilehash: fd98af90e86b6b98a856e633e50c5bf266cc466a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364586"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>Contrôles ActiveX MFC : peinture d'un contrôle ActiveX

Cet article décrit le processus de peinture du contrôle ActiveX et le mode de modification du code de peinture pour optimiser le processus. (Voir [Optimiser le dessin de contrôle](../mfc/optimizing-control-drawing.md) pour les techniques sur la façon d’optimiser le dessin en n’ayant pas de contrôles individuellement restaurer les objets GDI précédemment sélectionnés. Une fois que tous les contrôles sont dessinés, le conteneur peut automatiquement restaurer les objets d'origine).

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

Les exemples dans cet article proviennent d'un contrôle créé par l'Assistant Contrôle ActiveX de MFC avec des paramètres par défaut. Pour plus d’informations sur la création d’une application de contrôle squelette à l’aide du MFC ActiveX Control Wizard, voir l’article [MFC ActiveX Control Wizard](../mfc/reference/mfc-activex-control-wizard.md).

Les rubriques suivantes sont traitées :

- [Le processus global pour peindre un contrôle et le code créé par l'Assistant Contrôle ActiveX pour prendre en charge la peinture](#_core_the_painting_process_of_an_activex_control)

- [Comment optimiser le processus de peinture ?](#_core_optimizing_your_paint_code)

- [Comment peindre votre contrôle à l'aide de métafichiers ?](#_core_painting_your_control_using_metafiles)

## <a name="the-painting-process-of-an-activex-control"></a><a name="_core_the_painting_process_of_an_activex_control"></a>Le processus de peinture d’un contrôle ActiveX

Lorsque les contrôles ActiveX sont initialement affichés ou redessinés, ils suivent un processus de peinture semblable à d'autres applications développées à l'aide de MFC, avec une distinction importante : les contrôles ActiveX peuvent être dans un état actif ou inactif.

Un contrôle actif est représenté dans un conteneur de contrôles ActiveX par une fenêtre enfant. Comme d’autres fenêtres, il est responsable de la peinture elle-même quand un message WM_PAINT est reçu. La classe de base du contrôle, [COleControl](../mfc/reference/colecontrol-class.md) `OnPaint` , gère ce message dans sa fonction. Cette implémentation par défaut appelle la fonction `OnDraw` de votre contrôle.

Un contrôle inactif est peint différemment. Lorsque le contrôle est inactif, sa fenêtre est invisible ou inexistante, donc il ne peut pas recevoir de message de peinture. En revanche, le conteneur de contrôle appelle directement la fonction `OnDraw` du contrôle. Ceci diffère du processus de peinture actif d'un contrôle en ce que la fonction membre `OnPaint` n'est jamais appelée.

Comme décrit dans les paragraphes précédents, la manière dont un contrôle ActiveX est mis à jour dépend de l'état du contrôle. Toutefois, étant donné que le framework appelle la fonction membre `OnDraw` dans les deux cas, vous ajoutez la majorité de votre code de peinture dans cette fonction membre.

La fonction membre `OnDraw` gère la peinture du contrôle. Lorsqu'un contrôle est inactif, le conteneur de contrôle appelle `OnDraw`, en passant le contexte de périphérique du conteneur de contrôle et les coordonnées de la zone rectangulaire occupée par le contrôle.

Le rectangle passé par le framework à la fonction membre `OnDraw` contient la zone occupée par le contrôle. Si le contrôle est actif, l'angle supérieur gauche est (0, 0) et le contexte de périphérique est passé pour la fenêtre enfant qui contient le contrôle. Si le contrôle est inactif, la coordonnée supérieure gauche n'est pas nécessairement égale à 0, 0 et le contexte de périphérique est passé pour le conteneur de contrôle qui contient le contrôle.

> [!NOTE]
> Il est important que `OnDraw` vos modifications ne dépendent pas du point supérieur gauche du rectangle étant égal à (0, 0) et que vous dessinez seulement à l’intérieur du rectangle passé à `OnDraw`. Des résultats inattendus peuvent se produire si vous dessinez au delà de la zone du rectangle.

L'implémentation par défaut fournie par l'Assistant Contrôle ActiveX MFC dans le fichier d'implémentation du contrôle (.CPP), comme indiqué ci-dessous, peint le rectangle avec un pinceau blanc et remplit l'ellipse avec la couleur d'arrière-plan actuelle.

[!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
> Lors de la peinture d’un contrôle, vous ne devez pas faire des hypothèses sur l’état du contexte de l’appareil qui est passé comme le paramètre *pdc* à la `OnDraw` fonction. Occasionnellement le contexte de périphérique est fourni par l'application conteneur et n'est pas nécessairement initialisé à l'état par défaut. En particulier, sélectionnez explicitement les stylets, pinceaux, couleurs, polices et autres ressources dont votre code de dessin dépend.

## <a name="optimizing-your-paint-code"></a><a name="_core_optimizing_your_paint_code"></a>Optimiser votre code de peinture

Lorsque le contrôle se peint avec succès, l'étape suivante consiste à optimiser la fonction `OnDraw`.

L'implémentation par défaut du contrôle de peinture ActiveX peint la zone de contrôle entière. Ceci suffit pour les contrôles simples, mais dans de nombreux cas, redessiner le contrôle serait plus rapide si seulement la partie qui nécessitait une mise à jour était repeinte, au lieu du contrôle entier.

La `OnDraw` fonction fournit une méthode facile d’optimisation en passant *rcInvalid*, la zone rectangulaire du contrôle qui a besoin de redessiner. Utilisez cette zone, généralement inférieure à la zone de contrôle entière, pour accélérer le processus de peinture.

## <a name="painting-your-control-using-metafiles"></a><a name="_core_painting_your_control_using_metafiles"></a>Peinture de votre contrôle à l’aide de métafiles

Dans la plupart des cas, le paramètre *pdc* de la `OnDraw` fonction indique un contexte de périphérique d’écran (DC). Toutefois, lors de l'impression d'images du contrôle ou lors d'une session d'aperçu avant impression, le contrôleur de domaine reçu pour affichage est un type spécial appelé "contexte de périphérique de métafichier". Contrairement à un écran contrôleur de domaine, qui gère à la fois les demandes qui lui sont envoyées, les métafichiers DC stocke les demandes qui doivent être traitées ultérieurement. Certaines applications conteneur peuvent également choisir d'afficher l'image de contrôle lorsqu'il se trouve en mode création à l'aide d'un métafichier DC.

Les demandes de dessin métadiliens peuvent être `IViewObject::Draw` faites par le conteneur à travers deux fonctions `IDataObject::GetData`d’interface: (cette fonction peut également être appelée pour le dessin non-métaafile) et . Lorsqu’un DC métaafile est adopté comme l’un des paramètres, le cadre MFC fait un appel à [COleControl::OnDrawMetafile](../mfc/reference/colecontrol-class.md#ondrawmetafile). Puisqu'il s'agit d'une fonction membre virtuelle, remplacez cette fonction dans la classe de contrôle pour effectuer tout traitement spécial. Le comportement par défaut appelle `COleControl::OnDraw`.

Pour garantir que le contrôle peut être dessiné à la fois sur l'écran et sur des contextes de périphérique de métafichier, vous ne devez utiliser que les fonctions membres qui sont prises en charge à la fois dans un écran et dans un contexte de périphérique de métafichier. Sachez que le système de coordonnées peut ne pas être exprimé en pixels.

Etant donné que l'implémentation par défaut de `OnDrawMetafile` appelle la fonction `OnDraw` du contrôle, n'utilisez que les fonctions membres qui conviennent à la fois pour un métafichier et pour un contexte de périphérique, sauf si vous remplacez `OnDrawMetafile`. Ce qui suit répertorie le sous-ensemble de fonctions membres `CDC` qui peuvent être utilisées à la fois dans un métafichier et dans écran de contexte de périphérique. Pour plus d’informations sur ces fonctions, voir la classe [CDC](../mfc/reference/cdc-class.md) dans la *référence MFC*.

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

Outre les fonctions membres `CDC`, il existe plusieurs autres fonctions compatibles dans un contexte de périphérique de métafichier. Il s’agit notamment [de CPalette::AnimatePalette](../mfc/reference/cpalette-class.md#animatepalette), [CFont::CreateFontIndirect](../mfc/reference/cfont-class.md#createfontindirect), et trois fonctions membres de: `CBrush` [CreateBrushIndirect](../mfc/reference/cbrush-class.md#createbrushindirect), [CreateDIBPatternBrush](../mfc/reference/cbrush-class.md#createdibpatternbrush), et [CreatePatternBrush](../mfc/reference/cbrush-class.md#createpatternbrush).

Fonctions qui ne sont pas enregistrées dans un metafile sont: [DrawFocusRect](../mfc/reference/cdc-class.md#drawfocusrect), [DrawIcon](../mfc/reference/cdc-class.md#drawicon), [DrawText](../mfc/reference/cdc-class.md#drawtext), [ExcludeUpdateRgn](../mfc/reference/cdc-class.md#excludeupdatergn), [FillRect](../mfc/reference/cdc-class.md#fillrect), [FrameRect](../mfc/reference/cdc-class.md#framerect), [GrayString](../mfc/reference/cdc-class.md#graystring), [InvertRect](../mfc/reference/cdc-class.md#invertrect), [ScrollDC](../mfc/reference/cdc-class.md#scrolldc), et [TabbedTextOut](../mfc/reference/cdc-class.md#tabbedtextout). Étant donné qu'un contexte de périphérique de métafichier n'est pas réellement associé à un périphérique, vous ne pouvez pas utiliser SetDIBits, GetDIBits et CreateDIBitmap avec un contexte de périphérique de métafichier. Vous pouvez utiliser SetDIBitsToDevice et StretchDIBits avec un contexte de périphérique de métafichier comme destination. [CreateCompatibleDC](../mfc/reference/cdc-class.md#createcompatibledc), [CreateCompatibleBitmap](../mfc/reference/cbitmap-class.md#createcompatiblebitmap), et [CreateDiscardableBitmap](../mfc/reference/cbitmap-class.md#creatediscardablebitmap) ne sont pas significatifs avec un DC méta-sens.

Un autre point à prendre en considération lors de l'utilisation d'un contexte de périphérique de métafichier est que le système de coordonnées peut ne pas être exprimé en pixels. Pour cette raison, tout votre code de dessin doit `OnDraw` être ajusté pour s’adapter dans le rectangle passé dans le *paramètre rcBounds.* Cela empêche la peinture accidentelle en dehors du contrôle parce que *rcBounds* représente la taille de la fenêtre du contrôle.

Une fois que vous avez implémenté le rendu de métafichier pour le contrôle, utilisez le contrôleur de test pour tester le métafichier. Pour plus d’informations sur la façon d’accéder au conteneur de test, consultez la page [Test des propriétés et des événements avec le conteneur de test](../mfc/testing-properties-and-events-with-test-container.md) .

#### <a name="to-test-the-controls-metafile-using-test-container"></a>Pour tester le métafichier du contrôle à l'aide du Contrôleur de test

1. Sur le menu **Edit** du test Container, cliquez sur **Insérez un nouveau contrôle**.

1. Dans la boîte **de contrôle Insérez,** sélectionnez le contrôle et cliquez **sur OK**.

   Le contrôle s'affiche dans le conteneur de test.

1. Au menu **De contrôle,** cliquez sur **Draw Metafile**.

   Une fenêtre distincte apparaît dans laquelle le métafichier s'affiche. Vous pouvez modifier la taille de cette fenêtre pour voir comment la mise à l'échelle affecte un métafichier du contrôle. Vous pouvez fermer cette fenêtre à tout moment.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)
