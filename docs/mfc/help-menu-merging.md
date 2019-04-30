---
title: Fusion des menus Aide
ms.date: 11/04/2016
helpviewer_keywords:
- menus [MFC], merging
- merging Help menus [MFC]
- Help [MFC], for active document containers
ms.assetid: 9d615999-79ba-471a-9288-718f0c903d49
ms.openlocfilehash: e1e8f9af696b6ea4cd485f4215e1c8425098e987
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396403"
---
# <a name="help-menu-merging"></a>Fusion des menus Aide

Lorsqu’un objet est actif dans un conteneur, le menu protocole des Documents OLE de fusion permet de contrôler l’objet de la **aide** menu. Par conséquent, les rubriques d'aide du conteneur ne sont pas disponibles à moins que l'utilisateur désactive l'objet. L'architecture de la relation contenant-contenu de document actif examine les règles de la fusion de menus sur place afin d'autoriser le conteneur et un document actif à partager le menu. Les nouvelles règles sont simplement des conventions supplémentaires sur quel composant possède quelle partie du menu et comment le menu partagé est créé.

La nouvelle convention est simple. Dans les documents actifs, le **aide** menu comporte deux éléments de menu de niveau supérieur organisés comme suit :

`Help`

`Container Help >`

`Object Help    >`

Par exemple, lorsqu’une section Word est active dans le classeur Office, puis le **aide** menu s’affiche comme suit :

`Help`

`Binder Help >`

`Word Help   >`

Les deux éléments de menu sont des menus en cascade dans lesquels tous les éléments de menu supplémentaires spécifiques au conteneur et l'objet sont accessibles à l'utilisateur. Les éléments affichés ici varie avec le conteneur et les objets concernés.

Pour construire ce fusionnées **aide** menu, l’architecture de relation contenant-contenu de document actif modifie la procédure de Documents OLE normale. En fonction des Documents OLE, la barre de menus fusionnée peut comporter respectivement six groupes de menus, à savoir **fichier**, **modifier**, **conteneur**, **objet**,  **Fenêtre**, **aide**, dans cet ordre. À chaque groupe, il peut y avoir zéro menus ou plus. Les groupes **fichier**, **conteneur**, et **fenêtre** appartiennent au conteneur et les groupes **modifier**, **Object,** et **aide** appartiennent à l’objet. Lorsque l'objet souhaite réaliser la fusion de menus, il crée une barre de menus vide et la passe au conteneur. Le conteneur insère ensuite ses menus, en appelant `IOleInPlaceFrame::InsertMenus`. L’objet passe également une structure qui est un tableau de six longues valeurs (**OLEMENUGROUPWIDTHS**). Après avoir inséré les menus, le conteneur marque le nombre de menus qu'il a ajoutés dans chacun de ses groupes, puis effectue un retour. L'objet insère ses menus, en tenant compte du nombre de menus dans chaque groupe de conteneurs. Enfin, l'objet passe la barre de menus fusionnée et le tableau (contenant le nombre de menus dans chaque groupe) à OLE, qui retourne un handle opaque "descripteur de menu". Plus tard l’objet passe ce handle et la barre de menus fusionnée au conteneur, via `IOleInPlaceFrame::SetMenu`. À ce stade, le conteneur affiche la barre de menus fusionnée et passe le handle à l’objet OLE, afin que ce dernier puisse distribuer des messages de menu approprié.

Dans la procédure de modification de document actif, l’objet doit tout d’abord initialiser les **OLEMENUGROUPWIDTHS** éléments à zéro avant de le transmettre au conteneur. Le conteneur effectue ensuite une insertion de menu normal avec une exception près : Le conteneur insère un **aide** menu comme dernier élément et stocke la valeur 1 dans la dernière (sixième) entrée du **OLEMENUGROUPWIDTHS** tableau (autrement dit, width [5], qui appartient au groupe d’aide de l’objet). Cela **aide** menu aura qu’un seul élément qui est un sous-menu, le «**aide conteneur** > « menu en cascade comme décrit précédemment.

L’objet exécute ensuite son code d’insertion de menu normal, à ceci près qu’avant d’insérer son **aide** menu, il vérifie la sixième entrée du **OLEMENUGROUPWIDTHS** tableau. Si la valeur est 1 et le nom du dernier menu est **aide** (ou chaîne localisée correcte), insère l’objet son **aide** menu comme sous-menu de du conteneur **vous aider à** menu.

L’objet définit ensuite le sixième élément de **OLEMENUGROUPWIDTHS** à zéro et incrémente le cinquième élément d’une unité. Cela informe OLE qui le **aide** menu appartient au conteneur et les messages de menu correspondant à ce menu (et ses sous-menus) doivent être acheminés vers le conteneur. Il est ensuite la responsabilité du conteneur de transférer **WM_INITMENUPOPUP**, **WM_SELECT**, **WM_COMMAND**et d’autres messages associés au menu qui appartiennent à l’objet partie de la **aide** menu. Cela est accompli en utilisant **WM_INITMENU** pour effacer un indicateur qui indique au conteneur si l’utilisateur a accédé dans l’objet **aide** menu. Le conteneur s’intéresse ensuite à **WM_MENUSELECT** d’entrées ou de sortie à partir de n’importe quel élément sur le **aide** menu lui-même n’a pas ajouté par le conteneur. À l’entrée, cela signifie que l’utilisateur a accédé au menu de l’objet, afin que le conteneur définit l’indicateur « dans l’objet menu Aide » et utilise l’état de cet indicateur pour transférer les **WM_MENUSELECT**, **WM_INITMENUPOPUP**et  **WM_COMMAND** messages, au minimum, à la fenêtre de l’objet. (En sortie, le conteneur désactive l'indicateur, puis traite ces derniers messages lui-même.) Le conteneur doit utiliser la fenêtre retournée à partir de l’objet `IOleInPlaceActiveObejct::GetWindow` fonctionner en tant que la destination de ces messages.

Si l’objet détecte un zéro dans le sixième élément de **OLEMENUGROUPWIDTHS**, il continue selon les règles de Documents OLE normales. Cette procédure traite des conteneurs qui participent **aide** fusion ainsi que celles qui ne le faites pas de menus.

Lorsque l’objet appelle `IOleInPlaceFrame::SetMenu`avant d’afficher le menu fusionné de la barre, le conteneur vérifie si le **aide** menu a un sous-menu supplémentaire, en plus de ce que le conteneur a insérés. Si, le conteneur laisse son **aide** menu dans la barre de menus fusionnée. Si le **aide** menu ne dispose pas d’un sous-menu supplémentaire, le conteneur supprime ses **aide** menu dans la barre de menus fusionnée. Cette procédure traite des objets qui participent à **aide** fusion ainsi que celles qui ne le faites pas de menus.

Enfin, lorsqu’il est temps de désassembler le menu, l’objet supprime le texte inséré **aide** menu outre la suppression de l’autre inséré les menus. Lorsque le conteneur supprime ses menus, il supprime son **aide** menu en plus des autres menus qu’il a insérés.

## <a name="see-also"></a>Voir aussi

[Conteneurs de documents actifs](../mfc/active-document-containers.md)
