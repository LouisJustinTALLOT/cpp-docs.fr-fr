---
title: Commandes standard
ms.date: 11/04/2016
helpviewer_keywords:
- File menu
- identifiers [MFC], command IDs
- command IDs, standard commands
- OLE commands
- commands [MFC], standard
- standard command IDs
- Window menu commands
- standard commands
- View menu commands
- Edit menu standard commands
- Help [MFC], menus
- programmer-defined IDs [MFC]
ms.assetid: 88cf3ab4-79b3-4ac6-9365-8ac561036fbf
ms.openlocfilehash: 987023322e38584d10901c1ab1fe20ac46926bd2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272085"
---
# <a name="standard-commands"></a>Commandes standard

Le framework définit le nombre de messages de commande standard. Les identificateurs de ces commandes prennent généralement la forme :

**ID_** *Source*_*élément*

où *Source* est généralement un nom de menu et *élément* est un élément de menu. Par exemple, l’ID de commande pour la nouvelle commande dans le menu fichier est ID_FILE_NEW. ID de commande standard sont affichés en gras dans la documentation. ID définis par le programmeur sont affichés dans une police qui diffère du texte qui entoure.

Voici une liste de certaines commandes principales prises en charge :

*Commandes du Menu fichier*<br/>
Nouveau, ouvrir, fermer, enregistrer, enregistrer sous, mise en Page, configuration de l’impression, imprimer, aperçu avant impression, sortie et de fichiers récemment utilisés.

*Modifier les commandes de Menu*<br/>
Effacer, effacer tout, copier, couper, rechercher, coller, répéter, remplacer, sélectionner tout, Annuler et rétablir.

*Commandes du menu Affichage*<br/>
Barre d’outils et la barre d’état.

*Commandes du menu Fenêtre*<br/>
Nouveau, réorganiser, Cascade, mosaïque horizontale, mosaïque verticale et fractionner.

*Commandes du menu Aide*<br/>
Index, à l’aide de l’aide et environ.

*Commandes OLE (Menu Edition)*<br/>
Insérer le nouvel objet, modifier les liens, lien de coller, collage spécial et *typename* objet (commandes de verbe).

Le framework fournit différents niveaux de prise en charge pour ces commandes. Certaines commandes sont prises en charge uniquement en tant qu’ID de commande définis, tandis que d’autres sont pris en charge avec des implémentations complètes. Par exemple, le framework implémente la commande Ouvrir dans le menu fichier en créant un nouvel objet de document, affichant une boîte de dialogue Ouvrir et ouvrant et en lisant le fichier. En revanche, vous devez implémenter commandes dans le menu Edition vous-même, dans la mesure où les commandes comme ID_EDIT_COPY dépendent de la nature des données que vous copiez.

Pour plus d’informations sur les commandes prises en charge et le niveau de l’implémentation fournie, consultez [Note technique 22](../mfc/tn022-standard-commands-implementation.md). Les commandes standards sont définis dans le fichier AFXRES. H.

## <a name="see-also"></a>Voir aussi

[Objets d’interface utilisateur et ID de commande](../mfc/user-interface-objects-and-command-ids.md)
