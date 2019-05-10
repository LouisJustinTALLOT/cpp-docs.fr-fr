---
title: Rendre un objet ATL comme Noncreatable
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.objects
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
ms.openlocfilehash: 5b259a677fdf3013ae1be6073afaf34f76a6e2fd
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221051"
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
[C++types de projets dans Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Programmation avec ATL et le code C Run-Time](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Principes de base des objets ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)
