---
title: Éléments de l'interface
ms.date: 11/19/2018
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
ms.openlocfilehash: 4d4d81287cb30a7d3608025085cdb3f9a208147a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619992"
---
# <a name="interface-elements"></a>Éléments de l'interface

Ce document décrit les éléments d’interface qui ont été introduits dans Visual Studio 2008 SP1 et décrit également les différences avec la version antérieure de la bibliothèque.

L'illustration suivante montre une application générée à l'aide des nouveaux éléments d'interface.

![Exemple d’application MFC Feature Pack](../mfc/media/mfc_featurepack.png "Exemple d’application MFC Feature Pack")

## <a name="window-docking"></a>Ancrage de fenêtre

La fonctionnalité d’ancrage de fenêtre ressemble à l’ancrage de fenêtre utilisé par l’interface utilisateur graphique de Visual Studio.

## <a name="control-bars-are-now-panes"></a>Les barres de contrôle sont désormais des volets

Les barres de contrôle sont maintenant appelées volets et sont dérivées de la [classe CBasePane](reference/cbasepane-class.md). Dans les versions antérieures de MFC, la classe de base des barres de contrôle était `CControlBar`.

La fenêtre frame principale de l’application est généralement représentée par la classe [CFrameWndEx](reference/cframewndex-class.md) ou la [classe CMDIFrameWndEx](reference/cmdiframewndex-class.md). Le cadre principal est appelé *site d’ancrage*. Les volets peuvent avoir l'un des trois types de parents suivants : un site d'ancrage, une barre d'ancrage ou une fenêtre mini-frame.

Il existe deux types de volets : non redimensionnables et redimensionnables. Les volets redimensionnables, tels que les barres d'état et les barres d'outils, peuvent être redimensionnés à l'aide de séparateurs ou de curseurs. Ils peuvent former des conteneurs (un volet peut être ancré à un autre volet, ce qui crée un séparateur entre eux). Toutefois, ils ne peuvent pas être attachés (ancrés) aux barres d'ancrage.

Si votre application utilise des volets non redimensionnables, dérivez-les de la [classe CPane](reference/cpane-class.md).  Si votre application utilise des volets redimensionnables, dérivez-les de la [classe CDockablePane](reference/cdockablepane-class.md)

## <a name="dock-site"></a>Site d'ancrage

Le site d'ancrage (ou fenêtre frame principale) possède tous les volets et fenêtres mini-frame dans une application. Le site d’ancrage contient un membre [CDockingManager](reference/cdockingmanager-class.md) . Ce membre gère la liste de tous les volets qui appartiennent au site d'ancrage. La liste est triée de sorte que les volets créés aux bords externes du site d'ancrage soient placés au début de la liste. Lorsque le framework redessine le site d'ancrage, elle effectue une boucle sur cette liste et ajuste la disposition de chaque volet pour inclure le rectangle englobant actuel du site d'ancrage. Vous pouvez appeler `AdjustDockingLayout` ou `RecalcLayout` lorsque vous devez ajuster la disposition d'ancrage, et le framework redirige cet appel vers le gestionnaire d'ancrage.

## <a name="dock-bars"></a>Barres d'ancrage

Chaque fenêtre frame principale peut positionner des *barres d’ancrage* le long de ses bordures. Une barre d’ancrage est un volet qui appartient à une [classe CDockSite](reference/cdocksite-class.md). Les barres d’ancrage peuvent accepter des objets dérivés de [CPane](reference/cpane-class.md), tels que des barres d’outils. Pour créer des barres d'ancrage lorsque la fenêtre frame principale est initialisée, appelez `EnableDocking`. Pour activer les barres de masquage automatique, appelez `EnableAutoHideBars`. `EnableAutoHideBars`crée des objets [CAutoHideDockSite](reference/cautohidedocksite-class.md) et les positionne en regard de chaque barre d’ancrage.

Chaque barre d'ancrage est divisée en lignes d'ancrage. Les lignes Dock sont représentées par la [classe CDockingPanesRow](reference/cdockingpanesrow-class.md). Chaque ligne d'ancrage contient une liste de barres d'outils. Si un utilisateur ancre une barre d'outils ou déplace la barre d'outils d'une ligne à une autre de la même barre d'ancrage, le framework crée une ligne et redimensionne la barre d'ancrage en conséquence, ou elle positionne la barre d'outils sur une ligne existante.

## <a name="mini-frame-windows"></a>Fenêtres mini-frame

