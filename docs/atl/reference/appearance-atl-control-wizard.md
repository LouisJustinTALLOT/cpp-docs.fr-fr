---
title: Apparence, Assistant contrôle ATL
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: 4d3b0519951636fad4175dc35261ba35b3694ffa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62248951"
---
# <a name="appearance-atl-control-wizard"></a>Apparence, Assistant contrôle ATL

Utilisez cette page de l’Assistant pour identifier les options d’élément utilisateur supplémentaires pour le contrôle. Cette page est disponible pour les contrôles identifiés en tant que **contrôles Standard** sous **type de contrôle** sur le [Options, Assistant contrôle ATL](../../atl/reference/options-atl-control-wizard.md) page.

## <a name="uielement-list"></a>Liste des éléments d’interface

- **Afficher l’état**

   Définit l’apparence du contrôle dans le conteneur.

   - **Opaque**: Définit le bit VIEWSTATUS_OPAQUE dans le [double](/windows/desktop/api/ocidl/ne-ocidl-tagviewstatus) énumération et dessine le rectangle du contrôle entier passé à la [CComControlBase::OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) (méthode). Le contrôle apparaît complètement opaque et aucun du conteneur affiche au-delà des limites du contrôle.

      Ce paramètre permet de dessiner le contrôle plus rapidement le conteneur. Si cette option n’est pas sélectionnée, le contrôle peut contenir des parties transparentes.

      Seul un contrôle opaque peut avoir un arrière-plan uni.

   - **D’arrière-plan unie**: Définit le bit VIEWSTATUS_SOLIDBKGND dans l’énumération double. L’arrière-plan du contrôle apparaît sous la forme d’une couleur unie sans motif.

      Cette option est disponible uniquement si le **Opaque** option est également sélectionnée.

- **Ajouter un contrôle basé sur**

   Définit le contrôle doit être basé sur un type de contrôle Windows en ajoutant un [CContainedWindow](ccontainedwindowt-class.md) données membres à la classe qui implémente le contrôle. Il ajoute également une table des messages et des fonctions de gestionnaire de messages à traiter les messages Windows pour le contrôle. Dans la liste, choisissez le type de contrôle de Windows que vous souhaitez créer, le cas échéant.

   - **Button**

   - **ListBox**

   - **SysAnimate32**

   - **SysListView32**

   - **ComboBox**

   - **RichEdit**

   - **SysDateTimePick32**

   - **SysMonthCal32**

   - **ComboBoxEx32**

   - **ScrollBar**

   - **SysHeader32**

   - **SysTabControl32**

   - **Edition**

   - **Static**

   - **SysIPAddress32**

   - **SysTreeView32**

- **État divers**

   Définit des options d’apparence et le comportement supplémentaires pour le contrôle.

   - **Invisible au moment de l’exécution**: Définit le contrôle est invisible au moment de l’exécution. Vous pouvez utiliser les contrôles invisibles pour effectuer des opérations en arrière-plan, telles que le déclenchement d’événements à intervalles réguliers.

   - **Agit comme un bouton**: Définit le bit OLEMISC_ACTSLIKEBUTTON dans le [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) énumération pour permettre un contrôle d’agir comme un bouton. Si le conteneur a marqué le site du client du contrôle comme un bouton par défaut, cette option permet à votre contrôle de bouton à afficher comme un bouton par défaut en dessinant lui-même avec une image épaisse. Consultez [CComControlBase::GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) pour plus d’informations.

   - **Agit comme étiquette**: Définit le bit OLEMISC_ACTSLIKELABEL dans l’énumération OLEMISC pour permettre un contrôle de remplacer l’étiquette native du conteneur. Le conteneur détermine que faire avec cet indicateur, voire rien.

- **Autre**

   Définit les options de comportement supplémentaires pour le contrôle.

   - **Normalisées de contrôleur de domaine**: Définit le contrôle pour créer un contexte de périphérique normalisé lorsqu’elle est appelée pour dessiner lui-même. Cette action normalise l’apparence du contrôle, mais il rend le dessin moins efficace.

   - **Que la fenêtre**: Spécifie que votre contrôle ne peut pas être sans fenêtre. Si vous ne sélectionnez pas cette option, votre contrôle est automatiquement sans fenêtre dans des conteneurs qui prennent en charge les objets sans fenêtre, et il est automatiquement une fenêtre dans des conteneurs qui ne prennent pas en charge les objets sans fenêtre. Cette option force votre contrôle à utiliser une fenêtre, même dans des conteneurs qui prennent en charge les objets sans fenêtre.

   - **Insérable**: Sélectionnez cette option pour que votre contrôle s’affichent dans le **insérer un objet** boîte de dialogue d’applications telles que Word et Excel. Votre contrôle peut ensuite être inséré par n’importe quelle application qui prend en charge les objets incorporés dans cette boîte de dialogue.

## <a name="see-also"></a>Voir aussi

[Assistant Contrôle ATL](../../atl/reference/atl-control-wizard.md)<br/>
[SUBEDIT, exemple : Superclasse un contrôle Windows Standard](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
