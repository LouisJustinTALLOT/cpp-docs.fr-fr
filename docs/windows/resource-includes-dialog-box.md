---
title: Include des ressources boîte de dialogue (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resourceincludes
dev_langs:
- C++
helpviewer_keywords:
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
ms.assetid: 659a54e6-e416-4045-8411-798730ff4ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 626327fec8efda873551e6d9ee502d7405eec5a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46371977"
---
# <a name="resource-includes-dialog-box-c"></a>Include des ressources boîte de dialogue (C++)

Vous pouvez utiliser la **Include des ressources** boîte de dialogue dans un projet C++ à modifier l’environnement classique de stockage de toutes les ressources dans le fichier .rc de projet et toutes les [symboles](../windows/symbols-resource-identifiers.md) dans Resource.h.

Pour ouvrir le **Include des ressources** de fichiers dans la boîte de dialogue, avec le bouton droit une .rc [affichage des ressources](../windows/resource-view-window.md), puis choisissez **Include des ressources** dans le menu contextuel.

- **Fichier d’en-tête de symbole**

   Vous permet de modifier le nom du fichier d'en-tête où sont stockées les définitions de symbole de votre fichier de ressources. Pour plus d’informations, consultez [modification des noms de symbole de fichiers d’en-tête](../windows/changing-the-names-of-symbol-header-files.md).

- **Directives de symboles en lecture seule**

   Vous permet d'inclure les fichiers d'en-tête qui contiennent les symboles à ne pas modifier durant une session d'édition. Par exemple, vous pouvez inclure un fichier de symboles partagé entre plusieurs projets. Vous pouvez également inclure des fichiers MFC .h. Pour plus d’informations, consultez [symboles notamment partagés (lecture seule) ou calculés](../windows/including-shared-read-only-or-calculated-symbols.md).

- **Directives de compilation**

   Vous permet d’inclure des fichiers de ressources qui sont créés et modifiés à l’écart des ressources de votre fichier de ressources principal, qui contiennent des directives au moment de la compilation (comme celles qui incluent des ressources de manière conditionnelle) ou qui contiennent des ressources dans un format personnalisé. Vous pouvez également utiliser le **zone directives de compilation** pour inclure des fichiers de ressources MFC standards. Pour plus d’informations, consultez [inclusion des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md).

> [!NOTE]
> Entrées de ces zones de texte apparaissent dans le fichier .rc marqué par `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, et `TEXTINCLUDE 3` respectivement. Pour plus d’informations, consultez [TN035 : à l’aide de plusieurs fichiers de ressources et les fichiers d’en-tête avec Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Une fois que vous avez apporté des modifications à votre fichier de ressources en utilisant le **Include des ressources** boîte de dialogue, vous devez fermer le fichier .rc et puis le rouvrir pour que les modifications entrent en vigueur. Pour plus d’informations, consultez [inclusion des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Guide pratique pour spécifier des répertoires Include pour les ressources](../windows/how-to-specify-include-directories-for-resources.md)<br/>
[Symboles : identificateurs de ressources](../windows/symbols-resource-identifiers.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Éditeurs de ressources](../windows/resource-editors.md)