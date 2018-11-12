---
title: Déplacement d’une chaîne à partir d’un fichier de ressources à un autre (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
ms.assetid: 94f8ee81-9b4c-4788-ba95-68c58db38029
ms.openlocfilehash: e89a0d44dc824c72710f8a047a18771ba8da492b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649811"
---
# <a name="moving-a-string-from-one-resource-file-to-another-c"></a>Déplacement d’une chaîne à partir d’un fichier de ressources à un autre (C++)

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Déplacer une chaîne à partir du fichier de script d’une ressource à un autre

1. Ouvrez les tables de chaînes dans les deux fichiers .rc. (Pour plus d’informations, consultez [affichage des ressources dans un fichier de Script de ressources en dehors d’un projet](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).)

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Avec le bouton droit de la chaîne que vous souhaitez déplacer et choisissez **couper** dans le menu contextuel.

3. Placez le curseur dans la cible **éditeur de chaînes** fenêtre.

4. Dans le fichier .rc vers lequel vous souhaitez déplacer la chaîne, avec le bouton droit et choisissez **coller** dans le menu contextuel.

   > [!NOTE]
   > Si le **ID** ou **valeur** de conflits avec une chaîne déplacée **ID** ou **valeur** dans le fichier de destination, soit le **ID** ou **valeur** des modifications de chaîne déplacée. S’il existe une chaîne avec le même **ID**, le **ID** des modifications de chaîne déplacée. S’il existe une chaîne avec le même **valeur**, le **valeur** des modifications de chaîne déplacée.

Pour plus d’informations sur l’ajout de ressources aux projets managés (ceux qui ciblent le common language runtime), consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [procédure pas à pas : localisation de Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de chaînes](../windows/string-editor.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Personnalisation des dispositions de fenêtres](/visualstudio/ide/customizing-window-layouts-in-visual-studio)