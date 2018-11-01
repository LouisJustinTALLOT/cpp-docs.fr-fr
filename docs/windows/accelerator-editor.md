---
title: Éditeur d’accélérateurs (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.accelerator.F1
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [C++], accelerator key
- accelerator keys [C++]
- resource editors [C++], Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
ms.openlocfilehash: fdb2d9cf0954142da990a0a9f995cb482060345d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621492"
---
# <a name="accelerator-editor-c"></a>Éditeur d’accélérateurs (C++)

Une table d’accélérateurs est une ressource C++ Windows qui contient une liste des touches accélérateur (également connu sous les touches de raccourci) et les identificateurs de commande qui leur sont associés. Un programme peut avoir plusieurs tables d’accélérateurs.

Normalement, les accélérateurs sont utilisés comme raccourcis clavier pour des commandes de programme qui sont également disponibles dans un menu ou une barre d’outils. Toutefois, vous pouvez utiliser la table d’accélérateurs pour définir des combinaisons de touches pour des commandes qui ne sont associées à aucun objet d’interface utilisateur.

Vous pouvez utiliser [Affichage de classes](/visualstudio/ide/viewing-the-structure-of-code) pour raccorder des commandes de touches accélérateur à du code.

Avec le **Accelerator** éditeur, vous pouvez :

- [Définir des propriétés d’accélérateurs](../windows/setting-accelerator-properties.md)

- [Associer une touche accélérateur à un élément de menu](../windows/associating-an-accelerator-key-with-a-menu-item.md)

- [Modifier des tables d’accélérateurs](../windows/editing-accelerator-tables.md)

- [Utiliser des touches accélérateur prédéfinies](../windows/predefined-accelerator-keys.md)

   > [!TIP]
   > Lors de l’utilisation du **Accelerator** éditeur, vous pouvez avec le bouton droit pour afficher un menu contextuel des commandes fréquemment utilisées. Les commandes disponibles varient selon la cible du pointeur.

   > [!NOTE]
   > Windows ne vous permet pas de créer des tables d’accélérateurs vides. Si vous créez une table d’accélérateurs sans entrée, elle est supprimée automatiquement lorsque vous l’enregistrez.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)