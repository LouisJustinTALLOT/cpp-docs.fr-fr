---
title: Ajout d’une propriété (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00b19fa7166e6edad05d729c5a738a2a827086ae
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212793"
---
# <a name="adding-a-property-visual-c"></a>Ajout d'une propriété locale (Visual C++)
Vous pouvez utiliser [l’Assistant Ajout de propriété](../ide/names-add-property-wizard.md) pour ajouter une propriété à une interface de votre projet.  
  
### <a name="to-add-a-property-to-your-object"></a>Pour ajouter une propriété à votre objet  
  
1.  Dans [l’affichage de classes](https://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925), cliquez avec le bouton droit sur le nom de l’interface à laquelle vous souhaitez ajouter la propriété.  
  
    > [!NOTE]
    >  Vous pouvez également ajouter des propriétés aux dispinterfaces qui, tant que le projet n’est pas attribué, sont imbriquées dans le nœud de la bibliothèque.  
  
2.  Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Ajouter une propriété**.  
  
3.  Dans [l’Assistant Ajout de propriété](../ide/names-add-property-wizard.md), indiquez les informations permettant de créer la propriété.  
  
4.  Spécifiez tous les paramètres IDL (Interface Definition Language) pour la propriété dans la page [Attributs IDL](../ide/idl-attributes-add-property-wizard.md) de l’Assistant.  
  
5.  Cliquez sur **Terminer** pour ajouter la propriété.  
  
 Les méthodes **Get** et `Put` de la propriété sont affichées sous la forme de deux icônes dans l’affichage de classes, sous l’interface où elle est définie. Vous pouvez double-cliquer sur l’une ou l’autre des icônes pour voir la déclaration de propriété dans le fichier .idl.  
  
-   Pour les interfaces ATL, les fonctions **Get** et **Put** sont ajoutées au fichier .cpp tandis que les références à ces fonctions sont ajoutées au fichier .h.  
  
-   Pour les dispinterfaces MFC, si vous sélectionnez **Variable membre** comme type d’implémentation, une méthode et une variable sont ajoutées à la classe qui l’implémente. Si vous sélectionnez **Méthodes Get/Set** comme type d’implémentation, deux méthodes sont ajoutées à la classe qui l’implémente.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une interface COM](../ide/creating-a-com-interface-visual-cpp.md)   
 [Modification d’une interface COM](../ide/editing-a-com-interface.md)   
 [COM (Component Object Model)](/windows/desktop/com/the-component-object-model)   
 [Pointeurs d’interface et interfaces](/windows/desktop/com/interface-pointers-and-interfaces)