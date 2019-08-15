---
title: Apparence, Assistant contrôle ATL
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: e07dc017241848f1a670c17b12c2254de6d1b8e1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492187"
---
# <a name="appearance-atl-control-wizard"></a>Apparence, Assistant contrôle ATL

Utilisez cette page de l’Assistant pour identifier d’autres options d’élément utilisateur pour le contrôle. Cette page est disponible pour les contrôles identifiés comme des **contrôles standard** sous **type de contrôle** dans la page [options, Assistant contrôle ATL](../../atl/reference/options-atl-control-wizard.md) .

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

- **Afficher l’État**

   Définit l’apparence du contrôle dans le conteneur.

   - **Opaque**: Définit le bit VIEWSTATUS_OPAQUE dans l’énumération [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) et dessine le rectangle de contrôle entier passé à la méthode [CComControlBase:: OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) . Le contrôle apparaît entièrement opaque, et aucun des conteneurs ne s’affiche derrière les limites du contrôle.

      Ce paramètre aide le conteneur à dessiner le contrôle plus rapidement. Si cette option n’est pas sélectionnée, le contrôle peut contenir des parties transparentes.

      Seul un contrôle opaque peut avoir un arrière-plan Uni.

   - **Arrière-plan Uni**: Définit le bit VIEWSTATUS_SOLIDBKGND dans l’énumération VIEWSTATUS. L’arrière-plan du contrôle apparaît sous la forme d’une couleur unie sans modèle.

      Cette option est disponible uniquement si l’option **opaque** est également sélectionnée.

- **Ajouter un contrôle basé sur**

   Définit le contrôle pour qu’il soit basé sur un type de contrôle Windows en ajoutant un membre de données de type [CContainedWindow](ccontainedwindowt-class.md) à la classe qui implémente le contrôle. Elle ajoute également une table des messages et des fonctions de gestionnaire de messages pour gérer les messages Windows pour le contrôle. Choisissez dans la liste le type de contrôle Windows que vous souhaitez créer, le cas échéant.

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

   Définit des options d’apparence et de comportement supplémentaires pour le contrôle.

   - **Invisible au moment**de l’exécution: Définit le contrôle pour qu’il soit invisible au moment de l’exécution. Vous pouvez utiliser des contrôles invisibles pour effectuer des opérations en arrière-plan, telles que le déclenchement d’événements à intervalles réguliers.

   - **Agit comme Button**: Définit le bit OLEMISC_ACTSLIKEBUTTON dans l’énumération [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) pour permettre à un contrôle d’agir comme un bouton. Si le conteneur a marqué le site client du contrôle comme bouton par défaut, la sélection de cette option permet à votre contrôle de bouton de s’afficher comme bouton par défaut en dessinant lui-même avec un cadre plus épais. Pour plus d’informations, consultez [CComControlBase:: GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) .

   - **Agit comme étiquette**: Définit le bit OLEMISC_ACTSLIKELABEL dans l’énumération OLEMISC pour permettre à un contrôle de remplacer l’étiquette native du conteneur. Le conteneur détermine ce qu’il faut faire avec cet indicateur, le cas échéant.

- **Autre**

   Définit des options de comportement supplémentaires pour le contrôle.

   - **DC normalisé**: Définit le contrôle pour créer un contexte de périphérique normalisé lorsqu’il est appelé pour se dessiner lui-même. Cette action normalise l’apparence du contrôle, mais rend le dessin moins efficace.

   - **Fenêtre uniquement**: Spécifie que votre contrôle ne peut pas être sans fenêtre. Si vous ne sélectionnez pas cette option, votre contrôle est automatiquement sans fenêtre dans les conteneurs qui prennent en charge les objets sans fenêtre, et il est automatiquement fenêtre dans les conteneurs qui ne prennent pas en charge les objets sans fenêtre. La sélection de cette option force le contrôle à être Window, même dans les conteneurs qui prennent en charge les objets sans fenêtre.

   - À **Insérer**: Sélectionnez cette option pour que votre contrôle apparaisse dans la boîte de dialogue **Insérer un objet** des applications telles que Word et Excel. Votre contrôle peut ensuite être inséré par n’importe quelle application qui prend en charge les objets incorporés via cette boîte de dialogue.

## <a name="see-also"></a>Voir aussi

[Assistant Contrôle ATL](../../atl/reference/atl-control-wizard.md)<br/>
[Exemple de sous-modification: Superclasse un contrôle Windows standard](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
