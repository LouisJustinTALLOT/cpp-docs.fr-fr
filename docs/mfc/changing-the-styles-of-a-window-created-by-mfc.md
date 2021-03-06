---
description: 'En savoir plus sur : modification des styles d’une fenêtre créée par MFC'
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
ms.openlocfilehash: 1025bf1e207a885c30105c56ebb16419e7f82fe1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339746"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Modification des styles d'une fenêtre créée par MFC

Dans sa version de la `WinMain` fonction, MFC inscrit plusieurs classes de fenêtre standard pour vous. Étant donné que vous ne modifiez généralement pas `WinMain` les MFC, cette fonction vous donne la possibilité de modifier les styles de fenêtre par défaut MFC. Cet article explique comment vous pouvez modifier les styles d’une telle classe de fenêtre préinscrite dans une application existante.

## <a name="changing-styles-in-a-new-mfc-application"></a><a name="_core_changing_styles_in_a_new_mfc_application"></a> Modification des styles dans une nouvelle application MFC

Si vous utilisez Visual C++ 2,0 ou une version ultérieure, vous pouvez modifier les styles de fenêtre par défaut dans l’Assistant application lorsque vous créez votre application. Dans la page fonctionnalités de l’interface utilisateur de l’Assistant Application, vous pouvez modifier les styles pour la fenêtre frame principale et les fenêtres enfants MDI. Pour l’un des deux types de fenêtre, vous pouvez spécifier son épaisseur de cadre (épais ou fin) et l’un des éléments suivants :

- Indique si la fenêtre a des contrôles de réduction ou d’agrandissement.

- Indique si la fenêtre apparaît initialement réduite, agrandie ou aucune.

Pour les fenêtres Frame principales, vous pouvez également spécifier si la fenêtre a un menu système. Pour les fenêtres enfants MDI, vous pouvez spécifier si la fenêtre prend en charge les volets de fractionnement.

## <a name="changing-styles-in-an-existing-application"></a><a name="_core_changing_styles_in_an_existing_application"></a> Modification des styles dans une application existante

Si vous modifiez les attributs des fenêtres dans une application existante, suivez plutôt les instructions dans le reste de cet article.

Pour modifier les attributs de fenêtre par défaut utilisés par une application Framework créée à l’aide de l’Assistant Application, remplacez la fonction membre virtuelle [PreCreateWindow](reference/cwnd-class.md#precreatewindow) de la fenêtre. `PreCreateWindow` permet à une application d’accéder au processus de création normalement géré en interne par la classe [CDocTemplate](reference/cdoctemplate-class.md) . Le Framework appelle `PreCreateWindow` juste avant la création de la fenêtre. En modifiant la structure [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) transmise à `PreCreateWindow` , votre application peut modifier les attributs utilisés pour créer la fenêtre. Par exemple, pour vous assurer qu’une fenêtre n’utilise pas de légende, utilisez l’opération de bits suivante :

[!code-cpp[NVC_MFCDocView#15](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

L’exemple d’application [CTRLBARS](../overview/visual-cpp-samples.md) illustre cette technique pour modifier les attributs d’une fenêtre. Selon les modifications apportées à votre application `PreCreateWindow` , il peut être nécessaire d’appeler l’implémentation de la classe de base de la fonction.

La discussion suivante couvre le cas SDI et le [cas MDI](#_core_the_mdi_case).

## <a name="the-sdi-case"></a><a name="_core_the_sdi_case"></a> Cas SDI

Dans une application SDI (single document interface), le style de fenêtre par défaut dans l’infrastructure est une combinaison de la **WS_OVERLAPPEDWINDOW** et des styles de **FWS_ADDTOTITLE** . **FWS_ADDTOTITLE** est un style spécifique à MFC qui indique à l’infrastructure d’ajouter le titre du document à la légende de la fenêtre. Pour modifier les attributs de fenêtre dans une application SDI, remplacez la `PreCreateWindow` fonction dans votre classe dérivée de `CFrameWnd` (laquelle des noms de l’Assistant application `CMainFrame` ). Par exemple :

[!code-cpp[NVC_MFCDocViewSDI#11](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

Ce code crée une fenêtre frame principale sans boutons réduire et agrandir et sans une bordure dimensionnable. La fenêtre est initialement centrée sur l’écran.

## <a name="the-mdi-case"></a><a name="_core_the_mdi_case"></a> Le cas MDI

Un peu plus de travail est nécessaire pour modifier le style de fenêtre d’une fenêtre enfant dans une application d’interface multidocument (MDI, multiple document interface). Par défaut, une application MDI créée à l’aide de l’Assistant application utilise la classe [CMDIChildWnd](reference/cmdichildwnd-class.md) par défaut définie dans MFC. Pour modifier le style de fenêtre d’une fenêtre enfant MDI, vous devez dériver une nouvelle classe de `CMDIChildWnd` et remplacer toutes les références à `CMDIChildWnd` dans votre projet par des références à la nouvelle classe. Le plus souvent, la seule référence à `CMDIChildWnd` dans l’application se trouve dans la fonction membre de votre application `InitInstance` .

Le style de fenêtre par défaut utilisé dans une application MDI est une combinaison des styles **WS_CHILD**, **WS_OVERLAPPEDWINDOW** et **FWS_ADDTOTITLE** . Pour modifier les attributs de fenêtre des fenêtres enfants d’une application MDI, remplacez la fonction [PreCreateWindow](reference/cwnd-class.md#precreatewindow) dans votre classe dérivée de `CMDIChildWnd` . Par exemple :

[!code-cpp[NVC_MFCDocView#16](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

Ce code crée des fenêtres MDI enfants sans bouton Agrandir.

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Styles Windows](reference/styles-used-by-mfc.md#window-styles)

- [Styles de fenêtre frame](frame-window-styles-cpp.md)

- [Styles de fenêtre](/windows/win32/winmsg/window-styles)

## <a name="see-also"></a>Voir aussi

[Styles de fenêtre frame](frame-window-styles-cpp.md)
