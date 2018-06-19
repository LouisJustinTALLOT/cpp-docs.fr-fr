---
title: Apparence, Assistant contrôle ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.misc
dev_langs:
- C++
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1d27b46f529d8423bdaf733928a9f3e46b3f185
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358600"
---
# <a name="appearance-atl-control-wizard"></a>Apparence, Assistant contrôle ATL
Insérez « Résultats de recherche « résumé ici.  
  
 Utilisez cette page de l’Assistant pour identifier les options d’éléments utilisateur supplémentaires pour le contrôle. Cette page est disponible pour les contrôles identifiés comme **contrôles Standard** sous **type de contrôle** sur la [Options, Assistant contrôle ATL](../../atl/reference/options-atl-control-wizard.md) page.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Afficher l’état**  
 Définit l’apparence du contrôle dans le conteneur.  
  
-   **Opaque**: définit le `VIEWSTATUS_OPAQUE` bit dans le [VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201) énumération et dessine le rectangle du contrôle tout entier passé à la [CComControlBase::OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) (méthode). Le contrôle apparaît complètement opaque et aucun du conteneur affiche au-delà des limites du contrôle.  
  
     Ce paramètre permet de dessiner le contrôle plus rapidement le conteneur. Si cette option n’est pas sélectionnée, le contrôle peut contenir des parties transparentes.  
  
     Seul un contrôle opaque peut avoir un arrière-plan uni.  
  
-   Définit le `VIEWSTATUS_SOLIDBKGND` bit dans le `VIEWSTATUS` énumération. L’arrière-plan du contrôle s’affiche comme une couleur unie avec aucun modèle.  
  
     Cette option est disponible uniquement si le **Opaque** option est également sélectionnée.  
  
 **Ajouter un contrôle basé sur**  
 Définit le contrôle doit être basé sur un type de contrôle Windows en ajoutant un [CContainedWindow](ccontainedwindowt-class.md) membre de données à la classe implémentant le contrôle. Il ajoute également une table des messages et des fonctions de gestionnaires de messages à traiter les messages Windows pour le contrôle. Dans la liste, choisissez le type de contrôle Windows que vous souhaitez créer, le cas échéant.  

  
-   `Button`  
  
-   `ListBox`  
  
-   `SysAnimate32`  
  
-   `SysListView32`  
  
-   `ComboBox`  
  
-   `RichEdit`  
  
-   `SysDateTimePick32`  
  
-   `SysMonthCal32`  
  
-   `ComboBoxEx32`  
  
-   `ScrollBar`  
  
-   `SysHeader32`  
  
-   `SysTabControl32`  
  
-   `Edit`  
  
-   `Static`  
  
-   `SysIPAddress32`  
  
-   `SysTreeView32`  
  
 **État divers**  
 Définit les options d’apparence et le comportement supplémentaires pour le contrôle.  
  
-   **Invisible au moment de l’exécution**: définit le contrôle est invisible au moment de l’exécution. Vous pouvez utiliser des contrôles invisibles pour effectuer des opérations en arrière-plan, telles que le déclenchement d’événements à intervalles réguliers.  
  
-   **Se comporte comme bouton**: définit le `OLEMISC_ACTSLIKEBUTTON` bit dans le [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) énumération pour activer un contrôle d’agir comme un bouton. Si le conteneur a marqué le site du client du contrôle comme un bouton par défaut, cette option permet à votre contrôle de bouton à afficher comme bouton par défaut en dessinant lui-même à un frame épais. Consultez [CComControlBase::GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) pour plus d’informations.  
  
-   **Agit comme étiquette**: définit le `OLEMISC_ACTSLIKELABEL` bit dans le `OLEMISC` énumération pour activer un contrôle de remplacer l’étiquette du conteneur natif. Le conteneur détermine que faire avec cet indicateur, le cas échéant.  
  
 **Autre**  
 Définit les options de comportement supplémentaires pour le contrôle.  
  
-   **Normalisé de contrôleur de domaine**: définit le contrôle à créer un contexte de périphérique normalisé lorsqu’elle est appelée pour dessiner lui-même. Cette action standardise l’apparence du contrôle, mais elle simplifie le dessin moins efficace.  
  
-   **Que la fenêtre**: Spécifie que votre contrôle ne peut pas être sans fenêtre. Si vous ne sélectionnez pas de cette option, votre contrôle est automatiquement sans fenêtre dans les conteneurs qui prennent en charge les objets sans fenêtre, et il est automatiquement une fenêtre dans un conteneur qui ne prennent pas en charge les objets sans fenêtre. Cette option force votre fenêtre, même dans les conteneurs qui prennent en charge les objets sans fenêtre du contrôle.  
  
-   **Insérer**: sélectionnez cette option pour que votre contrôle s’affichent dans le **insérer un objet** boîte de dialogue d’applications telles que Word et Excel. Votre contrôle peut ensuite être inséré par toute application qui prend en charge les objets incorporés dans cette boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant contrôle ATL](../../atl/reference/atl-control-wizard.md)   
 [SUBEDIT, exemple : Superclasses un contrôle Windows Standard](http://msdn.microsoft.com/en-us/30e46bdc-ed92-417c-b6b8-359017265a7b)

