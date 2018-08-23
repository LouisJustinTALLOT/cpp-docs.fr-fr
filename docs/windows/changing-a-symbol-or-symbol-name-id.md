---
title: Modification d’un symbole ou un nom de symbole (ID) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing
dev_langs:
- C++
helpviewer_keywords:
- symbol names
- symbols, names
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e2fb5268ca23def96c31f724b93fbdf1c81c4a43
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599693"
---
# <a name="changing-a-symbol-or-symbol-name-id"></a>Modification d'un symbole ou d'un nom de symbole (ID)

Quand vous créez une ressource ou un objet de ressource, l'environnement de développement lui assigne un nom de symbole par défaut, par exemple, IDD_DIALOG1. Vous pouvez utiliser la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour modifier le nom du symbole par défaut ou modifier le nom d’un symbole déjà associé à une ressource.

### <a name="to-change-a-resources-symbol-name"></a>Pour changer le nom de symbole d'une ressource

1. Dans [affichage des ressources](../windows/resource-view-window.md), sélectionnez la ressource.

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Dans le **propriétés** fenêtre, tapez un nouveau nom de symbole ou sélectionnez dans la liste des symboles existants dans le **ID** boîte.

   Si vous tapez un nouveau nom de symbole, il reçoit automatiquement une valeur.

Vous pouvez utiliser la [boîte de dialogue Symboles des ressources](../windows/resource-symbols-dialog-box.md) pour modifier les noms de symboles pas actuellement assignés à une ressource. Pour plus d’informations, consultez [modification des symboles non assignés](../windows/changing-unassigned-symbols.md).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Restrictions relatives au nom de symbole](../windows/symbol-name-restrictions.md)  
[ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)