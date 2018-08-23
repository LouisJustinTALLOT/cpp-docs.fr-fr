---
title: Boîte de dialogue de ressource ajouter | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.insertresource
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], adding
- Add Resource dialog box
ms.assetid: e9fb6967-738f-47e8-ab58-728cf35b3af0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a48b99ad1d00fdcc184f6a3fadc772b32057f75d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601328"
---
# <a name="add-resource-dialog-box"></a>Ajouter une ressource (boîte de dialogue)

Utilisez cette boîte de dialogue pour ajouter des ressources à un projet d’application de bureau Windows C++.

> [!NOTE]
> Ces informations ne s’applique pas aux ressources dans les applications de plateforme Windows universelle. Pour plus d’informations, consultez [ressources d’application et le système de gestion de ressources](/windows/uwp/app-resources/).

### <a name="resource-type"></a>Type de ressource

Spécifie le type de ressource que vous voulez créer.

Vous pouvez développer les catégories de ressources curseur et boîte de dialogue pour afficher des ressources supplémentaires. Ces ressources se trouvent dans ...\Microsoft Visual Studio `version`\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Si vous ajoutez des fichiers .rct, vous devez les placer dans ce répertoire ou vous devez spécifier un [chemin d’accès include](../windows/how-to-specify-include-directories-for-resources.md) pour eux. Les ressources de ces fichiers apparaissent alors au deuxième niveau en dessous de la catégorie appropriée. Il n’existe pas de limite prédéfinie au nombre de fichiers .rct que vous pouvez ajouter.

Les ressources affichées au niveau le plus élevé du contrôle d’arborescence sont les ressources par défaut fournies par Visual Studio.

### <a name="new"></a>Nouveau

Crée une ressource en fonction du type que vous avez sélectionné dans le **Type de ressource** boîte. La ressource s’ouvre dans l’éditeur approprié. Par exemple, si vous créez une ressource de boîte de dialogue, il s’ouvre dans le [éditeur de boîte de dialogue](../windows/dialog-editor.md).

### <a name="import"></a>Import

Ouvre le **importer** boîte de dialogue dans laquelle vous pouvez accéder à une ressource que vous souhaitez importer dans votre projet actuel. Vous pouvez importer un bitmap, une icône, un curseur, un fichier de ressources HTML, un fichier de ressources audio (.WAV) ou un fichier de ressources personnalisées.

### <a name="custom"></a>Personnalisé

Ouvre le [boîte de dialogue Nouvelle ressource personnalisée](../windows/new-custom-resource-dialog-box.md) dans lequel vous pouvez créer une ressource personnalisée. Les ressources personnalisées peuvent être modifiées seulement dans l’éditeur binaire.

## <a name="requirements"></a>Configuration requise

Aucun.

## <a name="see-also"></a>Voir aussi

[Guide pratique pour créer une ressource](../windows/how-to-create-a-resource.md)