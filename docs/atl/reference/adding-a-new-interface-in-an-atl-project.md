---
title: Ajout d’une nouvelle interface à un projet ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.interface
helpviewer_keywords:
- interfaces, adding to ATL objects
- Implement Interface ATL wizard
- controls [ATL], interfaces
- ATL projects, adding interfaces
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
ms.openlocfilehash: 8bf0138f85929e06b67e9a2e294eda8a2f385e1a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499381"
---
# <a name="adding-a-new-interface-in-an-atl-project"></a>Ajout d’une nouvelle interface à un projet ATL

Lorsque vous ajoutez une interface à votre objet ou contrôle, vous créez des fonctions extraites pour chaque méthode dans cette interface. Dans votre objet ou contrôle, vous pouvez ajouter uniquement les interfaces qui se trouvent actuellement dans une bibliothèque de types existante. En outre, la classe dans laquelle vous ajoutez l’interface doit implémenter la macro [BEGIN_COM_MAP](com-map-macros.md#begin_com_map) ou, si le projet est attribué, elle doit avoir l' `coclass` attribut.

Vous pouvez ajouter une nouvelle interface à votre contrôle de l’une des deux manières suivantes : manuellement ou à l’aide des assistants code dans Affichage de classes.

## <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>Pour utiliser les assistants code dans Affichage de classes pour ajouter une interface à un objet ou un contrôle existant

1. Dans [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez avec le bouton droit sur le nom de la classe d’un contrôle. Par exemple, un contrôle total ou composite, ou toute autre classe de contrôle qui implémente une BEGIN_COM_MAP macro dans son fichier d’en-tête.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **implémenter l’interface**.

1. Sélectionnez les interfaces à implémenter dans l' [Assistant Implémentation](../../ide/implementing-an-interface-visual-cpp.md#implement-interface-wizard)de l’interface. Si l’interface n’existe dans aucune TypeLib disponible, vous devez l’ajouter manuellement au fichier. idl.

## <a name="to-add-a-new-interface-manually"></a>Pour ajouter une nouvelle interface manuellement

1. Ajoutez la définition de votre nouvelle interface au fichier. idl.

1. Dérivez votre objet ou contrôle à partir de l’interface.

1. Créez un [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) pour l’interface ou, si le projet est attribué, ajoutez l' `coclass` attribut.

1. Implémentez les méthodes sur l’interface.

## <a name="see-also"></a>Voir aussi

[Assistant Projet ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Types de projets C++ dans Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Programmation à l’aide du code ATL et Runtime C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Notions de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)
