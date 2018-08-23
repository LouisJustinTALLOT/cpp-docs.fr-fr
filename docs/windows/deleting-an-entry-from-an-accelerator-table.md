---
title: Suppression d’une entrée à partir d’une Table d’accélérateurs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], deleting entries
- keyboard shortcuts [C++], deleting entry from accelerator table
ms.assetid: cc9cd499-dc04-4fe6-9393-a3e471e115a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0c191a2e37e4fe99c12486270c34a558cf4e8455
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605405"
---
# <a name="deleting-an-entry-from-an-accelerator-table"></a>Suppression d'une entrée dans une table d'accélérateurs

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>Pour supprimer une entrée dans une table d'accélérateurs

1. Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Sélectionnez l'entrée à supprimer. (Maintenez la **Ctrl** ou **MAJ** enfoncée tout en cliquant pour sélectionner plusieurs entrées.)

3. Avec le bouton droit et choisissez **supprimer** dans le menu contextuel (ou sélectionnez **supprimer** à partir de la **modifier** menu).

\- ou -

- Appuyez sur la **supprimer** clé.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Modification des tables d’accélérateurs](../windows/editing-accelerator-tables.md)  
[Éditeur d’accélérateurs](../windows/accelerator-editor.md)