---
title: Fusion des menus aide | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- menus [MFC], merging
- merging Help menus [MFC]
- Help [MFC], for active document containers
ms.assetid: 9d615999-79ba-471a-9288-718f0c903d49
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c4d3ae9509edcbe79417bb37d02f4f585b2da653
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="help-menu-merging"></a>Fusion des menus Aide
Lorsqu’un objet est actif dans un conteneur, le menu protocole des Documents OLE de fusion donne le contrôle complet d’objet de la **aide** menu. Par conséquent, les rubriques d'aide du conteneur ne sont pas disponibles à moins que l'utilisateur désactive l'objet. L’architecture de la relation contenant-contenu de document actif développe les règles de la fusion de menus sur place afin d’autoriser le conteneur et un document actif à partager le menu. Les nouvelles règles sont simplement des conventions supplémentaires sur quel composant possède quelle partie du menu et comment le menu partagé est créé.  
  
 La nouvelle convention est simple. Dans les documents actifs, le **aide** menu comporte deux éléments de menu de niveau supérieur organisés comme suit :  
  
 `Help`  
  
 `Container Help >`  
  
 `Object Help    >`  
  
 Par exemple, lorsqu’une section Word est active dans le classeur Office, puis le **aide** menu s’affiche comme suit :  
  
 `Help`  
  
 `Binder Help >`  
  
 `Word Help   >`  
  
 Les deux éléments de menu sont des menus en cascade dans lesquels tous les éléments de menu supplémentaires spécifiques au conteneur et l'objet sont accessibles à l'utilisateur. Les éléments affichés ici varie avec le conteneur et les objets concernés.  
  
 Pour construire ce fusionnée **aide** menu, l’architecture de relation contenant-contenu de document actif modifie la procédure des Documents OLE normale. En fonction des Documents OLE, la barre de menus fusionnée peut comporter respectivement six groupes de menus, à savoir **fichier**, **modifier**, **conteneur**, `Object`, **defenêtre**, **Aide**, dans cet ordre. À chaque groupe, il peut y avoir zéro menus ou plus. Les groupes **fichier**, **conteneur**, et **fenêtre** appartiennent au conteneur et les groupes **modifier**, **(objet),** et **aide** appartient à l’objet. Lorsque l'objet souhaite réaliser la fusion de menus, il crée une barre de menus vide et la passe au conteneur. Le conteneur insère ses menus, en appelant **IOleInPlaceFrame::InsertMenu**. L’objet passe également une structure qui est un tableau de six longues valeurs (**OLEMENUGROUPWIDTHS**). Après avoir inséré les menus, le conteneur marque le nombre de menus qu'il a ajoutés dans chacun de ses groupes, puis effectue un retour. L'objet insère ses menus, en tenant compte du nombre de menus dans chaque groupe de conteneurs. Enfin, l’objet passe la barre de menus fusionnée et le tableau (contenant le nombre de menus dans chaque groupe) à OLE, qui retourne un handle opaque "descripteur de menu". Plus tard l’objet passe ce descripteur et la barre de menus fusionnée au conteneur, via **IOleInPlaceFrame::SetMenu**. À ce stade, le conteneur affiche la barre de menus fusionnée et passe le handle à l’objet OLE, afin que ce dernier puisse distribuer des messages de menu approprié.  
  
 Dans la procédure de modification de document actif, l’objet doit tout d’abord initialiser les **OLEMENUGROUPWIDTHS** éléments à zéro avant de le transmettre au conteneur. Le conteneur exécute une insertion de menu classique à une exception près : le conteneur insère un **aide** menu comme dernier élément et stocke la valeur 1 dans la dernière (sixième) entrée du **OLEMENUGROUPWIDTHS** tableau (autrement dit, width [5], qui appartient au groupe aide de l’objet). Cela **aide** menu aura qu’un seul élément qui est un sous-menu, le «**aide conteneur** > « menu en cascade comme décrit précédemment.  
  
 L’objet exécute ensuite son code d’insertion de menu normal, à ceci près qu’avant d’insérer son **aide** menu, il vérifie la sixième entrée de la **OLEMENUGROUPWIDTHS** tableau. Si la valeur est 1 et le nom du dernier menu est **aide** (ou chaîne localisée correcte), l’objet insère ses **aide** menu comme sous-menu du conteneur **aide** menu.  
  
 L’objet définit ensuite le sixième élément de **OLEMENUGROUPWIDTHS** à zéro et incrémente le cinquième élément d’une unité. Ceci indique que OLE le **aide** menu appartient au conteneur et les messages de menu correspondant à ce menu (et ses sous-menus) doivent être acheminés vers le conteneur. Il revient ensuite au conteneur de transférer `WM_INITMENUPOPUP`, **WM_SELECT**, **WM_COMMAND**et d’autres messages de menu qui appartiennent à une partie de l’objet de la **aide**  menu. Cela est accompli en utilisant `WM_INITMENU` pour effacer un indicateur qui indique au conteneur si l’utilisateur a accédé à l’objet **aide** menu. Le conteneur s’intéresse ensuite à `WM_MENUSELECT` d’entrées ou de sortie d’un élément sur le **aide** menu le conteneur ne peut pas ajoute lui-même. À l’entrée, cela signifie que l’utilisateur a accédé au menu de l’objet, afin que le conteneur définit l’indicateur « dans l’objet menu Aide » et utilise l’état de cet indicateur pour transmettre les `WM_MENUSELECT`, `WM_INITMENUPOPUP`, et **WM_COMMAND** des messages, au minimum, à la fenêtre de l’objet. (En sortie, le conteneur désactive l'indicateur, puis traite ces derniers messages lui-même.) Le conteneur doit utiliser la fenêtre retournée à partir de l’objet **IOleInPlaceActiveObejct::GetWindow** fonctionner en tant que la destination de ces messages.  
  
 Si l’objet détecte un zéro dans le sixième élément de **OLEMENUGROUPWIDTHS**, il continue selon les règles de Documents OLE normales. Cette procédure traite des conteneurs qui participent **aide** menu fusion ainsi que ceux qui ne le font pas.  
  
 Lorsque l’objet appelle **IOleInPlaceFrame::SetMenu**, avant d’afficher le menu fusionné de la barre, le conteneur vérifie si le **aide** menu a un sous-menu supplémentaire, en plus de l’élément qui a le conteneur inséré. Ce cas, le conteneur laisse son **aide** menu dans la barre de menus fusionnée. Si le **aide** menu n’est pas un sous-menu supplémentaire, le conteneur supprime ses **aide** menu dans la barre de menus fusionnée. Cette procédure traite les objets qui participent **aide** menu fusion ainsi que ceux qui ne le font pas.  
  
 Enfin, lorsqu’il est temps de désassembler le menu, l’objet supprime le texte inséré **aide** menu en plus de supprimer l’autre des menus insérés. Lorsque le conteneur supprime ses menus, il supprime son **aide** menu en plus des autres menus qu’il a insérés.  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs de documents actifs](../mfc/active-document-containers.md)

