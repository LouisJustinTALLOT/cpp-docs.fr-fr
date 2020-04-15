---
title: 'Menus et ressource : fusion de menus'
ms.date: 11/04/2016
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
ms.openlocfilehash: 149af83bd53b7a97fd264bd6b18701fc9f64ea1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364767"
---
# <a name="menus-and-resources-menu-merging"></a>Menus et ressource : fusion de menus

Cet article détaille les étapes nécessaires aux applications de documents OLE pour gérer correctement l’édition visuelle et l’activation sur place. L’activation place pose un défi pour les applications de conteneurs et de serveurs (composants). L’utilisateur reste dans la même fenêtre de cadre (dans le cadre du document de conteneur) mais est en fait en cours d’exécution d’une autre application (le serveur). Cela nécessite une coordination entre les ressources des applications du conteneur et du serveur.

Les sujets abordés dans cet article sont les suivants :

- [Mises en page du menu](#_core_menu_layouts)

- [Barres d’outils et de statut](#_core_toolbars_and_status_bars)

## <a name="menu-layouts"></a><a name="_core_menu_layouts"></a>Mises en page du menu

La première étape consiste à coordonner les dispositions du menu. Les applications de conteneurs doivent créer un nouveau menu à utiliser uniquement lorsque des éléments intégrés sont activés en place. Au minimum, ce menu doit consister en ce qui suit, dans l’ordre énuméré :

1. Menu de fichiers identique à celui utilisé lorsque les fichiers sont ouverts. (Habituellement, aucun autre élément de menu n’est placé avant l’article suivant.)

1. Deux séparateurs consécutifs.

1. Menu de fenêtre identique à celui utilisé lorsque les fichiers sont ouverts (seulement si l’application de conteneur dans une application MDI). Certaines applications peuvent avoir d’autres menus, comme un menu Options, qui appartiennent à ce groupe, qui reste sur le menu quand un élément intégré est activé en place.

    > [!NOTE]
    >  Il peut y avoir d’autres menus qui affectent la vue du document de conteneur, comme Zoom. Ces menus de conteneurs apparaissent entre les deux séparateurs dans cette ressource de menu.

Les applications serveur (composant) devraient également créer un nouveau menu spécifiquement pour l’activation sur place. Il devrait être comme le menu utilisé lorsque les fichiers sont ouverts, mais sans éléments de menu, tels que Fichier et fenêtre qui manipulent le document serveur au lieu des données. Typiquement, ce menu se compose de ce qui suit:

1. Modifier le menu identique à celui utilisé lorsque les fichiers sont ouverts.

1. Séparateur.

1. Menus d’édition d’objets, tels que le menu Pen dans l’application échantillon Scribble.

1. Séparateur.

1. Menu d’aide.

Par exemple, regardez la disposition de certains échantillons de menus en place pour un conteneur et un serveur. Les détails de chaque élément de menu ont été supprimés pour rendre l’exemple plus clair. Le menu place du conteneur comporte les entrées suivantes :

```
IDR_CONTAINERTYPE_CNTR_IP MENU PRELOAD DISCARDABLE
BEGIN
    POPUP "&File C1"
    MENUITEM SEPARATOR
    POPUP "&Zoom C2"
    MENUITEM SEPARATOR
    POPUP "&Options C3"
    POPUP "&Window C3"
END
```

Les séparateurs consécutifs indiquent où la première partie du menu du serveur doit aller. Maintenant, regardez le menu en place du serveur:

```
IDR_SERVERTYPE_SRVR_IP MENU PRELOAD DISCARDABLE
BEGIN
    POPUP "&Edit S1"
    MENUITEM SEPARATOR
    POPUP "&Format S2"
    MENUITEM SEPARATOR
    POPUP "&Help S3"
END
```

Les séparateurs indiquent ici où le deuxième groupe d’éléments de menu de conteneurs devrait aller. La structure de menu résultante quand un objet de ce serveur est activé en place à l’intérieur de ce conteneur ressemble à ceci:

```
BEGIN
    POPUP "&File C1"
    POPUP "&Edit S1"
    POPUP "&Zoom C2"
    POPUP "&Format S2"
    POPUP "&Options C3
    POPUP "&Window C3"
    POPUP "&Help S3"
END
```

Comme vous pouvez le voir, les séparateurs ont été remplacés par les différents groupes du menu de chaque application.

Les tables d’accélérateur associées au menu place doivent également être fournies par l’application serveur. Le conteneur les incorporera dans ses propres tables d’accélérateur.

Lorsqu’un élément intégré est activé en place, le cadre charge le menu sur place. Il demande ensuite à l’application serveur pour son menu pour l’activation en place et l’insère là où se trouvent les séparateurs. C’est ainsi que les menus se combinent. Vous obtenez des menus à partir du conteneur pour fonctionner sur le fichier et le placement de fenêtre, et vous obtenez des menus à partir du serveur pour fonctionner sur l’article.

## <a name="toolbars-and-status-bars"></a><a name="_core_toolbars_and_status_bars"></a>Barres d’outils et de statut

Les applications serveur doivent créer une nouvelle barre d’outils et stocker sa bitmap dans un fichier séparé. Les applications générées par les assistants d’application stockent cette bitmap dans un fichier appelé ITOOLBAR. Bmp. La nouvelle barre d’outils remplace la barre d’outils de l’application de conteneur lorsque l’élément de votre serveur est activé en place, et doit contenir les mêmes éléments que votre barre d’outils normale, mais supprimer les icônes représentant les éléments sur les menus de fichier et de fenêtre.

Cette barre d’outils `COleIPFrameWnd`est chargée dans votre classe dérivée, créée pour vous par l’assistant d’application. La barre d’état est gérée par l’application de conteneur. Pour plus d’informations sur la mise en œuvre de fenêtres à cadre sur place, voir [Serveurs: Implementing a Server](../mfc/servers-implementing-a-server.md).

## <a name="see-also"></a>Voir aussi

[Menus et ressources (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Activation](../mfc/activation-cpp.md)<br/>
[Serveurs](../mfc/servers.md)<br/>
[Containers](../mfc/containers.md)
