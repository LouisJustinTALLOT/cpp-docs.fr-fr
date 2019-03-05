---
title: Ajout d’une nouvelle Interface dans un projet ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.interface
helpviewer_keywords:
- interfaces, adding to ATL objects
- Implement Interface ATL wizard
- controls [ATL], interfaces
- ATL projects, adding interfaces
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
ms.openlocfilehash: 29b8fc3caf2d769fcc60772be7fdf1c25f13d100
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285384"
---
# <a name="adding-a-new-interface-in-an-atl-project"></a>Ajout d’une nouvelle Interface dans un projet ATL

Lorsque vous ajoutez une interface à votre contrôle ou un objet, vous créez des fonctions extraite pour chaque méthode dans cette interface. Dans votre contrôle ou un objet, vous pouvez ajouter uniquement les interfaces figurant actuellement dans une bibliothèque de types existante. En outre, la classe dans laquelle vous ajoutez l’interface doit implémenter la [BEGIN_COM_MAP](com-map-macros.md#begin_com_map) macro ou, si le projet est attribué, il doit avoir le `coclass` attribut.

Vous pouvez ajouter une nouvelle interface à votre contrôle dans un des deux façons : manuellement ou à l’aide des Assistants code dans l’affichage de classes.

## <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>Utilisation des Assistants de code dans l’affichage de classes pour ajouter une interface à un objet existant ou d’un contrôle

1. Dans [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez sur le nom de classe d’un contrôle. Par exemple, un contrôle total ou contrôle composite ou toute autre classe de contrôle qui implémente une macro BEGIN_COM_MAP dans son fichier d’en-tête.

1. Dans le menu contextuel, cliquez sur **ajouter**, puis cliquez sur **implémenter l’Interface**.

1. Sélectionnez les interfaces à implémenter dans le [Assistant Implémentation d’Interface](../../ide/implement-interface-wizard.md). Si l’interface n’existe pas dans n’importe quel typelib disponible, puis vous devez ajouter il manuellement au fichier .idl.

## <a name="to-add-a-new-interface-manually"></a>Pour ajouter une nouvelle interface manuellement

1. Ajoutez la définition de la nouvelle interface au fichier .idl.

1. Dérivez votre objet ou le contrôle à partir de l’interface.

1. Créer un nouveau [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) pour l’interface ou, si le projet est attribué, ajoutez le `coclass` attribut.

1. Implémenter des méthodes sur l’interface.

## <a name="see-also"></a>Voir aussi

[Assistant Projet ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Types de projets Visual C++](../../ide/visual-cpp-project-types.md)<br/>
[Création de projets de bureau à l’aide des Assistants Application](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[Programmation avec ATL et le code C Run-Time](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Principes de base des objets ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)
