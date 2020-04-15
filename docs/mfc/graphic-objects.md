---
title: Objets graphiques
ms.date: 11/04/2016
f1_keywords:
- HRGN
- HFONT
- HBITMAP
helpviewer_keywords:
- CRgn class [MFC], HRGN handle type
- HPEN [MFC]
- objects [MFC], graphic
- palettes [MFC], creating in device context
- pens [MFC], creating in device context
- bitmaps [MFC], creating in device contexts
- palette objects [MFC]
- memory [MFC], display contexts
- MFC, graphic objects
- regions [MFC], creating in device context
- CPen class [MFC], HPEN handle type
- GDI objects [MFC]
- HRGN [MFC]
- graphic objects [MFC]
- GDI objects [MFC], graphic-object classes
- CFont class [MFC], HFONT handle type
- HFONT and class CFont [MFC]
- HBITMAP and class CBitmap [MFC]
- fonts [MFC], creating in device context
- images [MFC], graphic objects [MFC]
- CBitmap class [MFC], HBITMAP handle type
- HPALETTE and class CPalette [MFC]
- CBrush class [MFC], HBRUSH handle type
- objects [MFC], graphic objects
- drawing [MFC], in device contexts
- device contexts [MFC], graphic objects [MFC]
- brushes [MFC], creating in device context
- region objects [MFC]
- pen objects [MFC]
- GDI [MFC], graphic-object classes
- graphic objects [MFC], creating in device context
- HBRUSH and class CBrush [MFC]
- painting and device context [MFC]
- CPalette class [MFC], HPALETTE handle type
ms.assetid: 41963b25-34b7-4343-8446-34ba516b83ca
ms.openlocfilehash: 0201e53114b71c02877762f89cc65fc46d17700c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370524"
---
# <a name="graphic-objects"></a>Objets graphiques

Windows propose divers outils de dessin à utiliser dans des contextes de périphériques. On trouve des stylets pour tracer des lignes, des pinceaux pour remplir des intérieurs et des polices pour dessiner du texte. MFC propose des classes d'objets graphiques équivalentes aux outils de dessin de Windows. Le tableau ci-dessous présente les classes disponibles et les types de handle GDI (Graphics Device Interface) Windows équivalents.

> [!NOTE]
> Pour plus d’informations, consultez la [documentation GDI SDK](/windows/win32/gdiplus/-gdiplus-gdi-start).

Cet article explique l'utilisation de ces classes d'objets graphiques :

### <a name="classes-for-windows-gdi-objects"></a>Classes pour objets Windows GDI

|Classe|Type de handle Windows|
|-----------|-------------------------|
|[CPen](../mfc/reference/cpen-class.md)|`HPEN`|
|[CBrush](../mfc/reference/cbrush-class.md)|`HBRUSH`|
|[CFont](../mfc/reference/cfont-class.md)|**HFONT**|
|[CBitmap](../mfc/reference/cbitmap-class.md)|`HBITMAP`|
|[CPalette](../mfc/reference/cpalette-class.md)|`HPALETTE`|
|[CRgn](../mfc/reference/crgn-class.md)|**HRGN**|

> [!NOTE]
> La classe [CImage](../atl-mfc-shared/reference/cimage-class.md) fournit un support bitmap amélioré.

À chaque classe d'objets graphiques de la bibliothèque de classes correspond un constructeur qui vous permet de créer des objets graphiques de cette classe, que vous devez ensuite initialiser avec la fonction de création appropriée, comme `CreatePen`.

À chaque classe d'objets graphiques de la bibliothèque de classes correspond un opérateur de conversion de type (transtypage) chargé de convertir un objet MFC en handle Windows associé. Le handle obtenu est valide tant que l'objet associé ne le détache pas. Utilisez la fonction `Detach` de membre de l’objet pour détacher la poignée.

Le code suivant convertit un `CPen` objet en handle Windows :

[!code-cpp[NVC_MFCDocViewSDI#5](../mfc/codesnippet/cpp/graphic-objects_1.cpp)]

#### <a name="to-create-a-graphic-object-in-a-device-context"></a>Pour créer un objet graphique dans un contexte de périphérique

1. Définissez un objet graphique sur le frame de pile. Initialisez l'objet avec la fonction de création propre au type, par exemple, `CreatePen`. Vous pouvez aussi initialiser l'objet dans le constructeur. Voir la discussion de la [création en une seule étape et en deux étapes](../mfc/one-stage-and-two-stage-construction-of-objects.md), qui fournit un code d’exemple.

1. [Sélectionnez l’objet dans le contexte actuel de l’appareil,](../mfc/selecting-a-graphic-object-into-a-device-context.md)enregistrant l’ancien objet graphique qui a été sélectionné auparavant.

1. Quand vous en avez terminé avec l'objet graphique actuel, sélectionnez à nouveau l'ancien objet graphique dans le contexte de périphérique pour restaurer son état.

1. Autorisez la suppression automatique de l'objet graphique alloué par le frame dès qu'il est hors de portée.

> [!NOTE]
> Si vous prévoyez d'utiliser un objet graphique de façon récurrente, vous pouvez l'allouer une fois et le sélectionner dans un contexte de périphérique chaque fois que vous en avez besoin. Veillez à supprimer cet objet dès que vous n'en avez plus besoin.

### <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Construction d'objets graphiques en une ou deux étapes](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Exemple de construction d'un stylet en une ou deux étapes](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Sélection d’un objet graphique dans un contexte d’appareil](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Contextes de périphérique](../mfc/device-contexts.md)

## <a name="see-also"></a>Voir aussi

[Objets fenêtres](../mfc/window-objects.md)
