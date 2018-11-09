---
title: Ajout d'une propriété locale (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
ms.openlocfilehash: 3c47a5b50442f47e6042ea1232590dbdde7299ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563083"
---
# <a name="adding-a-property-visual-c"></a>Ajout d'une propriété locale (Visual C++)

Vous pouvez utiliser [l’Assistant Ajout de propriété](../ide/names-add-property-wizard.md) pour ajouter une propriété à une interface de votre projet.

### <a name="to-add-a-property-to-your-object"></a>Pour ajouter une propriété à votre objet

1. Dans [l’affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez avec le bouton droit sur le nom de l’interface à laquelle vous souhaitez ajouter la propriété.

   > [!NOTE]
   > Vous pouvez également ajouter des propriétés aux dispinterfaces qui, tant que le projet n’est pas attribué, sont imbriquées dans le nœud de la bibliothèque.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Ajouter une propriété**.

1. Dans [l’Assistant Ajout de propriété](../ide/names-add-property-wizard.md), indiquez les informations permettant de créer la propriété.

1. Spécifiez tous les paramètres IDL (Interface Definition Language) pour la propriété dans la page [Attributs IDL](../ide/idl-attributes-add-property-wizard.md) de l’Assistant.

1. Cliquez sur **Terminer** pour ajouter la propriété.

Les méthodes **Get** et `Put` de la propriété sont affichées sous la forme de deux icônes dans l’affichage de classes, sous l’interface où elle est définie. Vous pouvez double-cliquer sur l’une ou l’autre des icônes pour voir la déclaration de propriété dans le fichier .idl.

- Pour les interfaces ATL, les fonctions **Get** et **Put** sont ajoutées au fichier .cpp tandis que les références à ces fonctions sont ajoutées au fichier .h.

- Pour les dispinterfaces MFC, si vous sélectionnez **Variable membre** comme type d’implémentation, une méthode et une variable sont ajoutées à la classe qui l’implémente. Si vous sélectionnez **Méthodes Get/Set** comme type d’implémentation, deux méthodes sont ajoutées à la classe qui l’implémente.

## <a name="see-also"></a>Voir aussi

[Création d’une interface COM](../ide/creating-a-com-interface-visual-cpp.md)<br>
[Modification d’une interface COM](../ide/editing-a-com-interface.md)<br>
[COM (Component Object Model)](/windows/desktop/com/the-component-object-model)<br>
[Pointeurs d’interface et interfaces](/windows/desktop/com/interface-pointers-and-interfaces)