Un volet flottant réside dans une fenêtre mini-frame. Les fenêtres mini-frame sont représentées par deux classes : la [classe CMDITabInfo](reference/cmditabinfo-class.md) (qui ne peut contenir qu’un seul volet) et la [classe CMultiPaneFrameWnd](reference/cmultipaneframewnd-class.md) (qui peut contenir plusieurs volets). Pour détacher un volet dans votre code, appelez [CBasePane :: FloatPane](reference/cbasepane-class.md#floatpane). Une fois qu'un volet est rendu flottant, le framework crée automatiquement une fenêtre mini-frame qui devient le parent du volet flottant. Lorsque le volet flottant est ancré, le framework réinitialise son parent, et le volet flottant devient une barre d'ancrage (pour les barres d'outils) ou un site d'ancrage (pour les volets redimensionnables).

## <a name="pane-dividers"></a>Diviseurs de volet

Les diviseurs de volet (également appelés curseurs ou séparateurs) sont représentés par la [classe CPaneDivider](reference/cpanedivider-class.md). Lorsqu'un utilisateur ancre un volet, le framework crée des diviseurs de volet, que le volet soit ancré au site d'ancrage ou à un autre volet. Lorsqu’un volet est ancré au site d’ancrage, le séparateur de volets est appelé *diviseur de volet par défaut*. Le diviseur de volet par défaut est chargé de la disposition de tous les volets d'ancrage dans le site d'ancrage. Le gestionnaire d'ancrage gère une liste de diviseurs de volet par défaut et une liste de volets. Les gestionnaires d'ancrage sont chargés de la disposition de tous les volets d'ancrage.

## <a name="containers"></a>Containers

Tous les volets redimensionnables, une fois ancrés entre eux, sont conservés dans des conteneurs. Les conteneurs sont représentés par la [classe CPaneContainer](reference/cpanecontainer-class.md). Chaque conteneur possède des pointeurs vers son volet gauche, volet droit, sous-conteneur gauche, sous-conteneur droit ainsi que vers le séparateur entre les parties gauche et droite. (*Gauche* et *droite* ne font pas référence aux côtés physiques mais identifient plutôt les branches d’une structure arborescente.) De cette façon, nous pouvons créer une arborescence de volets et de séparateurs et, par conséquent, obtenir des dispositions complexes des volets qui peuvent être redimensionnés ensemble. La classe `CPaneContainer` gère l’arborescence des conteneurs ; elle gère également deux listes de volets et de curseurs qui résident dans cette arborescence. Les gestionnaires de conteneur de volet sont généralement incorporés dans les curseurs et les fenêtres mini-frame par défaut qui comportent plusieurs volets.

## <a name="auto-hide-control-bars"></a>Masquer automatiquement les barres de contrôle

Par défaut, chaque `CDockablePane` prend en charge la fonctionnalité de masquage automatique. Lorsqu'un utilisateur clique sur le bouton en forme d'épingle dans la légende de `CDockablePane`, le framework bascule le volet en mode de masquage automatique. Pour gérer le clic, l’infrastructure crée une [classe CMFCAutoHideBar](reference/cmfcautohidebar-class.md) et une [classe cmfcautohidebutton,](reference/cmfcautohidebutton-class.md) associée à l' `CMFCAutoHideBar` objet. Le Framework place le nouveau `CMFCAutoHideBar` sur le [CAutoHideDockSite](reference/cautohidedocksite-class.md). Elle attache également `CMFCAutoHideButton` à la barre d'outils. La [classe CDockingManager](reference/cdockingmanager-class.md) gère le `CDockablePane` .

## <a name="tabbed-control-bars-and-outlook-bars"></a>Barres de contrôle et barres Outlook avec onglets

La [classe CMFCBaseTabCtrl](reference/cmfcbasetabctrl-class.md) implémente les fonctionnalités de base d’une fenêtre à onglets avec des onglets détachables. Pour utiliser un `CMFCBaseTabCtrl` objet, initialisez une [classe CBaseTabbedPane](reference/cbasetabbedpane-class.md) dans votre application. La classe `CBaseTabbedPane` est dérivée de `CDockablePane` et gère un pointeur vers un objet `CMFCBaseTabCtrl`. La classe `CBaseTabbedPane` permet aux utilisateurs d'ancrer et de redimensionner les barres de contrôle avec onglets. Utilisez [CDockablePane :: AttachToTabWnd](reference/cdockablepane-class.md#attachtotabwnd) pour créer dynamiquement des barres de contrôles ancrées et avec onglets.

Le contrôle de barre Outlook est également basé sur les barres avec onglets. La [classe CMFCOutlookBar](reference/cmfcoutlookbar-class.md) est dérivée de `CBaseTabbedPane` . Pour plus d’informations sur l’utilisation de la barre Outlook, consultez [CMFCOutlookBar, classe](reference/cmfcoutlookbar-class.md).

## <a name="see-also"></a>Voir aussi

[Concepts](mfc-concepts.md)
