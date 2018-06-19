---
title: 'Menus et ressources : fusion de menus | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 252619872fc53e06629a4cbded7e3640131dc94a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351964"
---
# <a name="menus-and-resources-menu-merging"></a>Menus et ressource : fusion de menus
Cet article décrit les étapes nécessaires pour les applications de document OLE gérer la modification visuelle et l’activation en place correctement. L’activation sur place pose des problèmes pour le conteneur et le serveur les applications (composant). L’utilisateur reste dans la même fenêtre frame (dans le contexte du document conteneur), mais est en cours d’exécution une autre application (serveur). Cela nécessite une coordination entre les ressources des applications conteneur et serveur.  
  
 Les rubriques abordées dans cet article sont les suivantes :  
  
- [Dispositions de menus](#_core_menu_layouts)  
  
- [Barres d’outils et les barres d’état](#_core_toolbars_and_status_bars)  
  
##  <a name="_core_menu_layouts"></a> Dispositions de menus  
 La première étape consiste à coordonner la disposition des menus. Pour plus d’informations, consultez la **la création du Menu** section [considérations relatives à la programmation Menu](https://msdn.microsoft.com/library/ms647557.aspx) dans le Kit de développement logiciel Windows.  
  
 Applications conteneur doivent créer un nouveau menu à être utilisé uniquement lorsque des éléments incorporés sont activés sur place. Ce menu doit comporter au minimum, la commande suivante, dans l’ordre indiqué :  
  
1.  Menu fichier identique à celui utilisé lorsque les fichiers sont ouverts. (Généralement aucuns les autres éléments de menu ne sont placés avant l’élément suivant).  
  
2.  Deux séparateurs consécutifs.  
  
3.  Menu Fenêtre identique à celui utilisé lorsque les fichiers sont ouverts (uniquement si l’application conteneur dans une application MDI). Certaines applications peuvent avoir d’autres menus, par exemple un menu d’Options, qui appartiennent à ce groupe, qui reste dans le menu lorsqu’un élément incorporé est activé sur place.  
  
    > [!NOTE]
    >  Il existe peut-être d’autres menus qui affectent l’affichage du document conteneur, comme le Zoom. Ces menus du conteneur s’affichent entre les deux séparateurs de cette ressource de menu.  
  
 Applications serveur (composant) doivent également créer un nouveau menu pour l’activation sur place. Il doit être identique au menu utilisé lorsque les fichiers sont ouverts, mais sans les éléments de menu, telles que le fichier et fenêtre qui manipulent le document serveur au lieu des données. En règle générale, ce menu comprend les éléments suivants :  
  
1.  Menu Edition identique à celui utilisé lorsque les fichiers sont ouverts.  
  
2.  Séparateur.  
  
3.  Menus, tels que le menu stylet dans l’exemple d’application Scribble de modification de l’objet.  
  
4.  Séparateur.  
  
5.  Menu d’aide.  
  
 Pour obtenir un exemple, observez la disposition de certains exemples de menus sur place pour un conteneur et un serveur. Les détails de chaque élément de menu ont été supprimés pour que l’exemple plus claire. Le menu du conteneur sur place a les entrées suivantes :  
  
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
  
 Les séparateurs consécutifs indiquent où la première partie du menu serveur. Observez le menu sur place du serveur :  
  
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
  
 Les séparateurs indiquent l’emplacement du deuxième groupe de conteneur d’éléments de menu. La structure de menu qui en résulte lorsqu’un objet à partir de ce serveur est activé sur place à l’intérieur de ce conteneur ressemble à ceci :  
  
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
  
 Comme vous pouvez le voir, les séparateurs ont été remplacés par les différents groupes de menu de chaque application.  
  
 Tables d’accélérateurs associées au menu sur place doivent également être fournies par l’application serveur. Le conteneur de les incorporer dans ses propres tables d’accélérateurs.  
  
 Lorsqu’un élément incorporé est activé sur place, le framework charge le menu sur place. Puis, il demande à l’application de serveur pour le menu pour l’activation sur place et insère où se trouvent les séparateurs. Voici comment combinent des menus. Vous obtenez des menus du conteneur pour l’exploitation de l’emplacement de fichier et fenêtre, les menus à partir du serveur pour l’exploitation de l’élément.  
  
##  <a name="_core_toolbars_and_status_bars"></a> Barres d’outils et les barres d’état  
 Serveur d’applications doit créer une nouvelle barre d’outils et stocker son image bitmap dans un fichier distinct. Les applications générées par l’Assistant application stockent cette image bitmap dans un fichier appelé ITOOLBAR. BMP. La nouvelle barre d’outils remplace la barre d’outils de l’application conteneur lorsque votre élément serveur est activé sur place et doit contenir les mêmes éléments que votre barre d’outils standard, mais supprimer des icônes représentant les éléments dans les menus fichier et fenêtre.  
  
 Cette barre d’outils est chargé dans votre `COleIPFrameWnd`-classe dérivée, créé pour vous par l’Assistant application. La barre d’état est gérée par l’application conteneur. Pour plus d’informations sur l’implémentation des fenêtres de frame en place, consultez [serveurs : implémentation d’un serveur](../mfc/servers-implementing-a-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Menus et ressources (OLE)](../mfc/menus-and-resources-ole.md)   
 [Activation](../mfc/activation-cpp.md)   
 [Serveurs](../mfc/servers.md)   
 [Conteneurs](../mfc/containers.md)

