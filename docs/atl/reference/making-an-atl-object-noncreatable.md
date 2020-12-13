---
description: 'En savoir plus sur : rendre un objet ATL non pouvant être créé'
title: Rendre un objet ATL impossible à créer
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.objects
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
ms.openlocfilehash: 0a7a07081546722e5a960cb8bf0384a1d7e47f9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139176"
---
# <a name="making-an-atl-object-noncreatable"></a>Rendre un objet ATL impossible à créer

Vous pouvez modifier les attributs d’un objet COM basé sur ATL afin qu’un client ne puisse pas créer directement l’objet. Dans ce cas, l’objet est retourné par l’intermédiaire d’un appel de méthode sur un autre objet plutôt que d’être créé directement.

## <a name="to-make-an-object-noncreatable"></a>Pour rendre un objet non pouvant être créé

1. Supprimez le [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) pour l’objet. Si vous souhaitez que l’objet ne soit pas créé, mais le contrôle à inscrire, remplacez OBJECT_ENTRY_AUTO par [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto).

1. Ajoutez l’attribut [noncreatable](../../windows/attributes/noncreatable.md) à la coclasse dans le fichier. idl. Par exemple :

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
[Types de projets C++ dans Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Programmation avec des Run-Time du code ATL et C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Notions de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)
