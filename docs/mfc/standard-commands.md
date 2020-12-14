---
description: 'En savoir plus sur : commandes standard'
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
ms.openlocfilehash: 09c0afecf5b34565c3ab14e276c7c43a20189a0a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216741"
---
# <a name="standard-commands"></a>Commandes standard

Le Framework définit de nombreux messages de commande standard. Les ID de ces commandes prennent généralement la forme suivante :

**ID_** *source* _ *élément*

où *source* est généralement un nom de menu et un *élément* est un élément de menu. Par exemple, l’ID de commande de la nouvelle commande dans le menu fichier est ID_FILE_NEW. Les ID de commande standard sont affichés en gras dans la documentation. Les ID définis par le programmeur sont affichés dans une police différente du texte environnant.

Voici une liste de quelques-unes des commandes les plus importantes prises en charge :

*Commandes du menu fichier*<br/>
Nouveau, ouvrir, fermer, enregistrer, enregistrer sous, mise en page, imprimer la configuration, imprimer, aperçu avant impression, quitter et les fichiers récemment utilisés.

*Commandes du menu Edition*<br/>
Effacer, effacer tout, copier, couper, Rechercher, coller, répéter, remplacer, sélectionner tout, annuler et rétablir.

*Commandes du menu Affichage*<br/>
Barre d’outils et barre d’État.

*Commandes du menu fenêtre*<br/>
Nouveau, réorganiser, cascade, mosaïque horizontale, mosaïque verticale et fractionner.

*Commandes du menu aide*<br/>
Index, utilisation de l’aide et à propos de.

*Commandes OLE (menu Edition)*<br/>
Insérez un nouvel objet, modifiez des liens, collez un lien, collez un objet spécial et un objet *TypeName* (commandes VERB).

L’infrastructure fournit différents niveaux de prise en charge pour ces commandes. Certaines commandes sont uniquement prises en charge en tant qu’ID de commande défini, tandis que d’autres sont prises en charge avec des implémentations approfondies. Par exemple, l’infrastructure implémente la commande ouvrir dans le menu fichier en créant un nouvel objet document, en affichant une boîte de dialogue Ouvrir et en ouvrant et en lisant le fichier. En revanche, vous devez implémenter vous-même des commandes dans le menu Edition, car les commandes telles que ID_EDIT_COPY dépendent de la nature des données que vous copiez.

Pour plus d’informations sur les commandes prises en charge et le niveau d’implémentation fourni, consultez [Technical Note 22](../mfc/tn022-standard-commands-implementation.md). Les commandes standard sont définies dans le fichier AFXRES. H.

## <a name="see-also"></a>Voir aussi

[Objets de l’interface utilisateur et ID de commande](../mfc/user-interface-objects-and-command-ids.md)
