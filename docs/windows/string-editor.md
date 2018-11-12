---
title: Éditeur de chaînes (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.string.F1
helpviewer_keywords:
- String editor
- string tables
- string tables [C++], String editor
- string editing
- string editing, string tables
- resource editors [C++], String editor
- strings [C++], editing
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
ms.openlocfilehash: add153f84259985066397b6340fb4281a11beb17
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513657"
---
# <a name="string-editor-c"></a>Éditeur de chaînes (C++)

Une table de chaînes est une ressource Windows qui contient une liste d’ID, de valeurs et de légendes pour toutes les chaînes de votre application. Par exemple, les invites de la barre d’état figurent dans la table de chaînes.

Lors du développement d’une application, vous pouvez avoir plusieurs tables de chaînes, une pour chaque langue ou condition. Toutefois, un module exécutable n’a qu’une seule table de chaînes. Une application en cours d’exécution peut faire référence à plusieurs tables de chaînes si vous placez les tables dans différentes DLL.

Les tables de chaînes simplifient la localisation de votre application dans différentes langues. Si toutes les chaînes sont dans une table de chaînes, vous pouvez localiser l’application en traduisant les chaînes (et autres ressources) sans modifier le code source. Il est généralement préférable de procéder ainsi plutôt que de rechercher et de remplacer manuellement différentes chaînes dans les fichiers sources.

Avec l’Éditeur de chaînes, vous pouvez :

- [Rechercher une ou plusieurs chaînes](../windows/finding-a-string.md)

- [Insérer rapidement de nouvelles entrées](../windows/adding-or-deleting-a-string.md) dans la table de chaînes

- [Déplacer une chaîne d’un fichier de ressources vers un autre](../windows/moving-a-string-from-one-resource-file-to-another.md)

- [Utiliser la modification sur place pour les propriétés ID, Value et Caption](../windows/changing-the-properties-of-a-string.md) et afficher immédiatement les modifications

- [Modifier la propriété de légende de plusieurs chaînes](../windows/changing-the-caption-property-of-multiple-strings.md)

- [Ajouter des caractères de mise en forme ou des caractères spéciaux à une chaîne](../windows/adding-formatting-or-special-characters-to-a-string.md)

   > [!NOTE]
   > Windows n’autorise pas la création de tables de chaînes vides. Si vous créez une table de chaînes sans entrée, elle est supprimée automatiquement lorsque vous enregistrez le fichier de ressources.

Pour plus d’informations sur l’ajout de ressources aux projets managés (ceux qui ciblent le common language runtime), consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [procédure pas à pas : localisation de Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Chaînes](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[À propos des chaînes](/windows/desktop/menurc/about-strings)

