---
title: Commandes standard | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: abe1b1676c5d1944adf61f6ae4234a7e3478c3b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380144"
---
# <a name="standard-commands"></a>Commandes standard
Le framework définit le nombre de messages de commande standard. En règle générale, les identificateurs de ces commandes prennent la forme :  
  
 **ID_** *Source*_*élément*  
  
 où *Source* est généralement un nom de menu et *élément* est un élément de menu. Par exemple, l’ID de commande pour la nouvelle commande dans le menu fichier est `ID_FILE_NEW`. ID de commande standard sont affichés en gras dans la documentation. ID définis par le programmeur sont affichés dans une police différente de texte qui l’entoure.  
  
 Voici une liste de certains des plus importantes commandes prises en charge :  
  
 *Commandes du Menu fichier*  
 Nouveau, ouvrir, fermer, enregistrer, enregistrer sous, mise en Page, configuration de l’impression, imprimer, aperçu avant impression, sortie et de fichiers récemment utilisés.  
  
 *Modifier les commandes de Menu*  
 Effacer, effacer tout, copier, couper, rechercher, coller, répéter, remplacer, sélectionner tout, Annuler et rétablir.  
  
 *Commandes du menu Affichage*  
 Barre d’outils et la barre d’état.  
  
 *Commandes du menu Fenêtre*  
 Nouveau, réorganiser, Cascade, mosaïque horizontale, mosaïque verticale et fractionner.  
  
 *Commandes du menu Aide*  
 Index, à l’aide de l’aide et sur le point.  
  
 *OLE, commandes (Menu Edition)*  
 Insérer le nouvel objet, modifier les liaisons, Coller avec liaison, collage spécial et *typename* objet (commandes de verbe).  
  
 Le framework fournit des niveaux de prise en charge pour ces commandes. Certaines commandes sont prises en charge uniquement en tant qu’ID de commandes définis, alors que d’autres sont pris en charge avec des implémentations complètes. Par exemple, le framework implémente la commande Ouvrir dans le menu fichier en créant un nouvel objet de document, en affichant une boîte de dialogue Ouvrir et ouverture et la lecture du fichier. En revanche, vous devez implémenter les commandes dans le menu Edition vous-même, depuis les commandes telles que **ID_EDIT_COPY** dépendent de la nature des données que vous copiez.  
  
 Pour plus d’informations sur les commandes prises en charge et le niveau de l’implémentation fournie, consultez [Note technique 22](../mfc/tn022-standard-commands-implementation.md). Les commandes standard sont définis dans le fichier AFXRES. H.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets d’interface utilisateur et ID de commande](../mfc/user-interface-objects-and-command-ids.md)

