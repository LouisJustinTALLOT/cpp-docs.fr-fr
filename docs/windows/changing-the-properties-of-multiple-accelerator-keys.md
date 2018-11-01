---
title: Modification des propriétés de plusieurs touches accélérateur (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
ms.openlocfilehash: 00c2bed34d70fa13161cbaa8968d967664c8bb0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668999"
---
# <a name="changing-the-properties-of-multiple-accelerator-keys-c"></a>Modification des propriétés de plusieurs touches accélérateur (C++)

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Pour modifier les propriétés de plusieurs touches accélérateur

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Sélectionnez les touches accélérateur que vous souhaitez modifier en maintenant enfoncée la **Ctrl** enfoncée quand vous cliquez sur chacun d’eux.

3. Accédez à la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) et tapez les valeurs que vous voulez que tous les accélérateurs sélectionnés doivent partager.

   > [!NOTE]
   > Chaque valeur de modificateur apparaît sous la forme d’une propriété booléenne dans la **propriétés** fenêtre. Si vous modifiez un [modificateur](../windows/accelerator-modifier-property.md) valeur dans le **propriétés** fenêtre, la table d’accélérateurs traite le nouveau modificateur comme un ajout aux modificateurs déjà présents. Pour cette raison, si vous définissez des valeurs de la modifier, vous devez définir tous pour vous assurer que chaque accélérateur partage les mêmes **modificateur** paramètres.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Modification des tables d’accélérateurs](../windows/editing-accelerator-tables.md)<br/>
[Éditeur d’accélérateurs](../windows/accelerator-editor.md)