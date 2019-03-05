---
title: Rendre un objet ATL comme Noncreatable
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.objects
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
ms.openlocfilehash: da1d5c43d86d95d7eff9b6830b83b61737d3030f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267067"
---
# <a name="making-an-atl-object-noncreatable"></a>Rendre un objet ATL comme Noncreatable

Vous pouvez modifier les attributs d’un objet COM basé sur ATL afin qu’un client ne peut pas créer directement de l’objet. Dans ce cas, l’objet serait être retournée via un appel de méthode sur un autre objet plutôt que directement créé.

## <a name="to-make-an-object-noncreatable"></a>Pour rendre un objet comme noncreatable

1. Supprimer le [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) pour l’objet. Si vous souhaitez que l’objet comme noncreatable mais le contrôle à inscrire, remplacez OBJECT_ENTRY_AUTO avec [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto).

1. Ajouter le [noncreatable](../../windows/noncreatable.md) attribut à la coclasse dans le fichier .idl. Exemple :

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

[Assistant Projet ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Types de projets Visual C++](../../ide/visual-cpp-project-types.md)<br/>
[Création de projets de bureau à l’aide des Assistants Application](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[Programmation avec ATL et le code C Run-Time](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Principes de base des objets ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)
