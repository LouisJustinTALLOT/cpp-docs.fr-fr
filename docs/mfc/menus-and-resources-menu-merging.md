---
description: 'En savoir plus sur les menus et les ressources : fusion de menus'
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
ms.openlocfilehash: b326e02fb4dbdaaef0ae6015fef6b647cc85b907
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227973"
---
# <a name="menus-and-resources-menu-merging"></a>Menus et ressource : fusion de menus

Cet article détaille les étapes nécessaires pour que les applications de document OLE gèrent correctement l’édition visuelle et l’activation sur place. L’activation sur place pose un défi pour les applications de conteneur et de serveur (composant). L’utilisateur reste dans la même fenêtre frame (dans le contexte du document conteneur), mais exécute en fait une autre application (le serveur). Cela nécessite une coordination entre les ressources des applications conteneur et serveur.

Les sujets abordés dans cet article sont les suivants :

- [Dispositions de menu](#_core_menu_layouts)

- [Barres d’outils et barres d’État](#_core_toolbars_and_status_bars)

## <a name="menu-layouts"></a><a name="_core_menu_layouts"></a> Dispositions de menu

La première étape consiste à coordonner les dispositions des menus. Les applications de conteneur doivent créer un menu à utiliser uniquement lorsque des éléments incorporés sont activés sur place. Au minimum, ce menu doit se composer des éléments suivants, dans l’ordre indiqué :

1. Menu fichier identique à celui utilisé lorsque les fichiers sont ouverts. (En général, aucun autre élément de menu n’est placé avant l’élément suivant.)

1. Deux séparateurs consécutifs.

1. Menu fenêtre identique à celui utilisé lorsque les fichiers sont ouverts (uniquement si l’application conteneur est dans une application MDI). Certaines applications peuvent avoir d’autres menus, tels qu’un menu d’options, qui appartiennent à ce groupe, qui reste dans le menu lorsqu’un élément incorporé est activé sur place.

    > [!NOTE]
    >  Il peut y avoir d’autres menus qui affectent la vue du document conteneur, tels que Zoom. Ces menus de conteneur apparaissent entre les deux séparateurs de cette ressource de menu.

Les applications serveur (composant) doivent également créer un nouveau menu spécifiquement pour l’activation sur place. Elle doit être similaire au menu utilisé lorsque des fichiers sont ouverts, mais sans éléments de menu, tels qu’un fichier et une fenêtre qui manipulent le document serveur au lieu des données. En règle générale, ce menu se compose des éléments suivants :

1. Menu Edition identique à celui utilisé lorsque les fichiers sont ouverts.

1. Séparateur.

1. Menus d’édition d’objets, tels que le menu stylet dans l’exemple d’application Scribble.

1. Séparateur.

1. Menu aide.

Pour obtenir un exemple, examinez la disposition de certains exemples de menus en place pour un conteneur et un serveur. Les détails de chaque élément de menu ont été supprimés pour rendre l’exemple plus clair. Le menu sur place du conteneur contient les entrées suivantes :

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

Les séparateurs consécutifs indiquent où la première partie du menu du serveur doit être insérée. Examinez maintenant le menu sur place du serveur :

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

Les séparateurs indiquent ici où le deuxième groupe d’éléments de menu du conteneur doit être placé. La structure de menu obtenue lorsqu’un objet de ce serveur est activé sur place à l’intérieur de ce conteneur ressemble à ceci :

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

Les tables d’accélérateurs associées au menu sur place doivent également être fournies par l’application serveur. Le conteneur les incorpore dans ses propres tables d’accélérateurs.

Lorsqu’un élément incorporé est activé sur place, le Framework charge le menu sur place. Elle demande ensuite à l’application serveur de son menu une activation sur place et l’insère là où se trouvent les séparateurs. C’est ainsi que les menus sont combinés. Vous recevez des menus à partir du conteneur pour le fonctionnement au niveau du fichier et de la fenêtre, et vous recevez des menus du serveur pour l’utilisation de l’élément.

## <a name="toolbars-and-status-bars"></a><a name="_core_toolbars_and_status_bars"></a> Barres d’outils et barres d’État

Les applications serveur doivent créer une nouvelle barre d’outils et stocker son bitmap dans un fichier séparé. Les applications générées par l’Assistant Application stockent cette image bitmap dans un fichier appelé ITOOLBAR.BMP. La nouvelle barre d’outils remplace la barre d’outils de l’application conteneur lorsque l’élément de votre serveur est activé sur place et doit contenir les mêmes éléments que votre barre d’outils normale, mais supprimer les icônes représentant les éléments dans les menus fichier et fenêtre.

Cette barre d’outils est chargée dans votre `COleIPFrameWnd` classe dérivée de, créée pour vous par l’Assistant Application. La barre d’État est gérée par l’application conteneur. Pour plus d’informations sur l’implémentation des fenêtres Frame sur place, consultez [serveurs : implémentation d’un serveur](servers-implementing-a-server.md).

## <a name="see-also"></a>Voir aussi

[Menus et ressources (OLE)](menus-and-resources-ole.md)<br/>
[Activation](activation-cpp.md)<br/>
[Serveurs](servers.md)<br/>
[Containers](containers.md)
