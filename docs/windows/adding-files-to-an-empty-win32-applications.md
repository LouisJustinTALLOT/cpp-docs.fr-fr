---
title: Ajout de fichiers à des applications Win32 vides
ms.date: 11/04/2016
helpviewer_keywords:
- empty projects [C++], adding files
- projects [C++], adding items
- blank projects
- files [C++], adding to projects
ms.assetid: 070098e8-0396-49fe-a697-3daa2f1be6de
ms.openlocfilehash: d5347a0693619e5db44b1087fc249c68b9227fb2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568650"
---
# <a name="adding-files-to-an-empty-win32-applications"></a>Ajout de fichiers à des applications Win32 vides

### <a name="to-add-your-files-to-an-empty-windows-desktop-application"></a>Pour ajouter vos fichiers à une application de bureau Windows vide

1. Sélectionnez le répertoire dans l’ **Explorateur de solutions**.

2. Cliquez avec le bouton droit sur le nom du répertoire, cliquez sur **Ajouter** dans le menu contextuel, puis cliquez sur **Élément existant**.

3. Dans la boîte de dialogue **Ajouter un élément existant**, accédez aux fichiers que vous souhaitez ajouter à votre projet.

4. Cliquez sur **OK**.

Pour ajouter des fichiers qui sont source, en-tête ni les fichiers de ressources à votre projet, cliquez sur le **Solution** nœud **l’Explorateur de solutions** et ajoutez les fichiers au projet de la même manière. Un **divers** dossier sera créé pour contenir les autres fichiers dans votre projet.

> [!NOTE]
> Avant de générer votre projet, vous devrez spécifier les options de génération de ces fichiers pour qu’ils soient correctement inclus dans l’application finale. Pour plus d’informations, consultez [Spécification des paramètres de projet avec des pages de propriétés](../ide/property-pages-visual-cpp.md) et [Génération d’un programme C/C++](../build/building-c-cpp-programs.md).

## <a name="see-also"></a>Voir aussi

[Création d’une application de bureau Windows vide](../windows/creating-an-empty-windows-desktop-application.md)
