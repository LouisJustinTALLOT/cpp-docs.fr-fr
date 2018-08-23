---
title: Modification des noms de fichiers d’en-tête de symbole | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing.header
dev_langs:
- C++
helpviewer_keywords:
- resource files, multiple
- Resource Includes dialog box
- symbol header files, changing names
- symbol header files
- header files, changing names
- names [C++], symbol header files
- symbols, symbol header files
- Resource.h
ms.assetid: b948284a-7899-402e-ab12-9f2c8480ca9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2df697df91374b61b72b9093c8cf16e1ac613863
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605224"
---
# <a name="changing-the-names-of-symbol-header-files"></a>Modification des noms des fichiers d'en-tête de symbole

Normalement toutes les définitions de symbole sont enregistrées dans `Resource.h`. Toutefois, vous devrez peut-être changer ce nom de fichier Include pour pouvoir, par exemple, utiliser plusieurs fichiers de ressources dans le même répertoire.

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Pour changer le nom du fichier d'en-tête de symbole de ressource

1. Dans [affichage des ressources](../windows/resource-view-window.md), cliquez sur votre fichier .rc et choisissez [Include des ressources](../windows/resource-includes-dialog-box.md) dans le menu contextuel.

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Dans le **fichier d’en-tête de symbole** , tapez le nouveau nom pour le fichier include.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Affichage des symboles des ressources](../windows/viewing-resource-symbols.md)  
[ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)