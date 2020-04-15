---
title: Apparence, Assistant contrôle ATL
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: 3484fb5d0f919af0dfd18b584e96d4675e2baea8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319397"
---
# <a name="appearance-atl-control-wizard"></a>Apparence, Assistant contrôle ATL

Utilisez cette page de l’assistant pour identifier d’autres options d’élément utilisateur pour le contrôle. Cette page est disponible pour les contrôles identifiés comme **contrôles standard** sous le type **de contrôle** sur la page [Options, ATL Control Wizard.](../../atl/reference/options-atl-control-wizard.md)

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

- **Afficher l’état**

   Définit l’apparence du contrôle dans le conteneur.

  - **Opaque**: définit le VIEWSTATUS_OPAQUE peu dans [l’énumération VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) et tire l’ensemble du rectangle de contrôle passé à la [base de CComControl::OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) méthode. Le contrôle semble complètement opaque, et aucun des conteneurs ne montre derrière les limites de contrôle.

      Ce réglage aide le conteneur à dessiner le contrôle plus rapidement. Si cette option n’est pas sélectionnée, le contrôle peut contenir des pièces transparentes.

      Seul un contrôle opaque peut avoir un fond solide.

  - **Contexte solide**: définit le VIEWSTATUS_SOLIDBKGND peu dans le recensement VIEWSTATUS. L’arrière-plan du contrôle apparaît comme une couleur solide sans motif.

      Cette option n’est disponible que si l’option **Opaque** est également sélectionnée.

- **Ajouter le contrôle basé sur**

   Définit le contrôle pour être basé sur un type de contrôle Windows en ajoutant un membre de données [CContainedWindow](ccontainedwindowt-class.md) à la classe implémentant le contrôle. Il ajoute également une carte de message et des fonctions de gestionnaire de messages pour gérer les messages Windows pour le contrôle. Choisissez parmi la liste le type de contrôle Windows que vous souhaitez créer, le cas échéant.

  - **Bouton**

  - **Zone de liste**

  - **SysAnimate32**

  - **SysListView32**

  - **Liste déroulante**

  - **RichEdit**

  - **SysDateTimePick32**

  - **SysMonthCal32**

  - **ComboBoxEx32**

  - **ScrollBar**

  - **SysHeader32**

  - **SysTabControl32**

  - **Modifier**

  - **Statique**

  - **SysIPAddress32**

  - **SysTreeView32**

- **Statut Misc**

   Définit des options d’apparence et de comportement supplémentaires pour le contrôle.

  - **Invisible au moment de la course**: définit le contrôle pour être invisible au moment de la course. Vous pouvez utiliser des commandes invisibles pour effectuer des opérations en arrière-plan, telles que des événements de tir à intervalles chronométrés.

  - **Agit comme un bouton**: définit le OLEMISC_ACTSLIKEBUTTON bit dans le recensement [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) pour permettre à un contrôle d’agir comme un bouton. Si le conteneur a marqué le site client du contrôle comme un bouton par défaut, la sélection de cette option permet à votre contrôle de bouton de s’afficher comme un bouton par défaut en se dessinant avec un cadre plus épais. Voir [CComControlBase::GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) pour plus d’informations.

  - **Agit comme l’étiquette**: Définit le OLEMISC_ACTSLIKELABEL bit dans le recensement OLEMISC pour permettre un contrôle pour remplacer l’étiquette native du conteneur. Le conteneur détermine ce qu’il faut faire avec ce drapeau, si quelque chose.

- **Autres**

   Définit des options de comportement supplémentaires pour le contrôle.

  - **C.A. Normalisé**: Définit le contrôle pour créer un contexte d’appareil normalisé lorsqu’il est appelé à se dessiner. Cette action standardise l’apparence du contrôle, mais elle rend le dessin moins efficace.

  - **Fenêtre seulement**: Spécifie que votre contrôle ne peut pas être sans fenêtre. Si vous ne sélectionnez pas cette option, votre contrôle est automatiquement sans fenêtre dans des conteneurs qui prennent en charge les objets sans fenêtre, et il est automatiquement fenêtre dans des conteneurs qui ne prennent pas en charge les objets sans fenêtre. La sélection de cette option oblige votre contrôle à être fenêtre, même dans des conteneurs qui prennent en charge les objets sans fenêtre.

  - **Insérer**: Sélectionnez cette option pour que votre contrôle apparaisse dans la boîte de dialogue **Insert Object** d’applications telles que Word et Excel. Votre contrôle peut ensuite être inséré par n’importe quelle application qui prend en charge les objets embarqués à travers cette boîte de dialogue.

## <a name="see-also"></a>Voir aussi

[Assistant Contrôle ATL](../../atl/reference/atl-control-wizard.md)<br/>
[SUBEDIT Sample: Superclasses a Standard Windows Control](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
