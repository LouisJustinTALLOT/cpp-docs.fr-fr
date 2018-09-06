---
title: Rendre un objet ATL comme Noncreatable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.objects
dev_langs:
- C++
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a77ed656d39888e85e607ee4fdd96b384d0d250
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761454"
---
# <a name="making-an-atl-object-noncreatable"></a>Rendre un objet ATL comme Noncreatable

Vous pouvez modifier les attributs d’un objet COM basé sur ATL afin qu’un client ne peut pas créer directement de l’objet. Dans ce cas, l’objet serait être retournée via un appel de méthode sur un autre objet plutôt que directement créé.

### <a name="to-make-an-object-noncreatable"></a>Pour rendre un objet comme noncreatable

1. Supprimer le [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) pour l’objet. Si vous souhaitez que l’objet comme noncreatable mais le contrôle à inscrire, remplacez OBJECT_ENTRY_AUTO avec [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto).

2. Ajouter le [noncreatable](../../windows/noncreatable.md) attribut à la coclasse dans le fichier .idl. Exemple :

    ```  
    [uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851), 
    helpstring("MyObject"), 
    noncreatable]  
    coclass MyObject  
    {  
        [default] interface IMyInterface;  
    }  
    ```

## <a name="see-also"></a>Voir aussi

[Assistant Projet ATL](../../atl/reference/atl-project-wizard.md)   
[Types de projets Visual C++](../../ide/visual-cpp-project-types.md)   
[Création de projets de bureau à l’aide des Assistants Application](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
[Programmation avec ATL et le Code C Run-Time](../../atl/programming-with-atl-and-c-run-time-code.md)   
[Principes de base des objets ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
[Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)

