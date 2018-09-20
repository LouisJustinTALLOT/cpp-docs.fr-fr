---
title: 'Comment : ajouter la prise en charge MFC aux fichiers de Script de ressources (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.add.MFC
dev_langs:
- C++
helpviewer_keywords:
- rc files [C++], adding MFC support
- .rc files [C++], adding MFC support
- MFC, adding support to resource scripts files
- resource script files [C++], adding MFC support
ms.assetid: 599dfe9d-ad26-4e34-899c-49b56599e37f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 631a6eb1ea2f992fe33183b5e8d997afb1d8fa40
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372416"
---
# <a name="how-to-add-mfc-support-to-resource-script-files-c"></a>Comment : ajouter la prise en charge MFC aux fichiers de Script de ressources (C++)

Normalement, lorsque vous générez une application MFC pour Windows à l’aide de la [Assistant Application MFC](../mfc/reference/mfc-application-wizard.md), l’Assistant génère un ensemble de base de fichiers (y compris un fichier de script (.rc) de ressources) qui contiennent les principales fonctionnalités de Microsoft Foundation classes (MFC). Toutefois, si vous modifiez un fichier .rc d’une application Windows qui n’est pas basée sur MFC, les fonctionnalités suivantes propres à l’infrastructure MFC ne sont pas disponibles :

- Assistants code MFC

- Chaînes d'invite de menu

- Contenu des listes pour les contrôles zone de liste déroulante

- Hébergement de contrôles ActiveX

Toutefois, vous pouvez ajouter une prise en charge de MFC aux fichiers .rc existants qui en sont dépourvus.

### <a name="to-add-mfc-support-to-rc-files"></a>Pour ajouter la prise en charge de MFC à des fichiers .rc

1. Ouvrez le fichier de script de ressources.

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Dans [affichage des ressources](../windows/resource-view-window.md), mettez en surbrillance le dossier de ressources (par exemple, MFC.rc).

3. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), définissez le **MFC Mode** propriété **True**.

   > [!NOTE]
   > Outre la définition de cet indicateur, le fichier .rc doit faire partie d'un projet MFC. Par exemple, définissant simplement **MFC Mode** à **True** sur un fichier .rc dans Win32 projet ne vous donne aucune des fonctionnalités MFC.

## <a name="requirements"></a>Configuration requise

MFC

## <a name="see-also"></a>Voir aussi

[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)