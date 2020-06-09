---
title: Fusion des menus Aide
ms.date: 11/04/2016
helpviewer_keywords:
- menus [MFC], merging
- merging Help menus [MFC]
- Help [MFC], for active document containers
ms.assetid: 9d615999-79ba-471a-9288-718f0c903d49
ms.openlocfilehash: 1bd70af6f24ee6f9873b89b2060f4b2d90149c90
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620129"
---
# <a name="help-menu-merging"></a>Fusion des menus Aide

Lorsqu’un objet est actif dans un conteneur, le protocole de fusion de menus des documents OLE donne au contrôle total de l’objet le menu **aide** . Par conséquent, les rubriques d'aide du conteneur ne sont pas disponibles à moins que l'utilisateur désactive l'objet. L'architecture de la relation contenant-contenu de document actif examine les règles de la fusion de menus sur place afin d'autoriser le conteneur et un document actif à partager le menu. Les nouvelles règles sont simplement des conventions supplémentaires sur quel composant possède quelle partie du menu et comment le menu partagé est créé.

La nouvelle convention est simple. Dans les documents actifs, le menu **aide** contient deux éléments de menu de niveau supérieur organisés comme suit :

`Help`

`Container Help >`

`Object Help    >`

Par exemple, lorsqu’une section Word est active dans le classeur Office, le menu **aide** apparaît comme suit :

`Help`

`Binder Help >`

`Word Help   >`

Les deux éléments de menu sont des menus en cascade dans lesquels tous les éléments de menu supplémentaires spécifiques au conteneur et l'objet sont accessibles à l'utilisateur. Les éléments affichés ici varie avec le conteneur et les objets concernés.

Pour créer ce menu **aide** fusionné, l’architecture de relation contenant-contenu de document actif modifie la procédure des documents OLE normaux. Selon les documents OLE, la barre de menus fusionnée peut avoir six groupes de menus, à savoir **fichier**, **modifier**, **conteneur**, **objet**, **fenêtre**, **aide**, dans cet ordre. À chaque groupe, il peut y avoir zéro menus ou plus. Le **fichier**de groupes, le **conteneur**et la **fenêtre** appartiennent au conteneur et les groupes **modification**, **objet** et **aide** appartiennent à l’objet. Lorsque l'objet souhaite réaliser la fusion de menus, il crée une barre de menus vide et la passe au conteneur. Le conteneur insère ensuite ses menus en appelant `IOleInPlaceFrame::InsertMenus` . L’objet passe également une structure qui est un tableau de six valeurs longues (**OLEMENUGROUPWIDTHS**). Après avoir inséré les menus, le conteneur marque le nombre de menus qu'il a ajoutés dans chacun de ses groupes, puis effectue un retour. L'objet insère ses menus, en tenant compte du nombre de menus dans chaque groupe de conteneurs. Enfin, l'objet passe la barre de menus fusionnée et le tableau (contenant le nombre de menus dans chaque groupe) à OLE, qui retourne un handle opaque "descripteur de menu". Plus tard, l’objet passe ce handle et la barre de menus fusionnée au conteneur, via `IOleInPlaceFrame::SetMenu` . À ce stade, le conteneur affiche la barre de menus fusionnée et passe le handle à l’objet OLE, afin que ce dernier puisse distribuer des messages de menu approprié.

Dans la procédure de document actif modifiée, l’objet doit d’abord initialiser les éléments **OLEMENUGROUPWIDTHS** à zéro avant de le passer au conteneur. Le conteneur effectue ensuite une insertion de menu normale, à une exception près : le conteneur insère un menu **aide** en tant que dernier élément et stocke la valeur 1 dans la dernière entrée (sixième) du tableau **OLEMENUGROUPWIDTHS** (autrement dit, la largeur [5], qui appartient au groupe d’aide de l’objet). Ce menu **d’aide** ne comporte qu’un seul élément qui est un sous-menu, le menu en cascade «**aide du conteneur** > » comme décrit précédemment.

L’objet exécute ensuite son code d’insertion de menu normal, sauf qu’avant d’insérer son menu **aide** , il vérifie la sixième entrée du tableau **OLEMENUGROUPWIDTHS** . Si la valeur est 1 et que le nom du dernier menu est **aide** (ou la chaîne localisée appropriée), l’objet insère son menu **aide** en tant que sous-menu du menu **aide** du conteneur.

L’objet définit ensuite le sixième élément de **OLEMENUGROUPWIDTHS** sur zéro et incrémente le cinquième élément d’une unité. Cela permet à OLE de savoir que le menu **d’aide** appartient au conteneur et que les messages de menu correspondant à ce menu (et ses sous-menus) doivent être acheminés vers le conteneur. Il incombe ensuite au conteneur de transférer **WM_INITMENUPOPUP**, **WM_SELECT**, **WM_COMMAND**et d’autres messages liés au menu qui appartiennent à la partie de l’objet dans le menu **? (aide** ). Pour ce faire, utilisez **WM_INITMENU** pour effacer un indicateur qui indique au conteneur si l’utilisateur a accédé au menu **aide** de l’objet. Le conteneur observe ensuite **WM_MENUSELECT** pour l’entrée ou la sortie d’un élément du menu **d’aide** auquel le conteneur ne s’est pas ajouté. À l’entrée, cela signifie que l’utilisateur a accédé à un menu d’objet. le conteneur définit donc l’indicateur « dans le menu d’aide de l’objet » et utilise l’état de cet indicateur pour transférer les messages **WM_MENUSELECT**, **WM_INITMENUPOPUP**et **WM_COMMAND** au minimum dans la fenêtre de l’objet. (À la sortie, le conteneur efface l’indicateur et traite ensuite ces mêmes messages.) Le conteneur doit utiliser la fenêtre retournée par la fonction de l’objet `IOleInPlaceActiveObejct::GetWindow` comme destination pour ces messages.

Si l’objet détecte un zéro dans le sixième élément de **OLEMENUGROUPWIDTHS**, il continue en fonction des règles de documents OLE normales. Cette procédure couvre les conteneurs qui participent à la fusion du menu **aide** , ainsi que ceux qui ne le font pas.

Lorsque l’objet appelle `IOleInPlaceFrame::SetMenu` , avant d’afficher la barre de menus fusionnée, le conteneur vérifie si le menu **aide** a un sous-menu supplémentaire, en plus de ce que le conteneur a inséré. Si c’est le cas, le conteneur quitte son menu **aide** dans la barre de menus fusionnée. Si le menu **aide** n’a pas de sous-menu supplémentaire, le conteneur supprime le menu **aide** de la barre de menus fusionnée. Cette procédure couvre les objets qui participent à la fusion du menu **aide** , ainsi que ceux qui ne le font pas.

Enfin, lorsqu’il est temps de désassembler le menu, l’objet supprime le menu **d’aide** inséré en plus de supprimer les autres menus insérés. Quand le conteneur supprime ses menus, il supprime le menu **aide** en plus des autres menus qu’il a insérés.

## <a name="see-also"></a>Voir aussi

[Conteneurs de documents actifs](active-document-containers.md)
