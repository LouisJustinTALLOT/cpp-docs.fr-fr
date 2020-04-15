---
title: Modification des styles d'une fenêtre créée par MFC
ms.date: 11/04/2016
helpviewer_keywords:
- window styles [MFC]
- WS_OVERLAPPEDWINDOW macro [MFC]
- single document interface (SDI), changing window attributes
- MDI [MFC], window styles
- windows [MFC], MFC
- child windows [MFC], styles
- MFC, windows
- CFrameWnd class [MFC], window styles
- CREATESTRUCT macro [MFC]
- CMDIChildWnd class [MFC], changing window styles
- multidocument interface style
- PreCreateWindow method [MFC], window styles
- single document interface (SDI), style
- default window style
- defaults [MFC], window style
- PreCreateWindow method [MFC], changing window styles
- CMainFrame class [MFC]
- styles [MFC], windows
ms.assetid: 77fa4f03-96b4-4687-9ade-41e46f7e4b0a
ms.openlocfilehash: 221092eb25a4f044cda5b379d6774659d9e9d2d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374595"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Modification des styles d'une fenêtre créée par MFC

Dans sa version `WinMain` de la fonction, MFC vous enregistre plusieurs classes de fenêtre standard. Parce que vous n’éditez pas `WinMain`normalement MFC , cette fonction ne vous donne aucune possibilité de changer les styles de fenêtre par défaut MFC. Cet article explique comment vous pouvez modifier les styles d’une telle classe de fenêtre préenregistrée dans une application existante.

## <a name="changing-styles-in-a-new-mfc-application"></a><a name="_core_changing_styles_in_a_new_mfc_application"></a>Changer les styles dans une nouvelle application MFC

Si vous utilisez Visual CM 2.0 ou plus tard, vous pouvez modifier les styles de fenêtre par défaut dans l’Assistant d’Application lorsque vous créez votre application. Dans la page Des fonctionnalités d’interface utilisateur de l’Assistant d’application, vous pouvez modifier les styles de votre fenêtre de cadre principale et de fenêtres pour enfants MDI. Pour l’un ou l’autre type de fenêtre, vous pouvez spécifier son épaisseur de cadre (épaisse ou mince) et l’un des éléments suivants :

- Que la fenêtre dispose de contrôles Minimize ou Maxim.

- Que la fenêtre semble initialement minimisée, maximisée, ou ni l’un ni l’autre.

Pour les fenêtres à cadre principal, vous pouvez également spécifier si la fenêtre dispose d’un menu système. Pour les fenêtres pour enfants MDI, vous pouvez spécifier si la fenêtre prend en charge les vitres de splitter.

## <a name="changing-styles-in-an-existing-application"></a><a name="_core_changing_styles_in_an_existing_application"></a>Changer les styles dans une application existante

Si vous modifiez les attributs de fenêtre dans une application existante, suivez les instructions dans le reste de cet article à la place.

Pour modifier les attributs de fenêtre par défaut utilisés par une application-cadre créée avec l’Assistant d’Application, remplacez la fonction de membre virtuel [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) de la fenêtre. `PreCreateWindow`permet à une application d’accéder au processus de création normalement géré en interne par la classe [CDocTemplate.](../mfc/reference/cdoctemplate-class.md) Le cadre `PreCreateWindow` appelle juste avant la création de la fenêtre. En modifiant la structure [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) passée à `PreCreateWindow`, votre application peut modifier les attributs utilisés pour créer la fenêtre. Par exemple, pour vous assurer qu’une fenêtre n’utilise pas de légende, utilisez l’opération bitwise suivante :

[!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

[L’application d’échantillon CTRLBARS](../overview/visual-cpp-samples.md) démontre cette technique pour changer les attributs de fenêtre. Selon les changements apportés `PreCreateWindow`par votre application, il peut être nécessaire d’appeler la mise en œuvre de la classe de base de la fonction.

La discussion suivante porte sur l’affaire SDI et [l’affaire MDI](#_core_the_mdi_case).

## <a name="the-sdi-case"></a><a name="_core_the_sdi_case"></a>L’affaire SDI

Dans une seule application d’interface de document (SDI), le style de fenêtre par défaut dans le cadre est une combinaison des styles **WS_OVERLAPPEDWINDOW** et **FWS_ADDTOTITLE.** **FWS_ADDTOTITLE** est un style spécifique à MFC qui demande au cadre d’ajouter le titre de document à la légende de la fenêtre. Pour modifier les attributs de fenêtre dans `PreCreateWindow` une application SDI, remplacez la fonction de votre classe dérivée `CFrameWnd` (dont l’Assistant d’application nomme `CMainFrame`). Par exemple :

[!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

Ce code crée une fenêtre de cadre principale sans boutons Minimize et Maximize et sans bordure importante. La fenêtre est d’abord centrée sur l’écran.

## <a name="the-mdi-case"></a><a name="_core_the_mdi_case"></a>L’affaire MDI

Un peu plus de travail est nécessaire pour changer le style de fenêtre d’une fenêtre d’enfant dans une interface documentaire multiple (MDI) application. Par défaut, une application MDI créée avec l’Assistant d’Application utilise la classe [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) par défaut définie dans MFC. Pour changer le style de fenêtre d’une fenêtre pour `CMDIChildWnd` enfant MDI, vous devez tirer une nouvelle classe de et remplacer toutes les références à `CMDIChildWnd` dans votre projet avec des références à la nouvelle classe. Très probablement, la `CMDIChildWnd` seule référence à l’application `InitInstance` est située dans la fonction de membre de votre application.

Le style de fenêtre par défaut utilisé dans une application MDI est une combinaison de la **WS_CHILD**, **WS_OVERLAPPEDWINDOW**, et **FWS_ADDTOTITLE** styles. Pour modifier les attributs de fenêtre des fenêtres pour enfants d’une application MDI, `CMDIChildWnd`remplacez la fonction [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) dans votre classe dérivée de . Par exemple :

[!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

Ce code crée des fenêtres pour enfants MDI sans bouton Maximize.

### <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Styles Windows](../mfc/reference/styles-used-by-mfc.md#window-styles)

- [Styles de fenêtre de cadre](../mfc/frame-window-styles-cpp.md)

- [Styles de fenêtre](/windows/win32/winmsg/window-styles)

## <a name="see-also"></a>Voir aussi

[Styles de fenêtre frame](../mfc/frame-window-styles-cpp.md)
